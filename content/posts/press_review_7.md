---
title: "Issue 7: Recommendation systems and data engineering jobs"
date: 2020-11-09T07:01:10+02:00
draft: true
description: Once, I've assessed different recommendation systems through AB tests. They were black boxes for me. I've decided to focus my recent techno watch on recommendation systems. I wanted to understand better these black boxes. There are many ways to do recommendation systems. The solutions depend on your context and needs.

In this newsletter, I also would like to talk a bit about the roles of data engineers or machine learning engineers.
---

<!-- Begin Mailchimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/classic-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="https://github.us7.list-manage.com/subscribe/post?u=2170356f90245aa31be7ff655&amp;id=aabf54b022" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<h2>Sign up for a bi-weekly newsletter</h2>
    <div>Learn about data science in real life and machine learning in production</div>
<div class="indicates-required"><span class="asterisk">*</span> indicates required</div>
<div class="mc-field-group">
	<label for="mce-EMAIL">Email Address  <span class="asterisk">*</span>
</label>
	<input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL">
</div>
	<div id="mce-responses" class="clear">
		<div class="response" id="mce-error-response" style="display:none"></div>
		<div class="response" id="mce-success-response" style="display:none"></div>
	</div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_2170356f90245aa31be7ff655_aabf54b022" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>

Once, I've assessed different recommendation systems through AB tests. They were black boxes for me. This week, I've decided to focus my recent techno watch on recommendation systems. I wanted to understand better these black boxes. There are many ways to do recommendation systems. You can use reinforcement learning if you want. The solutions depend on your context and needs.

In this newsletter, I also would like to talk a bit about the roles of data engineers or machine learning engineers.

## [What is the difference between content based filtering and collaborative filtering?](https://www.quora.com/What-is-the-difference-between-content-based-filtering-and-collaborative-filtering)

As a summary:

This is the opportunity to understand two ways of doing recommender systems.

> Content based filtering - The point of content-based filtering system is to know the content of both user and item. Usually it constructs and then compare user-profile and item-profile using the content of shared attribute space. For example, for a movie, you represent it with the movie stars in it and the genres (using a binary coding for example).

It's the simpler way to process, but not the most efficient in complex cases.

> Collaborative filtering - Collaborative algorithm uses “User Behavior” for recommending items. They exploit behavior of other users and items in terms of transaction history, ratings, selection and purchase information. Other users behavior and preferences over the items are used to recommend items to the new users. In this case, features of the items are not known.

You can also use hybrid solutions.

## [Prototyping a Recommender System Step by Step Part 1: KNN Item-Based Collaborative Filtering](https://towardsdatascience.com/prototyping-a-recommender-system-step-by-step-part-1-knn-item-based-collaborative-filtering-637969614ea)

After having described 3 approaches to do recommender systems (content-based, collaborative filtering and hybrid), this article helps you build an item based collaborative filtering with KNN. 

At the end, the article discusses about the limitations of such a solution:

> popularity bias: recommender is prone to recommender popular items

> item cold-start problem: recommender fails to recommend new or less-known items because items have either none or very little interactions

There's also a scalability issue.

## [Prototyping a Recommender System Step by Step Part 2: Alternating Least Square (ALS) Matrix Factorization in Collaborative Filtering](https://towardsdatascience.com/prototyping-a-recommender-system-step-by-step-part-2-alternating-least-square-als-matrix-4a76c58714a1)

This post covers how to improve the previous KNN solution with matrix factorization. It uses ALS (Alternating Least Square), a way to build a distributed matrix factorization with Spark ML.

## [How does Netflix recommend movies? Matrix Factorization](https://www.youtube.com/watch?v=ZspR5PZemcs&t=229s)
> A friendly introduction to recommender systems with matrix factorization and how it's used to recommend movies in Netflix.

I found that it's easier to understand *matrix factorization* through this video than with the previous post. They complement each other.

## [We Don't Need Data Scientists, We Need Data Engineers](https://www.mihaileric.com/posts/we-need-data-engineers-not-data-scientists/)

As a summary:

> There are 70% more open roles at companies in data engineering as compared to data science.

> Today, the bottleneck in helping companies get machine learning and modelling insights to production center on data problems.

## [Positive and Negative Engineering](https://medium.com/the-prefect-blog/positive-and-negative-data-engineering-a02cb497583d)

This article talks about two very interesting concepts: *positive data engineering* and *negative data engineering*.
    
As a summary:
    
> Positive data engineering is what we typically think engineers do: write code to achieve an objective.
    
> Negative data engineering is when engineers write defensive code to make sure the positive code actually runs. For example: what happens if data arrives malformed? What if the database goes down? What if the computer running the code fails? What if the code succeeds but the computer fails before it can report the success? Negative engineering is characterized by needing to anticipate this infinity of possible failures.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss machine learning in real life.
