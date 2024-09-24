# Frequently Asked Questions (FAQ)

## Table of Contents

`**(contents need updating)**`

Origins
  - What is the purpose of the project?
  - Who made TaskCollect?
  - Is TaskCollect finished?

Usage
  - How do I access TaskCollect?
  - Why is TaskCollect so difficult to install on my computer?
  - How do I use TaskCollect?
  - Will I never have to use platform X again?

Features
  - Why doesn't TaskCollect have feature X?
  - Does TaskCollect support platform X?
  - Why is feature X not available even though platform Y implements it?
  - Will TaskCollect solve my time management issues?
  - Why is there no place to view messages from platform X?
  - When will you fix bug X and/or implement feature Y?

Implementation
  - Why is TaskCollect not written in language X?
  - Are there any Docker images available for TaskCollect?
  - Is TaskCollect scalable?
  - Why does TaskCollect not use JavaScript framework X?
  - Will you implement incremental loading?
  - Why is the TaskCollect repository not hosted on GitHub?
  - Why is there a different version of TaskCollect on GitHub?
  - Why are you reimplementing portions of the Go standard library?
  - Why have you done X instead of doing Y?

Troubleshooting
  - Why is page X loading so slowly?
  - Page X isn't loading and/or is displaying an error; why is that?
  - My institution isn't listed; what should I do?
  - Why can't I login with my institution-provided login details?

## Origins

### What is the purpose of the project?

The original purpose of the project was to tackle an aggravating issue — teachers in each class would use multiple educational platforms to teach, and often these chosen sets of platforms differed from teacher to teacher. The amount of housekeeping required each night from the perspective of a student was enormous — one had to keep track of resources and tasks across over ten platforms. A request to our school administration for the unification of educational platforms would have unlikely been realised. We chose an alternative route — to build a platform that would act as a single interface to all existing platforms — a platform multiplexer. While the issue became somewhat less serious in the coming months, we continued our project in hope that we could help all students in our school be more productive in their learning.

Moving towards the v1 release, we realised TaskCollect also served another useful function — it acted as a "frontend" to platforms we didn't particularly like. This mindset, coupled with the notion of a "learning manager" program that would give students full control of their learning, gave rise to the v2 proposal.

### Who made TaskCollect?

TaskCollect was developed by a team of four (then) secondary school students ([kvo][1], [rayokamoto][2], [Wasabi1092][3], [al2f][4]) who spent significant time outside school hours writing the implementation for TaskCollect. The project leader and maintainer continues to be kvo.

### Is TaskCollect finished?

Technically speaking, yes. TaskCollect reached version 1 in January 2023, and is thus considered "complete". However, we constantly find ways in which TaskCollect can be improved, and try to make changes accordingly. As an example of our continued work, a proposal for version 2 is currently being developed.

## Usage

### How do I access TaskCollect?

TaskCollect is currently developed as a web server, not an app, meaning that people can set up websites from the TaskCollect software (*instances* of TaskCollect). No public instances are currently available. If you want to use TaskCollect, you will need to download TaskCollect, run the web server on your computer, and access your local instance via http://localhost:8080/

### Why is the TaskCollect server so difficult to install on my computer?

TaskCollect is developed as a web server, not an app, hence our software release & distribution process is catered to server administrators, not end users. We do not provide installers for TaskCollect, but you can follow [these steps](institutions/deploy.html) to deploy a TaskCollect instance on your own computer.

### How do I use TaskCollect?

If you are using an existing TaskCollect isntance, simply navigate to its website. If you wish to self-host, follow [these steps](institutions/deploy.html). A [tour](docs/tour.html) of TaskCollect is also available, should you wish to familiarise yourself with TaskCollect's features.

### Will I never have to use platform X again?

If you're lucky, you might be able to use a platform entirely through TaskCollect. This depends on your use case and also the degree to which TaskCollect can support the platform in question. However, platforms might have proprietary features that are infeasible or impossible to provide an interface to. In these cases, TaskCollect might provide the URL to the relevant webpage on the platform (if one exists), or not implement support for that feature at all.

