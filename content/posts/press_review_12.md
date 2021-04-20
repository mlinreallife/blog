---
title: "Issue 12: Bayesian AB Tests"
date: 2021-03-01T07:01:10+02:00
draft: false
images: [bayes.png] 
description: Recently, for an R&D project, I had to implement Bayesian AB tests. As AB tests are an important key to develop safely and surely, I decided to present to you what I've learnt so far. I focused my reasearch on the Pymc3 library.
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

I have already worked with AB tests, but it was frequentist AB tests.

Recently, for an R&D project, I had to implement Bayesian AB tests. As AB tests are an important key to develop safely and surely, I decided to present to you what I've learnt so far. I focused my reasearch on the Pymc3 library.

## [Easy as ABC: A quick introduction to Bayesian A/B testing in Python](https://www.youtube.com/watch?v=nRLI_KbvZTQ&t=293s)
It's a very nice and brief introduction to Bayesian AB tests.

In Bayesian tests, you must set a previous distribution. It's your priors, what you already know.

##[Optimizing Revenue with Bayesian A/B testing](https://medium.com/ni-tech-talk/optimizing-revenue-with-bayesian-a-b-testing-5068e8ac41ea)

Here you can find an example of Bayesian AB tests with Pymc3. Beyond that, the advantages of Bayesian AB tests are explained.

> Bayesian A/B Testing employs Bayesian inference methods to give you ‘probability’ of how much B is better (or worse) than A.


> The immediate advantage of this method is that we can understand the result intuitively even without understanding what p-value or null hypothesis means. This means that it’s easier to communicate with our business stakeholders in a language that makes sense — the language of risk and value.

> Another advantage is that since Bayesian statistics don’t care for statistical significance, you don’t have to worry too much about the test size when you evaluate the result. You can start evaluating the effect from day one by reading the probability of B being better than A. Of course, as we get more data our answers will be more accurate, but since we are using the language of probabilities, we are able to say, for example, “A is better than B with 60% probability” rather than “We don’t have enough data” So you can decide if you want to wait any longer.

##[A/B testing with probabilistic programming and PyMC3 (part I)](https://towardsdatascience.com/a-b-testing-with-probabilistic-programming-and-pymc3-part-i-7ae52d45bc41)

I had difficulties understanding how to interpret the results with the precedent link. Then, I found this new link. It helped me a lot.

##[Bayesian AB Tests with Pymc3](https://github.com/NastasiaSaby/bayesian_ab_test)

I decided to mix the code of the 2 precedent links to get a small implementation. 
In this repository, you can find a Jupyter notebook and a Databricks notebook that implement an example of Bayesian AB tests.

![Graphical results](/bayes.png)

![Textual results](/result_abtests.png)

That's not enough to get something very robust in production. For instance, this solution doesn't handle big data. It is more something for an R&D project as mentioned early. But the idea can be very valuable for safe productions. This is why I wanted to highlight AB tests and Bayesian AB tests.

##[Machine learning in production](https://leanpub.com/machinelearningenproduction)
I have recently self-published a book about Machine Learning in production. I compiled all the things I have learnt so far. The book is written in French. 

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
