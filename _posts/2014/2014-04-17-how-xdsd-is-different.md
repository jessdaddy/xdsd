---
layout: article
title: "How XDSD Is Different"
date: 2014-04-17
author:
  name: Yegor Bugayenko
  avatar: http://www.gravatar.com/avatar/70942ffdd8084b5a51e17e3c0996d53c?s=300
categories: blog
disqus: true
tags:
  - process
  - human factor
description: |
  This article lays out the most important and critical
  differences between XDSD and traditional software
  development methodologies, including Agile
keywords:
  - extremely distributed development
  - motivation of programmers
  - project management
  - effective project management
---

eXtremely Distributed Software Development, or XDSD for short, is a methodology
that differs significantly from working in traditional software development
teams. Most XDSD methods are so different (yet critical) that many newcomers get
confused. This article should help you bootstrap once you join a project managed
with by XDSD principles &mdash; either as a developer or a project sponsor.

## We Pay Only For Closed Tasks

Unlike with many other projects, in XDSD, we pay only for closed tasks and the
agreed upon time budget. Let me explain by example. Let's say, you are a Ruby
programmer and you a get a new task that requires you to fix a broken unit test.
The task has a time budget of 30 minutes, as is the case most of the time.
Sometimes, though, tasks may have time budgets of fifteen minutes or one hour.

In our example, we agree upon a contract rate of $50 per hour. With the broken
test, you will receive $25 for completing the task &mdash; 30 minute tasked billed at
$50 per hour.

It does not matter how long it actually takes you to fix the test. Your actual
time spent on the project may be five minutes or five hours. Nevertheless, you
will receive compensation for 30 minutes of work only. If you fix the broken
test in 5 minutes, you receive $25. If the task takes you an hour, or even a
month, to complete, you still receive only $25.

Furthermore, if you fail to fix the unit test and close the task altogether, you
will receive no pay at all for the assignment.

You can view more details about this principle in the following articles:
[No Obligations Principle]({% post_url 2014/2014-04-13-no-obligations-principle %})
or
[Definition of Done]({% post_url 2014/2014-04-15-definition-of-done %}).

{% picture http://img.xdsd.org/2014/04/revolver-avi-with-dollar.jpg 0 Revolver (2005) by Guy Ritchie %}

As mentioned above, this is one of the most important differences between XDSD
and other methods. Many people get confused when they see this principle in
action, and some leave our projects because of it. They simply are used to being
paid by the end of the month &mdash; no matter how much work they actually
deliver. In XDSD, we consider this type of approach very unfair. We feel that
people who deliver more results should receive more cash. Conversely, those who
don't deliver should get less.

## We Deliver Unfinished Components

Since most of our tasks are half an hour in size, we encourage developers to
deliver unfinished components. Read more about this concept in the article
below:
[Puzzle Driven Development]({% post_url 2014/2014-04-12-puzzle-driven-development-by-roles %}).

## No Informal Communications

Unlike many other projects or teams you may have worked with, XDSD uses no
informal communication channels. To clarify, we never use emails, we never chat
on Skype and we don't do any meetings or phone calls. Additionally, XDSD
maintains no type mailing list. Our only method of communication is a ticket
tracking system (which in most projects consists of Github Issues.)

Moreover, we discourage horizontal communications between developers regarding
the scope of individual tasks. When assigned a task, your single and only point
of contact (and your only customer) is the task author. You communicate with the
author in the ticket to clarify task requirements.

When the requirements of a task are clear &mdash; and you understand them fully
&mdash; deliver the result to the author and wait for him to close the task.
After the author closes the task, the project manager pays you.

{% picture http://img.xdsd.org/2014/04/goodfellas-paulie-talking.jpg 0 Goodfellas (1990) by Martin Scorsese %}

We're very strict about this principle &mdash; no informal communications.
However, it doesn't mean that we are not interested in your opinions and
constructive criticism. Rather, we encourage everyone to submit their
suggestions and bugs. By the way, we pay for bugs (see the next section for
further details about bug reporting and payments.)

Since we have no formal communications, members of project teams are not
required to work at specific times. Instead, team members work at times
convenient for them in their time zones. This includes weekdays and weekends.

## We Pay For Bugs

Unlike many other software teams, XDSD welcomes bug reports in all our projects.
Therefore, we ask for bugs openly and expect team members to report them.
Review the following article for complete details on XDSD bug reporting:
[Bugs are welcome]({% post_url 2014/2014-04-13-bugs-are-welcome %})

We expect everyone involved with a project to report every bug found.
Additionally, we encourage team members to make suggestions. In XDSD, we pay
team members for every properly reported bug.

XDSD makes payments for reported bugs because we believe that the more of them
we can find, the higher the quality of the end product. Some new developers are
surprised when they receive tasks such as "you must find 10 bugs in class A."
Often, the natural reaction is to ask "what if there are no bugs?" However, we
believe that any software product may have an unlimited amount of bugs; it is
just a matter of expending the time and effort needed to discover them.

## Only Pull Request

We never grant team member access to the `master` branch &mdash; no matter how
long you work on a project. Consequently, you must always submit your changes
through pull requests (most of our projects are done in Github.)

We enforce this policy not because we don't trust our developers, but simply
because we don't trust anyone :)

## No Compromises About Code Quality

Before merge any changes to the `master` branch, we check the entire code base
with unit tests and static analyzers. Unit testing is a very common component in
modern software development, and one by which you should not be surprised.
However, the strictness of static analysis is something that often frustrates
XDSD newcomers, and we understand that. We pay much more attention to the
quality and uniformity of our source code than most of our competing software
development teams.

Even more important is that we never make compromises. If your pull request
violates even one rule of the static analyzer, it won't be accepted. And, it
doesn't matter how small or innocent that violation may look. This merging
process is fully automated and can't be bypassed.
