---
title: "How do I test with Apache Spark?"
date: 2019-07-30T17:01:10+02:00
draft: false
---

If you are wondering how you can test with Apache Spark. Or if you are curious about how other projects deal with tests, this article is for you. I will show examples in Scala with Specs2 but the global idea can work with any language or framework test.

What do we need to test with Apache Spark?
This is the first problem.
Suppose that we have data about diamonds sales. We want to extract only one field (the diamond color) from all the information.

```scala

//We create a case class
case class Diamond(color: String, price: Int)

//We use the case class to make the "diamonds.csv" file a Dataset
val diamonds: Dataset[Diamond] = spark.read.csv("diamonds.csv").as[Diamond] 

//We extract only the color
val result: Dataset[String] = diamonds.map(diamond => {
  diamond.color
})
```

Here, we are working with datasets. We could extract a function that takes a diamond as input and gives another one as output:

```scala
case class Diamond(color: String, price: Int)
val diamonds: Dataset[Diamond] = spark.read.csv("diamonds.csv").as[Diamond]

//We extract the computation into a method
def selectColor(diamond: Diamond): String = {
  diamond.color
}

val result: Dataset[String] = diamonds.map(selectColor(_))
```

Our function *selectColor* is like any other function in Scala. We can test it the same way.

But most of the time, what we want to test is more complex.
Let’s establish some naive coincidences between the diamonds prices and the trendy colors.

We have data about diamonds sales on one hand:

| color | price |
|-------|-------|
| green | 1000  |
| red   | 1500  |


and trendy colors on the other hand:

| color | score |
|-------|-------|
| green | 9     |
| red   | 4     |

And then our code is going to be more complex:

```scala

//Case class for Diamond
case class Diamond(color: String, price: Int)

//Case class for TrendyColor
case class TrendyColor(color: String, trendyScore: Int) 

//Case class for final result
case class Result(price: Int)

//Diamonds Data
val diamonds: Dataset[Diamond] = spark.read.parquet("diamonds.parquet").as[Diamond]

//trendy colors data
val trendyColors: Dataset[TrendyColor] = spark.read.parquet("trendyColors.parquet").as[TrendyColor] 

//We make a join
val diamondsJoinedWithTrendyColors: DataFrame = diamonds.join(
  trendyColors,
  Seq("color"),
  "inner"
) 

// We extract only the diamonds with trendy colors (score upper 5 is considered as a trendy color)
val diamondsWithHighTrendyScores: DataFrame = diamondsJoinedWithTrendyColors.
  filter("trendyScore > 5")

//We select only the price
diamondsWithHighTrendyScores.select("price").as[Result]
```
Again, we can extract a function here like this:

```scala
def priceOfDiamondsWithTrendyColors(
  diamonds: Dataset[Diamond], 
  trendyColors: Dataset[TrendyColor], 
  spark: SparkSession): Dataset[Result] = {
    
  import spark.implicits._
  
  val diamondsJoinedWithTrendyColors: DataFrame = diamonds.join(
      trendyColors,
      Seq("color"),
      "inner"
  )

  val diamondsWithHighTrendyScores: DataFrame = diamondsJoinedWithTrendyColors.
    filter("trendyScore > 5")
  
  diamondsWithHighTrendyScores.select("price").as[Result]
}
```

Here to test, we need a Spark Session (the Spark Session is the entry point to execute all the functions of Spark).

We need to create our datasets and to join them.

We also need a SparkSession to import Spark implicits. We can notice that because we have a SparkSession in our method signature. It is useful to make implicits transformations needed by Spark. In this example, it is useful to cast our final Dataset in Result.

Some people use a mini cluster to get a SparkSession in their tests. It leads to slow tests.

## Spark Session in our tests

We found another solution. We decided to use a Spark Session in our tests.

You could do something like this :

```scala

class DiamondsWithTrendyColorsSpec extends Specification {
  "DiamondsWithTrendyColors" should {
    
    //create a spark session
    val spark: SparkSession = {
    SparkSession
      .builder
      .master("local")
      .appName("spark test")
      .getOrCreate
  }

    "Give the diamonds prices for trendy colors" in {
      //create datasets
      val diamonds: Dataset[Diamonds] = spark.read.parquet...
      val trendyColors: Dataset[TrendyColors] = spark.read.parquet...
      
      //call the function with the spark session
      val result: Dataset[Result] = priceOfDiamondsWithTrendyColors(diamonds, trendyColors, spark)
      
      //Test the result
      result....
    }
}
```

We do not want to test Spark. We are pretty sure it works. But we want to test if we are good using Spark.

## Spark Session in a wrapper

We create a spark session for our test. But we are going to need it for almost all our tests. We found (thanks to the web and their bloggers) a solution.

We are going to use a wrapper for all our tests that need a Spark session.

