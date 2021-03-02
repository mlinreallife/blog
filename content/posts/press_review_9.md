---
title: "Issue 9: Code standardization, container orchestration, lakehouse, cats: concepts needed to productionalize machine learning models"
date: 2021-03-01T07:01:10+02:00
draft: false
images: [mia_cute.jpg] 
description: Code standardisation with Pylint, container orchestration with Kubernetes, lakehouse with DeltaLake, working with cats <3, these are many concepts that can be useful to productionalize machine learning. This is what I saw recently and thought interesting.
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

Code standardisation with Pylint, container orchestration with Kubernetes, lakehouse with DeltaLake, working with cats :heart:, these are many concepts that can be useful to productionalize machine learning. This is what I saw recently and thought interesting.

## [Why Pylint is both useful and unusable, and how you can actually use it](https://pythonspeed.com/articles/pylint/)

> Pylint saves the day.

> Pylint has a lot of useful errors and warnings… but also a whole lot of highly opinionated assumptions about how your code should look.

> Luckily Pylint has some functionality that can help: you can configure it to only enable a limited list of lint checks.

## [Kubernetes basics](https://www.youtube.com/watch?v=q1PcAawa4Bg&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT)

A serie of videos about Kubernetes done by Brendan Bruns, one of the cofounder of Kubernetes.

Well explained!

## [Kubeflow](https://www.youtube.com/watch?v=dC659IsHNyg&list=PLIivdWyY5sqLS4lN75RPDEyBgTro_YX7x&index=3)

A serie of videos about Kubeflow, a platform dedicated to data science and based upon Kubernetes.

I've never used it but it's always good to get an overview how the ecosystem around you.

## [Building Reliable Data Lakes with Delta Lake | Virtual Hands-on Lab](https://databricks.com/p/webinar/building-reliable-data-lakes-with-delta-lake-virtual-hands-on-lab)

If you're looking for ACID transactions, time travel, mixing the abilities of a data warehouse and a data lake, I recommend you to watch this webinar. It deals with DeltaLake, a tool developed by Databricks which has great capabilities.

## [Your cat might be better than focus](https://mlinreallife.github.io/posts/no_need_for_focus/)

I recently wrote an article to speak about the limits of focus in our jobs.

> Many books and people value focus and Pomodoro. I also value all of that. At the same time, you’re not executors. You need creativity, imagination, and distance with what you do. You need that more than I could have thought at the beginning of my career. This is why you also need to let your mind wander.
