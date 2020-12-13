---
title: "Issue 3: Feature store, weird chatbot, XGboost for Spark and Airflow in Amazon"
date: 2020-12-10T07:01:10+02:00
draft: false
description: "Issue 3: Feature store, weird chatbot, XGboost for Spark and Airflow in Amazon"
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

This week, I think I've finally understood what a feature store is (thanks to Tecton). There is also some other news: better integration of the orchestrator Airflow in Amazon, distributed XGboost with Spark, a chatbot from Google which is better than before but still weird.

# [Introducing Amazon Managed Workflows for Apache Airflow (MWAA)](https://aws.amazon.com/fr/blogs/aws/introducing-amazon-managed-workflows-for-apache-airflow-mwaa/)

I'm a big fan of Apache Airflow which is a great tool to orchestrate your tasks. 
Then, I'm glad to hear about 
> A fully managed service that makes it easy to run open-source versions of Apache Airflow on AWS

# [What is a Feature Store?](https://www.tecton.ai/blog/what-is-a-feature-store/)

![What is a feature Store](/Enl1mtNW8AAi9Lz.jpg)

A great article about what a feature store is concretely. In a nutshell:
> A feature store is an ML-specific data system that:
>
> - Runs data pipelines that transform raw data into feature values
> - Stores and manages the feature data itself, and
> - Serves feature data consistently for training and inference purposes

# [Meena, the new chatbot of Google is still weird](https://voicebot.ai/2020/02/03/googles-new-meena-chatbot-imitates-human-conversation-and-bad-jokes/)

Chatbots are better and better year after year, but still weird:

![Meena discussion](/meena.png)

# [How to Train XGBoost With Spark](https://databricks.com/blog/2020/11/16/how-to-train-xgboost-with-spark.html)

> XGBoost is currently one of the most popular machine learning libraries and distributed training is becoming more frequently required to accommodate the rapidly increasing size of datasets. 

> XGBoost4J-Spark can now be quickly used to distribute training on big data for high performance and accuracy predictions

![XGboost with Spark](/xgboost.jpg)


Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss machine learning in real life.