We build a trait with a Spark session this way:

```scala
import org.apache.spark.sql.SparkSession

trait SparkSessionTestWrapper {

  val spark: SparkSession = {
    SparkSession
      .builder
      .master("local")
      .appName("spark test")
      .getOrCreate
  }
}
```

And use it this way:

```scala
class DiamondsWithTrendyColorsSpec extends Specification with SparkSessionTestWrapper {
  "DiamondsWithTrendyColors" should {

    "Give the diamonds prices for trendy colors" in {
      ...
    }
}
```

Now we can use the same Spark session for all our tests.

## External files VS DataFrames/Datasets creation

At the beginning, I was using files as inputs to respect our real inputs. But sometimes perfectionism can be your enemy. Now I prefer using DataFrames or Datasets creation with the function *toDS* or *toDF*.

```scala

class DiamondsWithTrendyColorsSpec extends Specification with SparkSessionTestWrapper {
  "DiamondsWithTrendyColors" should {

    "Give the diamonds prices for trendy colors" in {
        val diamonds: Dataset[Diamonds] = Seq(
          Diamond("green", 1200),
          Diamond("red", 200)
         ).toDS
         
        val trendyColors: Dataset[TrendyColors] =  Seq(...
        
        ...
    }
}
```

## Performance

That was a good start. I was very glad to have found all these solutions. But I realised that it was not enough.

We faced performance issues.

For instance, we had code like the following:

```scala
lass DiamondsWithTrendyColorsSpec extends Specification with SparkSessionTestWrapper {
  "DiamondsWithTrendyColors" should {

    "Give the diamonds prices for trendy colors" in {
        val diamonds: Dataset[Diamonds] = ...
        val trendyColors: Dataset[TrendyColors] =  ...
        
        val expected: Array[Result] = ...
        val result: Dataset[Result] = priceOfDiamondsWithTrendyColors(diamonds, trendyColors, spark)
                     
        //Action "collect" that launches all the transformations before
        result.collect must beEqualTo(expected)
      
        //Action "count" that launches all the transformations before again
        result.count must beEqualTo(3)
    }
}
```

The problem is that *count* and *collect* are two Spark actions. Only actions launch the computation. Using *count* and then *collect*, we are launching twice the *priceOfDiamondsWithTrendyColors* function.

To avoid that, we decided to use once *collect* to work with Scala arrays and not Spark. And then with this array, we make our tests.

```scala

class DiamondsWithTrendyColorsSpec extends Specification with SparkSessionTestWrapper {
  "DiamondsWithTrendyColors" should {

    "Give the diamonds prices for trendy colors" in {
        val diamonds: Dataset[Diamonds] = ...
        val trendyColors: Dataset[TrendyColors] =  ...
        
        val expected: Array[Result] = ...
        val result: Dataset[Result] = priceOfDiamondsWithTrendyColors(diamonds, trendyColors, spark)
        
        // It launches the "collect" action and stores the result
        val resultAsArray: Array[Result] = result.collect
                        
        //We use this result twice
        resultAsArray must beEqualTo(expected)
        resultAsArray.size must beEqualTo(3)
    }
}
```

## Run once globally, test unitarly

To speed my tests, I run once a global action with Spark and test it unitarly.

Suppose I have a function that takes a dataset of diamonds as an input and returns a median price by color.

A classical way is to run a process with pair values and another with impair values.

But Spark is slow when testing.

Another way is to run only once this process. We put pair values for color *green* and impair values for color *red*. We could then check the results in different tests.

```scala

class DiamondsSpec extends Specification with SparkSessionTestWrapper {
  "Diamonds" should {

    "Give the median price for diamonds" in {
        val diamonds: Dataset[Diamonds] = ...
         
        val result: Array[Result] = ...collect
      
        result.count(diamond => {
          color == "green" && median == 890
        }) must beEqualTo(1)
      
        result.count(diamond => {
          color == "red" && median == 567
        }) must beEqualTo(1)
        
        ...
    }
}
```

## Conclusion

In this article, you can find the solutions I use to test with Apache Spark.

I found these ones thanks to several blogs and discussions. I am open to other ways to do it. Feel free to share yours.

I attached some links where you can find more information about this subject.

**Resources**:
- [Stack Overflow response](https://stackoverflow.com/questions/43729262/how-to-write-unit-tests-in-spark-2-0)
- [Testing spark applications](https://medium.com/@mrpowers/testing-spark-applications-8c590d3215fa)
- [How to cut the run time of a Spark SBT test suite by 40%](https://medium.com/@mrpowers/how-to-cut-the-run-time-of-a-spark-sbt-test-suite-by-40-52d71219773f)

**Updates:**
You will also find frameworks designed to test with Spark and frameworks designed to test data with Spark such as [Deequ](https://github.com/awslabs/deequ).

Thank you for reading.
