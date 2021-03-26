---
title: "Issue 11: Machine Learning Design Patterns"
date: 2021-03-01T07:01:10+02:00
draft: false
images: [challenges.png] 
description: In this newsletter, I would like to focus on a book: *Machine Learning Design Patterns*. I strongly recommend it. It deals with common problems and possible solutions that you can encounter in your ML journey.
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


## [Machine Learning Design Patterns](https://www.oreilly.com/library/view/machine-learning-design/9781098115777/)
In this newsletter, I would like to focus on a book: *Machine Learning Design Patterns*. I strongly recommend it. It deals with common problems and possible solutions that you can encounter in your ML journey. 

From data representation to responsible AI, it is quite uplifting.

It consists of 30 patterns. To give you a taste of them, I would give you a brief overview of some of them.

### Data Representation - Feature Cross

Sometimes, when using separately the features x_1 and x_2, it's not possible to find a linear boundary that separates the classes. This means that to solve the problem, we have to make the model more complex, perhaps by adding more layers to the model. However, a simpler solution exists.

It's the ability to cross two features. For instance, you can concatenate hour_of_day + day_of_week.

### Problem Representation - Reframing

You can reframe your problem from regression to classification. 

For example, instead of predicting the perfect time needed to do a task, we can use bucketizer for the outputs and predict that.

We can also do the contrary. For example, we can consider ratings as infinite value.

The more a distribution is large, the more the model will be accurate if considered as a classification.
The more a distribution is tiny, the more the model will be accurate if considered as a regression.

### Model Training - Transfer learning

Transfer learning works because it lets us stand on the shoulders of giants, utilizing models that have already been trained on a large dataset to do image classification.

Transfer learning works for texts and images. It doesn't work for tabular data because they are too specific.

### Reproducibility -  Workflow Pipeline

> In the Worflow Pipeline design pattern, we address the problem of creating an end-to-end reproducible pipeline by containerizing and orchestrating the steps in our machine learning process. The containerization might be done explicitly, or using a framework that simplifies the process.

### Responsible AI - Heuristic Benchmark

> The Heuristic Benchmark pattern compares and ML model against a simple, easy-to-understand heuristic in order to explain the model's performance to business decision makers.

##[Apache Spark 3.1 Release: Spark on Kubernetes is now Generally Available](https://www.datamechanics.co/blog-post/apache-spark-3-1-release-spark-on-kubernetes-is-now-ga?utm_campaign)

> With the Apache Spark 3.1 release in March 2021, the Spark on Kubernetes project is now officially declared as production-ready and Generally Available. This is the achievement of 3 years of booming community contribution and adoption of the project - since initial support for Spark-on-Kubernetes was added in Spark 2.3 (February 2018).

## Holidays \O/

I'm going to take a break (2 weeks). As a consequence, there will no newsletter during this time.

See you soon!

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
