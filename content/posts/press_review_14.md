---
title: "Issue 14: Market yourself, ACID transactions in DeltaLake, OpenSource and Bayesian ABTests"
date: 2021-03-01T07:01:10+02:00
draft: false
description: Market yourself, ACID transactions in DeltaLake, OpenSource and Bayesian ABTests
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

Market yourself, ACID transactions in DeltaLake, OpenSource and Bayesian ABTests. I've seen and worked on a lot of different topics these day. They are diverse, but I thought that they can be all useful.

## [Diving Into Delta Lake: Unpacking The Transaction Log](https://databricks.com/blog/2019/08/21/diving-into-delta-lake-unpacking-the-transaction-log.html)

I have presented a lot DeltaLake as its purpose was only for time travel. It's not the only feature. One that is also very important is ACID transactions. 
DeltaLake solves conflicts optimistically. 

> In general, the process proceeds like this:

> Record the starting table version.
> Record reads/writes.
> Attempt a commit.
> If someone else wins, check whether anything you read has changed.
> Repeat.

DeltaLake gives the possibility to modify parts of different data concurrently. If two programs are modifying the same portion of data, DeltaLake executes the modifications serially. If there's a conflict, an error is raised.

> In the vast majority of cases, this reconciliation happens silently, seamlessly, and successfully. However, in the event that there’s an irreconcilable problem that Delta Lake cannot solve optimistically (for example, if User 1 deleted a file that User 2 also deleted), the only option is to throw an error.

##[How to market yourself (without being a celebrity)](https://www.youtube.com/watch?v=tkBCPqWKCL8)

Let's start with a recap of the presentation:

Why should you market yourself?

You have experience and skills. It's normal to want recognition for that.
It can help you find another job or be promoted. Then, we will distinguish outside and inside marketing.

Tips to market yourself outside:

- Brand yourself
- You can choose a logo
- Keep the same good picture
- Be consistent
- Create content on your own platform (blogs or podcasts for instance)
- Speak with people (for example, you can do a blog post to answer to another one)
- Choose a domain of expertise. It should be a niche but not too much. You must find a balance.
- You don't have to be an expert at the beginning: just speak about the subject you want.

Tips to market yourself inside your company:

- Always keep with you a quick summary (one page) of your accomplishments in your company: it helps you to be ready to market yourself at anytime. More than that, it helps you for bad days to realise that you're able to bring value. 
- During stand-ups and demos, be joyful and present things as accomplishments.
- Help and mentor people
- Start another project to show that you're able to dedicate yourself and to take initiatives
- Create a newsletter internally and share your knowledge

I was pleased to attend this talk. Often, we speak about outside marketing. It's the first time I saw something about inside marketing. It's valuable. 

I don't totally agree with the last two points about marketing yourself inside your company. I didn't make researches about this subject. But I have already experienced the fact of starting another project, creating an internal newsletter and organising talks. My objective was not too market myself absolutely. That's true that it helped me a lot though. But there are counterparts. It takes time and you don't focus on the project you're paying for. Now, what I prefer doing is focusing only on my project and gravitate around to improve it and communicate about it. It's less demanding and I think more useful for everyone.

Be aware that here I'm giving you personal statistics. By definitions, it is worthless compared to a real study.

## [Overview of Bayesian AB Tests](https://mlinreallife.github.io/posts/bayesian-ab-tests/)

I’m working on Bayesian AB Tests for a showcase project.

Then I decided to do a quick memo on some principles regarding Bayesian AB Tests.

## [Contributing to open source is not what I thought it was](https://mlinreallife.github.io/posts/bayesian-ab-tests/)

When I was younger at the beginning of my career, I was fascinating by the idea of open source projects. I thought that contribution was unreachable for me. I still think it is difficult to open a pull request that modifies the code of a complex project like Apache Spark. But I have also realised that open source is not only about modifying code.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
