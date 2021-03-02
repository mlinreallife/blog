---
title: "Issue 8: Code standardisation and MLOps seen by Databricks"
date: 2021-02-16T07:01:10+02:00
draft: false
description: Code standardisation inside the same team is important. There are different ways to achieve this goal. In this newsletter, I also would like to talk about MLOps and the way Databricks presents that.
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

Code standardisation inside the same team is important. There are different ways to achieve this goal.
In this newsletter, I also would like to talk about MLOps and the way Databricks presents that.

## [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)
If you don't know where to start with code standardisation, the Python community released an official style guide named PEP 8. You can go through it.

## [How To Write Python Like A Senior Developer](https://towardsdatascience.com/how-to-write-code-like-a-senior-developer-9ee34555858f)

Code standardisation inside the same team is important. To do that, you can use Pylint in Python.
Pylint is based on PEP 8. With that, you don't have to know all the rules by heart. You can follow Pylint. You can integrate it in a CI/CD pipeline to get automatic checks.

## [Our Python Monorepo](https://medium.com/opendoor-labs/our-python-monorepo-d34028f2b6fa)

Another way to get code standardisation is to build a unique monorepo. I'm not sure the benefits are higher than the disadvantages. But I definitely believe reusing code between different projects is a path to standardisation and relaxation.

## [MLOps Virtual Event](https://databricks.com/fr/p/webinar/operationalizing-machine-learning-at-scale)

I recently attended a meeting provided by Databricks about MLOps. The recording is available on demand.

Here is what I've found interesting:
- One of the most evident benefit of The MLFlow Model registry is that it's a central place for the models
- Reminder: it's possible to auto log with MLFlow (if you don't need to log something special)
- Distribution of TensorFlow and Pytorch is available in the Databricks platform
- The new workspace should integrate more easily CI/CD needs
- H&M uses the following process to develop:
	- In your IDE, do all the things you need in a package and a notebook that is the glue (of the different elements of your package)
	- Launch your unit tests
	- Send the package and the notebook in Databricks with a local script
	- Launch your end-to-end test in the Databricks platform (manually)
	- Back to your IDE, commit and push
