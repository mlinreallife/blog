---
twitter:
- image: "data_versioning.png"
title: "Issue 1: Data versioning, tips for Pytest, freelancing, etc"
description: "First issue"
date: 2020-11-12T07:01:10+02:00
draft: false
description: Machine learning in real life is hard.  Finding your way into all the methods and tools is not easy. Here you will find some resources that me recently to do data versioning, tests or data drift detection.
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

Machine learning in real life is hard.  Finding your way into all the methods and tools is not easy.
Here you will find some resources that me recently to do data versioning, tests or data drift detection.

# English resources

## [Comparing Data Version Control Tools - 2020](https://dagshub.com/blog/data-version-control-tools/)

A great comparison between all the tools you can use to do data versioning.

![Data versioning comparison](/data_versioning.png)

>Managing data versions is a necessary step for data science teams to avoid output inconsistencies. Without data versioning tools, your on-call data scientist might find themselves up at 3 a.m. debugging a model issue resulting from inconsistent model outputs.

## [Pytest Options: Best Practices and Examples](https://queirozf.com/entries/pytest-options-best-practices-and-examples)

A short but useful article about tips to do tests with Pytest for Python:
- Show stdout output using *pytest --capture=tee-sys*
- Run single test using *pytest path/to/test.py -k 'test_foo'*
- Etc.

## [Failing Loudly: An Empirical Study of Methods for Detecting Dataset Shift](https://arxiv.org/abs/1810.11953)

Failures in data science are silent. This paper tests different solutions to get a practical way to fail loudly by doing data drift detection. The library *Alibi-detect* is based on this one.

![Failing loudly process](/failing_loudly_paper.PNG)

## [The art of being right in your job]({{< ref "/posts/the_art_of_being_right.md" >}})
This week, I published an article about *The Art of being right* written by Arthur Schopenhauer.

Have you ever struggled to explain why automated tests are important (or anything like that) to very reluctant and dogmatic but influential people such as well-established but very old school architects for instance? This book can help you with that.

# French resources

## [Etre freelance c'est être entrepreneur (A freelancer is an entrepreneur)](https://smartlink.ausha.co/punkindev/episode-10-etre-freelance-c-est-etre-entrepreneur)

Si vous êtes freelance ou que vous projetez de le devenir, cet épisode est pour vous.
Même si vous n'êtes pas freelance, vous apprendrez quelques astuces pour négocier votre futur salaire.

If you're a freelancer or plan to be one, this episode is for you.
Even if you're not a freelancer, you will learn some tips to negotiate your future salary.


Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