Educational platform support is a community project. We don't guarantee that support for any given platform is complete nor existent.

## Features

### Why doesn't TaskCollect have feature X?

There are two possible reasons — either we have decided the feature would be harmful to our project goals, or no one has implemented it yet. Most likely, it is the latter. Our team is small and our time is limited — even features that are at the top of our priority list may need several months before they are implemented.

If you have a feature that is not listed on our ticket list, please send an email with your feature request to <taskcollect-discuss@lists.sr.ht>

### Does TaskCollect support platform X?

Probably not. Platform support is a time-consuming and arduous task, and most of our team members are only willing to add platform support if they are individually affected and no one else volunteers to do it.

If you want a platform to be supported, you will most likely need to implement support yourself (and [email][5] your pull request to us), or hire someone to implement support for you (and send us a pull request). We do what we can, but we are just volunteers.

### Why is feature X not available even though platform Y implements it?

There oculd be several reasons for this. First, it could be simply that we are unaware of the feature. Another possibility is that we are aware that the feature exists but we have not yete had the time to implement it in TaskCollect. The final possible opiton is that we are aware of the feature but we believe that it would be unfitting to implement in TaskCollect — either because it is superfluous or there is a better way to solve hte source issue.

As an example, TaskCollect does not support OAuth or TOTP MFA for login because it would make TaskCollect logins unnecessarily burdensome. Instead, TaskCollect automatically completes OAuth authentication by pretending to be a user inputting their credentials into the Oauth dialog, and automatically generates TOTP codes for MFA by having the user input their MFA secret key. As a result, TaskCollect users no longer have to worry about inputting their credentials 10 times, or pulling out their phone for every login attempt.

### Will TaskCollect solve my time management issues?

Only you can solve your own time management issues. We provide you the tools to make time management easier, but as for the rest, the onus is on you.

### Why can't I view messages from platform X?

We believe in open standards, and proprietary message protocols are the opposite of that. We provide a button in TaskCollect that allows you to forward all unread messages to your email address, as emails. If you believe this will clutter your inbox, you should set up a rule for incoming emails from `no-reply@<TASKCOLLECT-INSTANCE-HOSTNAME>` (e.g. to move them to a  different email folder), where `<TASKCOLLECT-INSTANCE-HOSTNAME>` is the domain name of your TaskCollect instance.

### When will you fix bug X and/or implement feature Y?

If a ticket has not been filed to https://todo.sr.ht/~kvo/taskcollect, you should email us with your request at <~kvo/taskcollect-discuss@lists.sr.ht>. If a ticket has been filed, it is likely that we will not address your ticket for a number of months. We are full-time students, and our contributions to TaskCollect come from what free time we have left at the end of the day. If you think you have the knowledge and/or skills to address a ticket yourself, you are more than welcome to do so. [Contributions are welcome!](contrib.html)

### When will you make an app for TaskCollect?

We are currently in search of a GUI library that would suit the needs of TaskCollect. We are looking for a GUI library that:
  - can be statically linked with the TaskCollect executable
  - has support for Windows (amd64, i386), macOS (arm64, amd64), Linux (amd64, i386, arm64, arm), Android (arm64, arm, amd64, i386), and iOS (arm64, amd64)
  - can be trivially cross-compiled and cross-linked for all the above platforms
  - when used, results in code that is easy to read, understand, and maintain

We are currently leaning towards creating our own GUI library for these purposes, using Go's [exp/shiny]() for our cross-platform backend and various existing high-level GUI libraries as inspiration for the programmer interface. Searches for existing libraries continue.

## Implementation

### Why is TaskCollect not written in language X?

TaskCollect is written in Go for a number of reasons. Firstly, it compiles easily across different operating systems and CPU architectures, and produces statically linked binaries. Secondly, it has great built-in support for networking, HTTP, concurrency, and HTML, all of which are highly important to TaskCollect. Thirdly, the language is easy to learn, which is crucial considering that contributors to TaskCollect will almost always be students. Go is certainly not a flawless language, but it is the best we can find that meets our requirements.

