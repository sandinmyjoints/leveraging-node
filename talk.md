# Leveraging Node.js
at Fluencia

Note:
Aprovechando Node.js



### 2011: the situation.

* Have a fast-growing website that cannot go down or slow down, ever.
* Want to build a brand new SPA that people will pay you money to use.
* Do it with two or three engineers. ASAP.

Note:
- I want to start by briefly turning back the clock to late 2011.
- Put yourself in the shoes of the CEO of a small (like 3 employees) but growing
  company.
- (slides)



## What are you going to
## build the future on?

Note:
- This is the question the company was asking itself.
- The existing PHP codebase was showing its age.
- Engineering team at the time (such as it was, really the CEO and a new
  director of engineering) was very aware of PHP's limitations as a language,
  community, etc..
- Where to go in the future?



<img class="logo" src="./img/logo_node.png" alt="Node.js">

Note:
- Big surprise.
- So this company, Fluencia, went with Node, for reasons that I will talk about.
- But first, a little background.



<img class="logo" src="./img/logo_fluencia.png" alt="Fluencia">

Note:
- I'm William Bert. Senior Software Engineer at Fluencia. I've been here since 2012.
- What is Fluencia? Best way to learn Spanish online. Subscription. Over 100K
  users.
- We also run a reference site called SpanishDict. That's the high-traffic site.
  It used to be the company of the company, but we like Fluencia better.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict">

Note:
- SpanishDict gets around 10 million unique visitors a month.
- Top result if you google "Spanish".
- Both of these applications are backed by Node.
- Why? How did it come to be? Some of this was before my time, but I have it on
  good authority from some of the people who were there...



### Wanted:

## Speed / scalability
## Community
## Productivity

Note:
- Speed/scalability:
- Google has made huge investment in making V8 fast.
- No threads, very lightweight, very scalable.
- Community:
- Big community and growing.
- Lots of libraries already, more being released all the time.
- Productivity:
- I think in 2011, choosing Node when thinking about productivity was a bold
  choice.
- Node does async throughout, unlike other languages where it is bolted on, and
  not all libs support it.
- It is changing quickly, but it is stable enough.
- The core is small. The philosophy is for small modules that can be pieced
  together. Simplicity.


## Always bet on Javascript.

Note:
- Common code between front-end and back-end. Lessons learned in one can often
  be applied to other. Reduced cost of context switching. Shared code makes
  validation easier.
- The future (for us) included an SPA. Would need to do heavy lifting in
  Javascript. Full stack JS benefits.
- So this stack just makes sense.



## How we use Node.

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



<img class="logo half-size" src="./img/logo_fluencia.png" alt="Fluencia"
style="height: 50%; width: 50%">

* AWS
* MongoDB / Mongoose
* Node
* Express
* Require
* Backbone
* Jade + LESS + Handlebars
* Travis



<img class="logo half-size" src="./img/logo_fluencia.png" alt="Fluencia"
style="height: 50%; width: 50%">
## Shared code

About 8K LOC shared between client and server:

- a/b experiments
- access control
- constants
- native language support (nls) dictionary
- validation

Note:
- A noteable thing about Fluencia is the shared code.
- Fluencia has about 8K LOC shared between client and server:
- Literally common code between front-end and back-end.
- Shared code makes life easier.
- Lessons learned in one place can often be applied to other.
- Reduced cost of context switching.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">

* SpanishDict.com: website.
* Atalanta: data access layer.
* Spotcheck: lightweight S3 log querying.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">

* AWS
* MySQL
* Node
* Express
* Browserify
* Travis



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">
## Productivity

- 700+ unit tests that run in seconds.
- 10 minute deploys, deploy once a day.
- Speed continues **not** to be a problem.
- 2-3 boxes running each application, for redundancy, not load.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">
## Proxying

Dirty secret: a few parts of our site are still powered by legacy PHP app.

Node makes proxying easy.

* `node-http-proxy`
* Tweak as needed to reframe contents using new header, styles

Note:
- Very practical choice.
- We are a small shop. 2 engineers, then 3, for a long time.
- We do cost/benefit analysis on everything we do.



<img class="logo" src="./img/logo_sd.png" alt="SpanishDict" style="height: 50%;
width: 50%">
<img class="logo" src="./img/routing.svg" alt="SpanishDict routing">



## Thriving
## in Nodeland



## Challenges

* Figuring out uptime, error handling and recovery.
* Experimental / unstable parts.
* Bringing developers up to speed.
* Things change fast.
* Not clear what are best practices.
* Lots of modules to sort through.
* npm point of failure.

Note:
- Let's be clear: Node is not perfect.
- Here are some of the challenges we've found.
- Node ecosystem was (is) immature. Original Mysql lib did not do connection
  pooling correctly.



### Care about ops
- Thorough, informative logging
- Handle errors and uncaught exceptions (understand the difference!)
- Resources probably less of a problem

Note:
- Resources were less of a problem for us, anyway.



## Towards 100% Uptime

- Reading cluster, domain, and child_process modules helped somewhat.
- Though they are marked as experimental and unstable.



## Check in `node_modules`

Eliminate npm as a point of failure.

Note:
- There are ways around the annoyances of checking in libs.
- Do `npm rebuild` on deploy.



## Embrace the Community

* Hang out on #Node.js IRC.
* Follow leaders on Twitter, other channels.
* Meetups are great!
* We made our own meetup: Nova Node.



## Learn the ecosystem.

Note:
- Node ecosystem is very modular. Double-edged sword: more choices, more
  innovation. Less clear what is best. Things might not be maintained.
- Node core is less opinionated.
- Node is cutting-edge. Cuts both ways: smaller pool of potential candidates,
  less experience with Node. But candidates who eager to learn something new.
  Excitement.



## How to choose libs

There is no perfect way.

- Who created it
- Who maintains it
- Who uses it
- NPM last-published date
- Recent activity
- Github stars / open issues / open PRs
- Quality of documentation
- etc.


## How to find modules

- Community
- Word of mouth
- Blog
- RSS
- Twitter



## Keep an eye on the future.

Note:
- We were monitoring the release of 0.10.
- Now we're looking at 0.11 to see what's coming in 0.12.
- 1.0 is not far off.



## How we learned
## and continue to learn
## Node



## Onboarding

* Small new tickets
* Point them in right direction
* Share patterns,
* Pair programming
* Code review.
* Be active in community.
* Has anyone used nodeschool?

Note:
- We are growing. Went from 3 FT engineers to 5 + interns, and actively hiring.
- Onboarding is a big concern.
- doing personal projects,
- Googling solution and subscribe to RSS feed to read
- interesting articles are my ways of learning Node



## Build something!

Note:
- Can only really learn by doing.
- Build something. Anything.
- My first big assignment was to make a server to proxy tts requests to our tts
  software.


## Read all the docs.

Note:
- Core is small. The docs are not that big. You can do it.
- Much easier than with some other mature languages.
- You will learn something. Probably lots of things.
- They could still be improved, though.



## Give a talk.

Note:
- Pick something, anything that you want to learn about.
- No better way to learn than putting yourself in the spotlight. It helps that
the community here is friendly, welcoming, supportive, fun.



## [engineering.fluencia.com](http://engineering.fluencia.com)
## [fluencia.com/about-us/careers](http://www.fluencia.com/about-us/careers/)
## [@williamjohnbert](http://www.twitter.com/williamjohnbert)

Note:
- Read our engineering blog to learn more.
- If this sounded interesting, check out our careers page.
