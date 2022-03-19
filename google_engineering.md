How do Google engineers work?
=============================

October 2021

How do Google engineers work? Often times I, as an ex-Googler, need to recall
the way how Googlers worked. That's because, when I encounter a problem, I
usually try to imagine "What would XXXXX do?", where XXXXX is usually a great
Googler or ex-Googler.

Thankfully Google published lots of helpful information. The following
materials are good starters for those who want to take a quick look at Google
engineering.

* [Software Engineering at Google](https://arxiv.org/abs/1702.01715): A concise
and easy-to-read paper.
* [Software Engineering at Google](https://abseil.io/resources/swe-book): A
thick (but still easy to read) book. It even explains the roles of TLs, TLMs,
and eng managers. Free PDF available.
* [The Production Environment at Google, from the Viewpoint of an
SRE](https://sre.google/sre-book/production-environment/): A book chapter.
Describes basic Google infrastructure and development environment.
* [Google Style Guides](https://google.github.io/styleguide/): Coding style
guides. Google engineers must follow these guides (Or else code reviewers won't
approve their CLs).
* [Code search at Google Open Source](https://cs.opensource.google/): Shows
what their actual code look like.
* [SRE Books](https://sre.google/books/): Books written by Google's site
reliability engineers. Especially the 3rd one ("[Site Reliability
Engineering](https://sre.google/sre-book/table-of-contents/)") is a good
starting point.
* [Design Docs at Google](https://news.ycombinator.com/item?id=23915521): The
article linked here "tries" to describe what a Google design doc looks like. I
think it's quite close to actual Google design docs, except that they mostly
use Google Docs at Google. Google has templates for various types of design
docs.
* [Google's public design docs for Golang and
Chromium](https://news.ycombinator.com/item?id=20601043): Great examples.

And here's a comment I wrote on a [Quora post about
Google](https://qr.ae/pGVate):

"Re: #2, after leaving Google, I realized how valuable Google’s internal
engineering for source code management was. Their highly scalable source
repository (including integration with cloud/local filesystem that allows
fetching only the required parts) and distributed and fine-grained build system
made monorepo possible with such a gigantic codebase. And monorepo, with very
simple branching scheme (everybody looks at the mainline only, basically),
seems to bring very good advantages. Now with super powerful code search and
the web based IDE, it is fantastic. I truly miss many of them. Oh I forgot to
mention the unrealistically good code review system, originated from Guido van
Rossum’s Mondrian. And their culture that pursues high quality engineering."

EDITED Nov. 14, 2021: If you're curious about how Agile/Scrum are used at
Google: [link1](https://qr.ae/pGDja5), [link2](https://qr.ae/pGDjaU),
[link3](
https://www.reddit.com/r/agile/comments/af1pv1/do_tech_companies_like_airbnb_google_etc_do_scrum),
[link4](https://news.ycombinator.com/item?id=20600128),
[link5](https://qr.ae/pGDjer), and ...
[link6](http://steve-yegge.blogspot.com/2006/09/good-agile-bad-agile_27.html)
(This article by Steve Yegge is kinda extreme and militant, but I guess there
are many Googlers who would agree with it.)
