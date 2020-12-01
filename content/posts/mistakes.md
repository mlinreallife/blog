---
title: "Four mistakes I've done in my career"
date: 2020-09-18T17:01:10+02:00
draft: true
---

Most of the time, as data scientists or developers, we speak about our successes. Today, I would like to deal with the mistakes I've done in my career. Sometimes mistakes can be a valuable share.
I've chosen four ones. I've sorted them from the least important one to the worst one.

# 1. Invoices in production
Once, I created invoices in production. I hadn't realised I was working in the production environment and wanted to debug something directly into the application.

Oops. I was livid. What was I gonna do?

To fix that, I removed the invoices created in production directly in the database.

**Which lessons can I learn from that?**

- To err is human
- Add a graphical option when you're connected to the production like a big warning. You can set this only for the admin users. This way, you have less chance of doing a mistake.

# 2. Stop the source of revenue of a company for one full day

Once I did a small pull request. In this one, I removed by error a line of code that was calling the way to count the advertisements that were displayed in the application. I was working in a company whose revenues were generated by advertisements.

Two people reviewed my pull request but didn't notice I had removed the line that was calling the micro-service in charge of counting the advertisements. The tests were okay.
 
 **Which lessons can I learn from that?**
 
 - To err can be collectively human.
 - Micro-services work. The application was not down. Only the advertisements counter was down.
 - Reviews are not enough.
 - Test when you call a micro-service if you have called it in your unit tests. Some libraries such as Atoum in PHP can help with that. You mock your micro-service and check that it is called.

# 3. Believing that 100% of code coverage and a green Sonar are enough
I've talked about two technical problems. For me, the worst mistakes are when you are intellectually wrong.

One of my biggest error was that at the beginning of my career, I did tests, but it was really bad tests. I was developing with PHP and my tests were doing the role of a compilator, no more. I hadn't realised yet that the purposes of tests are much more than that. 

As we had almost 90% of code coverage and a green Sonar, it was difficult for me to understand the problem. Then, I was sure that if unit tests didn't work, we needed to do functional tests.

I spent a lot of time writing functional tests. These one, as any functional tests, were slow and hard to maintain.

As a result, the team didn't launch them.

 **Which lessons can I learn from that?**
 - 100% of code coverage and a green Sonar are far from enough to get a code free of bugs.
 - Unit tests are great if you understand that you should use them to test the functionalities of your application.
 - Use, or at least test, Test Driven Development and/or a mutation testing tool to understand better what a good test is.
 - Be careful with functional tests. Use them the proper way.
 - Ask for advice from others when you have a problem.
 - Never be too sure to get the solution to a problem.

# 4. Feeling irritated about interruptions and questions
Far from all, I consider that the worst error in my career was to be reluctant to interruptions and questions from my colleagues. 

I was considering that only my work was worthwhile. I didn't consider my team. I didn't consider that the work done by my team was also my work.
I didn't notice that their work helped me as mine helped us. I was selfish and blind. As a consequence, I disliked being interrupted. I was irritated when someone asked me a question. I was even more irritated when she or he asked me about something I've already answered. I'm full of regrets when I think of that. I'm ashamed of myself. How could I be so egoistic and ignorant? After some time, I realised I was wrong. After this experience, I never did that again. Now, I try to show everyone that I'm happy to help and I AM.

 **Which lessons can I learn from that?**
 - If you work in a team, behave as a member of the team contributing to a collective work.
 - If you can't stand to work with others, find a job where you can be alone.
 - Don't be afraid of questions and interruptions. They make you progress too.

# Conclusion

I guess every developer or data scientist has already done mistakes. A bug or a bad manipulation can be critical, but its impacts are limited. When you're wrong in your overall assumptions, that can be much more harmful.

Thank you for reading. Feel free to contact me on [Twitter](https://twitter.com/saby_nastasia) if you want to discuss that.