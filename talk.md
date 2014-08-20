# Leveraging Node.js
at Fluencia

Note:
- My name is William Bert
- Thanks for coming tonight. I'm really excited to be here.
- I'm going to talk about how we leverage Node.js at Fluencia to help deliver
  lots of value to our users as quickly as possible.
- Aprovechando Node.js



### 2011: the situation.

* Have a fast-growing website that cannot go down or slow down, ever.
* Want to build a brand new SPA that people will pay you money to use.
* Do it with two or three engineers. ASAP.

Note:
- I want to start by briefly turning back the clock to late 2011.
- Put yourself in the shoes of the CEO of a small (like 2-3 employees total) but
  growing company.
- (slides)



## What are you going to
## build the future on?

Note:
- This is the question the company was asking itself.
- The existing PHP codebase was showing its age.
- Engineering team at the time (which is really the CEO and a new director of
  engineering) was very aware of PHP's limitations as a language, community,
  etc..
- Where to go in the future?



<img class="logo" src="./img/logo_node.png" alt="Node.js">

Note:
- Big surprise.
- So this company went with Node, for reasons that I will talk about.
- I think this was a somewhat bold choice but showed a lot of foresight.
- I'd like to take credit for it, but I wasn't part of this company when this
  decision was made, in fact I should probably give a little more background...



<img class="logo" src="./img/logo_fluencia.png" alt="Fluencia">

Note:
- I'm a Senior Software Engineer at Fluencia. I've been here for a little more
  thna two years, since mid-2012.
- What is Fluencia? It's our company, and also one of our products.
- The product is the best way to learn Spanish online. SPA. Lots of lessons. 2
  years of college Spanish. Subscription. Launched 1 year ago. Over 150K users.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict">

Note:
- We also run a website called SpanishDict.com. That's the high-traffic site.
  It's older than Fluencia, and it used to be the name of the company, but we
  like Fluencia better.
- SpanishDict gets around 10 million unique visitors a month.
- Top result if you google "Spanish".
- Both of these products are backed by Node.
- Why? How did it come to be? Here is what the people who made that decision
  were thinking about...



### Wanted:

## Speed / scalability
## Community
## Productivity

Note:
- Speed/scalability: Google has made huge investment in making V8 fast. So Node
  is built on a very fast runtime.
- No threads. Instead, an event loop. Very lightweight, very scalable.
- Community: Big community and growing.
- Lots of libraries already, more being released all the time. Momentum.
- Productivity:
- Our focus is on relentlessly delivering value for our users.
- I think in 2011, choosing Node when thinking about productivity was a bold
  choice. But several reasons:
- Node does async control flow throughout, unlike other languages where it is
  bolted on, and standard lib / many libs don't support it. Builtin async
  support throughout was attractive.
- The core is small. The philosophy is for limited modules that can be pieced
  together. Simplicity. Choose from a wide variety of small modules and built
  something greater than the sum of the parts.
- It was stable enough that people were using it to get things, but it was
  continuously improving at a very rapid pace.
- And finally...



## Always bet on Javascript.

Note:
- It's ubiquitous.
- Common code between front-end and back-end is a nice win.
- Lessons learned in one can often be applied to other. Reduced cost of context
  switching. Actual shared code can make life easier.
- The future (in 2011) included an SPA. Would need to do heavy lifting in
  Javascript. Full JS stack had benefits.
- So this stack just makes sense.



## How we use Node today.

Note:
- That's enough about the past and how we made the choice.
- So how do we use Node today?
- Node backs our two main products and their supporting services:



<img class="logo half-size" src="./img/logo_fluencia.png" alt="Fluencia"
style="height: 50%; width: 50%">

* Fluencia: single page app with API.
* Cicero: text to speech service.
* Aurora: media transformation.

Note:
- Fluencia is an SPA for teaching Spanish to English speakers.
- It was a brand new project in the summer of 2012 when I started with the
  company.
- Now it has more than 150K users.
- It has some supporting services also built with Node.



<img class="logo half-size" src="./img/logo_fluencia.png" alt="Fluencia"
style="height: 50%; width: 50%">

* AWS
* MongoDB
* Node.js
* Express

* Require
* Backbone
* Jade + LESS
* Travis

Note:
- Fluencia's stack.



<img class="logo half-size" src="./img/logo_fluencia.png" alt="Fluencia"
style="height: 50%; width: 50%">

### About 8K LOC shared
### between client and server.

- a/b experiments
- access control
- constants
- native language support (nls)
- validation

Note:
- A noteable thing about Fluencia is the shared code.
- Fluencia has about 8K LOC shared between client and server:
- Literally common code between front-end and back-end.
- Shared code makes life easier.
- Certain things can be done exactly the same between client and server, such as (slide)



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">

* SpanishDict.com: website.
* Atalanta: data access layer.
* Spotcheck: lightweight S3 log querying.

Note:
- Our other main product is SpanishDict. 10M unique visitors/month.
- Traditional website.
- Also have several supporting services for it written in Node.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">

* AWS
* MySQL
* Node.js
* Express

* Browserify
* Travis

Note:
- SpanishDict's stack.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">
## Productivity.

- 700+ unit tests that run in seconds.
- 10 minute deploys, deploy at least once a day.
- Speed continues **not** to be a problem as we add new features.
- 2-3 boxes running each application, for redundancy, not load.

