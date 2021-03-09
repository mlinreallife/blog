---
title: "Issue 9: Code standardization, container orchestration, lakehouse, cats: concepts needed to productionalize machine learning models"
date: 2021-03-01T07:01:10+02:00
draft: false
images: [challenges.png] 
description: I'm glad to see that we can find more and more papers about deploying Machine Learning. Challenges are multiple and everywhere. Let's dive a bit into these challenges and resources that discuss these.
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

I'm glad to see that we can find more and more papers about deploying Machine Learning. The paper **Challenges in Deploying Machine Learning: a Survey of Case Studies** focuses on challenges that you can encounter in this adventure. Challenges are multiple and everywhere. The authors of the paper tried to categorise and name them. Let's dive a bit into these challenges and resources that discuss these.

## [Challenges in Deploying Machine Learning: a Survey of Case Studies](https://arxiv.org/pdf/2011.09926.pdf)

> The survey shows that practitioners face challenges at each stage of the deployment. The goal of this paper is to layout a research agenda to explore approaches addressing these challenges.

A categorisation of the issues and concerns is helpful:
![Challenges](/challenges.png)

## [Different ways to tackle the data labelling bottleneck in machine learning](https://mlinreallife.github.io/posts/data_labelling/)

*Data management - Data augmentation - Labelling of large volumes of data*

> Labelling in machine learning is an issue. It is expensive and leads to boring tasks.

> You can keep the costs of labelling down with automatic solutions. I wanted to highlight some methods to do that.

## [Complete guide to Association Rules (1/2)](https://towardsdatascience.com/association-rules-2-aa9a77241654)

*Model learning - Model selection - Model complexity*

I didn't know this concept in machine learning. It is useful to find relationships between items.

In some use cases, it can be used instead of a more recommender system.

> Association Rules is one of the very important concepts of machine learning being used in market basket analysis.

> Association rules help uncover all such relationships between items from huge databases.

> Rules do not extract an individual’s preference, rather find relationships between set of elements of every distinct transaction. This is what makes them different from collaborative filtering.

## [Python Type Checking (Guide)](https://realpython.com/python-type-checking/)

*Model deployment - Integration - Software engineering anti-patterns*

This guide is very useful if you want to understand type checking in Python.

You can add types in Python. By default, they do nothing. But you can use tools such as Enforce or Pydantic that force the good usage of the types.

It's a way to get safer deployment and maintenance.

## [Machine Learning Systems: Security](https://sahbichaieb.com/mlsystems-security/)

*Cross-cutting aspects - Security*

With this article, I realise that I don't know very much about the security regarding machine learning itself. Then, I think this blog post is a good start.

> Machine Learning systems are complex software systems where software code and data are interlaced, so they do not only face computer security risks but also data threats. 
