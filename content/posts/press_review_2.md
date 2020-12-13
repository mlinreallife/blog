---
title: "Issue 2: Unit tests for data, Data + AI summit, etc"
date: 2020-11-26T07:01:10+02:00
draft: false
description: Machine learning in real life is hard. Finding your way into all the methods and tools is not easy. Here you will find some resources that inspired me recently to do unit tests for data and productionalize models.
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

Machine learning in real life is hard. Finding your way into all the methods and tools is not easy.
Here you will find some resources that inspired me recently to do unit tests for data and productionalize models.

# [Automating Large-Scale Data Quality Verification](https://www.amazon.science/publications/automating-large-scale-data-quality-verification)

It's the paper behind Deequ, a library to do unit tests for data. It's very instructive.
You will see how the tool was thought. I didn't know that it was possible to profile your data to help you decide the tests you want to launch. Very good to know.

# [Data + AI Summit](https://databricks.com/dataaisummit/europe-2020)

Key takeaways:

- Spark has become a platform used by Python (47%) and SQL (41%) users essentially. Many new recent functionalities for Python users: Koalas, UDF with pandas, etc.

- Companies struggle to deploy and maintain notebooks and prefer using Python modules instead. They sometimes use a mix of notebooks and Python modules or only Python modules.

- Realising the difficulties companies have with productionizing notebooks, Databricks decided to launch a new DataScience workspace with better integration with Git, CI/CD, and security. It will be launched in January.

- SQL analytics based on Redash is a new way to do dashboards based on SQL queries. It will be launched soon.

- DeltaLake is the standard for lakehouse (the best of data lakes and data warehouses) when you’re looking for reliability with ACID transactions, performance, governance, and data quality checks (work in progress).

- MLFlow is becoming an essential part of many architectures to deploy safely and to be able to reproduce previous runs. New functionalities are coming: better integration with data versioning with DeltaLake, integration with SHAP to do interpretability.

Some videos are available [here](https://www.youtube.com/c/Databricks/search?query=data%20time%20travel).

# [Model drift or how the pandemic killed thousands of predictive systems]({{< ref "/posts/drift.md" >}})

Last week, I published a quick introduction to *Model drift*.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss machine learning in real life.