Note:
- Some evidence of how we're able to be productive with Node.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">

* Dirty secret: a few parts of our site are still powered by legacy PHP app.
* Node makes proxying easy:
  * `node-http-proxy` module.
  * Tweaked to inject updated header, footer, styles.

Note:
- A dirty secret: a few parts, < 1% of traffic, still powered by PHP.
- Very practical choice.
- We are a small shop. For a long time, 2 engineers, then 3, now we have a few more.
- We do cost/benefit analysis on everything we do.
- Complicated parts to reimplement. Why do it?
- An example of how Node allows you to implement things quickly and try new
  things out at a very low cost.



## Thriving
## in Nodeland.

Note:
- Now I'll talk about some of the practices we use to survive and thrive while
using Node.



## Challenges.

* Not always clear what are best practices.
  * npm: point of failure.
  * Error handling and recovery.
* Lots of modules to sort through.
* Bringing new developers up to speed.

Note:
- Let's be clear: Node is not perfect.
- Here are some of the challenges we've found.
- Node is young and changing quickly. Best practices are not always clear or
  even known.
- A couple examples. (slide)
- Is checking in node_modules a best practice? It solved our problem, but is it?
- Error handling recovery -- more about that in a moment.
- Node ecosystem is huge, and was (is) immature. For example, the original Mysql
  lib did not do connection pooling correctly. So we had to reimplement it
  ourselves. Price you pay.
- New developers are not always thinking asynchronously, though more and more
  they are!



### Care about ops.
- Thorough, informative logging.
- Resources maybe not a problem.
- Handle errors and uncaught exceptions.

Note:
- Logging brings visibility so you can figure out and solve problems. Several
  good libraries to help with this.
- Resources were less of a problem for us, anyway.
- Error handling and the notorious uncaught exception can cause downtime. Figure
  out what is acceptable to you and then figure out how to accomplish it. A little more...



### Towards 100% uptime.

- Had a problem.
- Looked for community resources.
- Read `cluster`, `child_process`, and `domain` module source.
- Developed a solution that works for us.

Note:
- We had a problem with occasional uncaught exceptions bringing down a whole
  worker process which was serving many users at once.
- It wasn't good enough that a dead worker would be replaced quickly, we needed
  it to gracefully exit, so that for example user question-answer events would
  not be lost.
- Dove into it and figured out an approach.



## Embrace the community.

* Follow leaders on Twitter, other channels.
* Hang out on #Node.js IRC.
* Meetups!
* We made our own meetup: Nova Node.

Note:
- The community is a huge resource, lots of smart people and good knowlege.



## Learn the ecosystem.

Note:
- Node core is small. Does much less out of the box than some things.
- Node ecosystem is very modular. Double-edged sword: more choices, more
  innovation but can be less clear what is best. Also, things might not be
  maintained.
- Node is still very new. Also double-edge sword: smaller pool of potential
  candidates, less experience with Node. But candidates eager to learn something
  new. Excitement.



## How to find modules.

- Favorite search engine
- Community / word of mouth
- What are your deps' deps?

Note:
- Finding modules is usually easy.



## How to choose modules.

There is no perfect way, but consider:

- Who created/maintains it?
- Who uses it?
- NPM last-published date?
- Recent activity?
- Open issues and PRs?
- Decent docs?
- etc.

Note:
- Choosing modules can be trickier.
- How to evaluate what is best? Here are some ideas.
- Can always contribute back to open source modules!



## Keep an eye on the future.

Note:
- We were monitoring the release of 0.10.
- Now we're looking at 0.11 to see what's coming in 0.12.
- 1.0 is not far off.



## How we learned
## and continue to learn
## Node.js.



## Build something!

Note:
- Can only really learn by doing.
- Build something. Anything.
- My first big assignment was to make a server to proxy TTS requests to the
  command-line based, definitely not-internet friendly enterprise software we'd
  licensed to generate the actual tts audio.
- Great project to learn how to structure an Express application, learn about
  streams and piping, and about communicating with child processes.



## Read all the docs.

Note:
- Core is small. The docs are not that big. You can do it.
- Much easier than with some other mature languages.
- You will learn something. Probably lots of things.
- They could still be improved, though.



## Give a talk.

Note:
- Pick something, anything that you want to learn about.
- No greater motivation to learn than putting yourself in the spotlight. It
helps that the community, especially here in DC in my experience, is friendly,
welcoming, supportive, fun.



## Onboarding.

* Small new tickets.
* Point new devs in right direction.
* Pair programming.
* Code review.
* Encourage personal projects.
* Encourage community involvement.

Note:
- Onboarding is great fun! Watching someone appreciate the power at their fingertips.
- We are growing. Went from 2 FT engineers when I started to 5 + interns, and
  actively hiring.



### [engineering.fluencia.com](http://engineering.fluencia.com)
### [fluencia.com/about-us/careers](http://www.fluencia.com/about-us/careers/)
### [@williamjohnbert](http://www.twitter.com/williamjohnbert)

Note:
- So that is how we leverage Node.js to deliver value to our users as fast as
  possible at Fluencia.
- Read our engineering blog to learn more.
- If what we do sounded interesting, check out our careers page.
- Thanks for listening!
