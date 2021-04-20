---
title: "Issue 13: Kubernetes and DevOps concepts"
date: 2021-03-01T07:01:10+02:00
draft: false
images: [blue_green.gif] 
description: Kubernetes is a tool. The concepts that are around this one are interesting: zero downtime deployment, containers orchestration, scaling, etc. They help to deploy safely and then to get solid ML systems. It's relevant to understand these concepts. This week, I would like to highlight some of them through different resources.
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

Kubernetes is a tool. The concepts that are around this one are interesting: zero downtime deployment, containers orchestration, scaling, etc. They help to deploy safely and then to get solid ML systems. It's relevant to understand these concepts. This week, I would like to highlight some of them through different resources.

## [Cloud Native DevOps with Kubernetes](https://www.oreilly.com/library/view/cloud-native-devops/9781492040750/)

The book is about Kubernetes but also about some DevOps concepts in general.

 The keypoints for me are:
 - The hype of Kubernetes will disappear and that's good. These kinds of tools will become standards.
 - It's hard to deploy yourself Kubernetes. Use a cloud provider instead.
 - There are tools around Kubernetes that will help you such as [Helm](https://helm.sh/).

 > Helm helps you manage Kubernetes applications — Helm Charts help you define, install, and upgrade even the most complex Kubernetes application.

 > Charts are easy to create, version, share, and publish — so start using Helm and stop the copy-and-paste.

 - Use [Kubeval](https://github.com/instrumenta/kubeval) to validate your Kubernete manifests
 
 > kubeval is a tool for validating a Kubernetes YAML or JSON configuration file. It does so using schemas generated from the Kubernetes OpenAPI specification, and therefore can validate schemas for multiple versions of Kubernetes.

 - Use [Sops](https://github.com/mozilla/sops) to get a simple way of managing your secrets 
 
 > Sops is an editor of encrypted files.

![sops_demo](/sops.gif)
 
 My favourite chapter of the book is *Observability and Monitoring*. *Observability* is a catch-all term that covers different techniques: black-box checks, metrics, logging and tracing.
 
 > The observability of your system is a measure of how well-instrumented it is, and how easily you can find out what's going on inside it.

It's also crucial to know what to check. A system that is 99,9% of the time up doesn't mean that users are happy. Your system can lag and your users can turn away from it.

##[Kubernetes - Be sure of being ready for real zero downtime deployment](https://medium.com/ni-tech-talk/optimizing-revenue-with-bayesian-a-b-testing-5068e8ac41ea)

I wanted to speak of a mistake that is easy to do with Kubernetes but harmful: not setting the readiness of your application. It can break the zero downtime concept. In this article, I highlight the problem and the solution.

## [Zero-downtime Blue Green Deployments for Microservices](https://medium.com/@dantwining_26268/zero-downtime-blue-green-deployments-for-microservices-7896558623b2)

This article explains the principle of blue green deployment with animations.

![blue_green](/blue_green.gif)

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
