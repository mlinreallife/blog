---
title: "Issue 1: Data versioning, tips for Pytest, freelancing, etc"
date: 2020-10-22T19:01:10+02:00
draft: true
---

Machine learning in real life is hard. Finding your way into all the methods and tools is not easy.
Here you will find some resources that inspired me recently to do data versioning, tests or data drift detection.

# Resources in English

## [Comparing Data Version Control Tools - 2020](https://dagshub.com/blog/data-version-control-tools/)

A great comparison between all the tools you can use to do data versioning.

![Data versioning comparison](/data_versioning.png)

>Managing data versions is a necessary step for data science teams to avoid output inconsistencies. Without data versioning tools, your on-call data scientist might find themselves up at 3 a.m. debugging a model issue resulting from inconsistent model outputs.

## [Pytest Options: Best Practices and Examples] (https://queirozf.com/entries/pytest-options-best-practices-and-examples)

A short but useful article about tips to do tests with Pytest for Python:
- Show stdout output using *pytest --capture=tee-sys*
- Run single test using *pytest path/to/test.py -k 'test_foo'*
- Etc.

## [Failing Loudly: An Empirical Study of Methods for Detecting Dataset Shift](https://arxiv.org/abs/1810.11953)

The failures in data science are silent. This paper tests different solutions to get a practical way to fail loudly by doing data drift detection. The library *Alibi-detect* is based on this one.

![Failing loudly process](/failing_loudly_paper.png)

# Resources in French

## [Etre freelance c'est être entrepreneur (A freelancer is an entrepreneur)] (https://smartlink.ausha.co/punkindev/episode-10-etre-freelance-c-est-etre-entrepreneur)

Si vous êtes freelance ou que vous projetez de le devenir, cet épisode est pour vous.
Même si vous n'êtes pas freelance, vous apprendrez à négocier votre salaire.

If you're a freelancer or plan to do it, this episode is for you.
Even if you're not a freelancer, you will learn how to negotiate your salary.


Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.
