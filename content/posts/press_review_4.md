---
title: "Issue 4: Resources to get an overview of a machine learning project"
date: 2020-12-23T07:01:10+02:00
draft: false
description: It's not easy to start when doing machine learning. This is why I would like to highlight some useful resources to get an idea of what a data science project looks like from end to end.
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

It's not easy to start when doing machine learning. This is why I would like to highlight some useful resources to get an idea of what a data science project looks like from end to end.

I also wanted to put forward a new tool to do data monitoring and tell you a story about debugging silent bugs in data science.

# [Machine learning engineering by Andriy Burkov](http://www.mlebook.com/wiki/doku.php)

A book about machine learning in real life. From data preparation to deployment, you will learn how to handle a real data science project.

As a summary, I can highlight 2 ideas I like:
 - Validating your model is not only about evaluating your accuracy. You also must be sure that your model is ethical and will be appreciated and used by your end-users.
 - Feature engineering is important. Test it intensively.

# [ML Production pipelines: a classification example by Adriana Menegozzo](https://databricks.com/session_eu20/ml-production-pipelines-a-classification-model)

30 minutes of video to get an overview from end to end of how to productionalize models.
It's straightforward and concise. 

As a summary: Test and monitor your predictive system. Don't forget that productionalizing a model is not a one-shot but a progressing process. You will improve over time.

# [Awesome production machine learning](https://github.com/EthicalML/awesome-production-machine-learning)

An awesome list of tools to productionalize models. If you're looking for a tool, it might be there. And if you know a tool that is not in the list, you can open a pull request.

Very good to know.

# [EvidentlyAI](https://github.com/evidentlyai/evidently)

Amazing! A tool to do data monitoring!

> Evidently helps analyze machine learning models during development, validation, or production monitoring. The tool generates interactive reports from pandas DataFrame. Currently, the Data Drift report is available.

![Data monitoring](/evidently_github.png)

# [Bugs are silent]({{< ref "/posts/drift.md" >}})

As a summary: Bugs in predictive systems are most of the time silent. Don't expect your users to raise their hands saying something is wrong. That won't happen. 

**Use monitoring instead of waiting from your end-users!**
