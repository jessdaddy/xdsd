---
layout: article
title: Incremental Requirements Development With Requs
date: 2014-04-25
author:
  name: Yegor Bugayenko
  avatar: http://www.gravatar.com/avatar/70942ffdd8084b5a51e17e3c0996d53c?s=300
categories: blog
disqus: true
tags:
  - requs
  - requirements
  - incremental
description:
Requirements engineering can be done incrementally with Requs open source controlled natural language
keywords:
  - requs
  - requirements engineering
  - requirements development
  - incremental requirements development
---
Requirements engineering is one of the most important disciplines in software development. Perhaps, even more important than architecture, design or coding itself. 

Joy Beatty and Karl Wiegers in [Software Requirements](http://www.amazon.com/Software-Requirements-Developer-Best-Practices/dp/0735679665) argue that the cost of mistakes made in a requirements specification is significantly higher than a bug in source code. I totally agree.

In XDSD projects we specify requirements using [Requs](http://www.requs.org), a [controlled natural language](http://en.wikipedia.org/wiki/Controlled_natural_language) that sounds like English, while at the same time is parseable by computers. A simple requirements document in Requs may look similar to:

{% highlight text linenos=table %}
Department has employee-s.
Employee has name and salary.
UC1 where Employee gets raise: "TBD".
{% endhighlight %}


This Software Requirements Specification (SRS) defines two types (`Department` and `Employee`) and one method `UC` (aka "use case").

Requs syntax is explained [here](http://www.requs.org/syntax.html).

The main and only goal of requirements engineering in any XDSD project is to create a complete and non-ambiguous SRS document. The person who performs this task is called the "system analyst". This article explains his or her main tasks and discusses possible pitfalls.

## Tasks

We modify SRS incrementally, and our increments are very small. For instance, say we have the sample document I mentioned above, and I'm a system analyst on the project. All my tasks will be similar to "there is a bug in SRS, let's fix it".

Even if it is a suggestion, it will still start with a complaint about the incompleteness of the SRS. For example:

 * UC1 doesn't explain how exactly an employee receives a raise.
 * Does the salary of an employee have limits? Can it be negative?
 * How many employees can a department have? Can it be zero?
 * Can an employee receive a decrease in salary?

All of these [bugs]({% post_url 2014/2014-04-13-bugs-are-welcome %}) are addressed to me. I need to fix them by improving the SRS. My workflow is the same in every task:

 1. Understand what is required
 2. Change the SRS 
 3. Close the task

Let's try this step by step.

## Requirements Providers

As a system analyst, my job is to understand what product owners (aka "requirements providers") want and document their wishes. In most cases, their wants and wishes are very vague and chaotic. My job is to make them complete and unambiguous. That's why the first step is to understand what is required.

First of all, I must determine who the product owner is before I can begin. The product owner signs the SRS, so I should pay complete attention to his opinions. However, my job is not only to listen, but also to suggest. A good system analyst can provoke creative thinking in a product owner by asking the right questions.

OK, now I that know the identity of the product owner, I need to talk to him. In XDSD, we don't do any meetings, phone calls, or any other type of informal communications. Therefore, my only mechanism for receiving the information I need is with is &mdash; tickets.

I will submit **new** tickets, addressing them to the product owner. As there can be many product owners in a project, I must submit tickets that clearly state in the first sentence that the ticket pertains to questions for a particular owners. The person receiving the ticket will then determine the best person to answer it.

Thus, while working with a single task, I will submit many questions and receive many interesting answers. I'll do all this in order to improve my understanding of the product the owners are developing.
When I understand how the SRS should be fixed, it is time to make changes in the Requs files.

## Requs Files

The SRS document is generated automatically on every continuous integration build cycle. It is compiled from pieces called `.req` files, which are usually located in the `src/main/requs` directory in a project repository.

My job, as a system analyst, is to make changes to some of these files and submit a pull request for review.
[Github Guidelines]({% post_url 2014/2014-04-15-github-guidelines %}) explaina how to work with Github. However, in short, I need to:

 * Clone the repository;
 * Check out its copy to my computer;
 * Make changes;
 * Commit my changes;
 * Push them to my remote fork;
 * Submit a pull request
 
It doesn't really matter which files I edit because Requs automatically composes together all files with the `req` extension. I can even add new files to the directory &mdash; they will be picked up. Likewise, I can also add sub-directories with files.

## Local Build

Before submitting a pull request, I will try to validate that my changes are syntactically and grammatically valid. I will compile Requs files into the SRS document using the same method our continuous integration server uses to compile them.

Before I can compile, though, I need to install [JDK7](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html) and [Maven](http://maven.apache.org/download.cgi).

Afterwards, I make the following command line call in the project directory:

{% highlight bash linenos=table %}
mvn clean requs:compile
{% endhighlight %}

After entering the commands, I expect to see the `BUILD SUCCESS` message. If not, there are some errors and I should fix them. My pull request won't be merged and I won't be able to close the task if Requs can't compile the files.
Once compiled, I can open the SRS in any browser. It is in `target/requs/index.xml`. Even though it is an XML file, Google Chrome and Safari can open it as a webpage.

## Pull Request Review

Once all changes are finished, I will submit a pull request. A project manager will the assign someone to review my pull request and I will receive feedback.

In most cases, there will be at least a few corrections requested by the reviewer. Generally speaking, my requests are reviewed by other system analysts. Therefore, I must address all comments and make sure my changes satisfy the reviewer.

I will make extra changes to the same branch locally, and push them to Github. The pull request will be updated automatically, so I don't need to create a new one.

Once the pull request is clean enough for the reviewer, he will merge it into the `master` branch.

## Close and Get Paid

Finally, my pull request is merged and I get back to the task owner. I tell him that the SRS was fixed and request that he review it. His original problem should be fixed by now &mdash; the SRS should provide the information required.

He then closes the task and the project manager pays me within a few hours.