### Are there any Docker images available for TaskCollect?

No. We believe running an additional operating system for each service is a harmful approach to developing distributed systems. In our opinion, the correct solution to solving the problem of "but it it works on my machine" is static library linking and trivial cross-compilation support, both of which are provided by Go. Distributed systems can be designed with plain executables as services, without the unnecessary overhead of an additional operating system.

### Is TaskCollect scalable?

Not yet. The current implementation involves a single binary which does a multitude of tasks, ranging from authentication to handling HTTP requests to web scraping. A move to enforce separation of concerns is planned, but we cannot yet say when it will happen.

### Why does TaskCollect not use JavaScript framework X?

We believe the coonsequences of using a JavaScript framework for TaskCollect outweigh the benefits. Having the entire interface generated by JavaScript means increased client-side bloat, reduced accessibility, an additional dependency tree we have to keep track of, and increased complexity in our building, running, and deployment processes. This is not what we want for our users nor our contributors.

### Will you implement incremental loading?

No. See the [answer above](). To compensate for the fact that data retrieval from educational platforms is slow, we have implemented a loading animation mechanism that is both simple and doesn't require each page to be loaded by JavaScript.

### Why is the TaskCollect repository not hosted on GitHub?

[SourceHut is faster][8]. Additionally, SourceHut has first-class support for mailing lists, which makes it a much more attractive option than competitors such as GitHub or Codeberg.

### Why is there a different version of TaskCollect on GitHub?

Disregarding unrelated projects with the same name, there is a GitHub organisation called TaskCollect with repositories that are closely related to TaskCollect's own mission. This is an earlier, discontinued implementation of TaskCollect with differing views on how it should have been implemented. The code hosted on GitHub was the work of [xxcodianxx][6], [xxori][7], [kvo][1], and [Wasabi1092][3], and was almost ready for release. However, an important upstream platform (Daymap) changed its authentication mechanism and development ceased thereafter.

### Why are you reimplementing portions of the Go standard library?

We found certain parts of the Go standard library (v1.18 when we started) insufficient for our needs. Given that our requirements were well within our development capabilities, we decided to reimplement the parts of the Go standard librar we were least satisfied with.

### Why have you done X instead of doing Y?

We always try to find an approach that best suits the needs of our users and contributors. Sometimes this means exploring a different approach to a problem, which might not be the standard way of solving the problem, but one that may resolve the problem more effectively for our use case. Sometimes we are disproven in this, but equally so we are sometimes disproven that the standard approach is the best.

## Troubleshooting

### Why is page X loading so slowly?

TaskCollect has been developed to be as fast as possible. If a page is loading slowly, it is most probable that the platform from/to which data is being received/sent is being slow, not TaskCollect. Unfortunately, even though TaskCollect tries to mitigate as many issues of the platforms it connects to as possible, latency issues are usually unavoidable.

### Page X isn't loading and/or is displaying an error; why is that?

Most likely, TaskCollect failed to connect to an educational platform when retrieving/sending data. This is usually because the platform is unresponsive, or had a new interface/API change that breaks TaskCollect's support for that platform. In the rarer occasion that it isn't, the underlying problem is an unresolved bug in TaskCollect. Contact the administrator of your TaskCollect instance to identify the cause of the problem; they should have access to the server logs.

### My institution isn't listed; what should I do?

If your institution is not listed in either the list of suported platforms, or on the TaskCollect login page, then your institution's educational platforms are not supported. If you would like institution support to be added, you should either [contact us]() or [contribute to TaskCollect]().

### Why can't I login with my institution-provided login details?

If you are having trouble logging in with your institution-provided login details, then likely TaskCollect support for your institution has encountered an issue. [Contact us]() to resolve this issue.


[1]: https://kvo.envs.net
[2]: https://github.com/rayokamoto
[3]: https://github.com/Wasabi1092
[4]: https://al2f.codeberg.page/
[5]: <taskcollect-devel@lists.sr.ht>
[6]: https://github.com/xcodian
[7]: https://github.com/xxori
[8]: https://forgeperf.org
