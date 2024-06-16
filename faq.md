# Frequently Asked Questions (FAQ)

## Table of Contents

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
### Why is TaskCollect so difficult to install on my computer?
### How do I use TaskCollect?

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
### Will TaskCollect solve my time management issues?
### Why is there no place to view messages from platform X?
### When will you fix bug X and/or implement feature Y?

## Implementation

### Why is TaskCollect not written in language X?

TaskCollect is written in Go for a number of reasons. Firstly, it compiles easily across different operating systems and CPU architectures, and produces statically linked binaries. Secondly, it has great built-in support for networking, HTTP, concurrency, and HTML, all of which are highly important to TaskCollect. Thirdly, the language is easy to learn, which is crucial considering that contributors to TaskCollect will almost always be students. Go is certainly not a flawless language, but it is the best we can find that meets our requirements.

### Are there any Docker images available for TaskCollect?

No. We believe running an additional operating system for each service is a harmful approach to developing distributed systems. In our opinion, the correct solution to solving the problem of "but it it works on my machine" is static library linking and trivial cross-compilation support, both of which are provided by Go. Distributed systems can be designed with plain executables as services, without the unnecessary overhead of an additional operating system.

### Is TaskCollect scalable?

Not yet. The current implementation involves a single binary which does a multitude of tasks, ranging from authentication to handling HTTP requests to web scraping. A move to enforce separation of concerns is planned, but we cannot yet say when it will happen.

### Why does TaskCollect not use JavaScript framework X?
### Will you implement incremental loading?

### Why is the TaskCollect repository not hosted on GitHub?

[SourceHut is faster][8]. Additionally, SourceHut has first-class support for mailing lists, which makes it a much more attractive option than competitors such as GitHub or Codeberg.

### Why is there a different version of TaskCollect on GitHub?

Disregarding unrelated projects with the same name, there is a GitHub organisation called TaskCollect with repositories that are closely related to TaskCollect's own mission. This is an earlier, discontinued implementation of TaskCollect with differing views on how it should have been implemented. The code hosted on GitHub was the work of [xxcodianxx][6], [xxori][7], [kvo][1], and [Wasabi1092][3], and was almost ready for release. However, an important upstream platform (Daymap) changed its authentication mechanism and development ceased thereafter.

### Why are you reimplementing portions of the Go standard library?
### Why have you done X instead of doing Y?

## Troubleshooting

### Why is page X loading so slowly?
### Page X isn't loading and/or is displaying an error; why is that?
### My institution isn't listed; what should I do?
### Why can't I login with my institution-provided login details?


[1]: https://kvo.envs.net
[2]: https://github.com/rayokamoto
[3]: https://github.com/Wasabi1092
[4]: https://al2f.codeberg.page/
[5]: <taskcollect-devel@lists.sr.ht>
[6]: https://xxcodianxx.github.io/
[7]: https://github.com/xxori
[8]: https://forgeperf.org
