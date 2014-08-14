# Leveraging Node.js
at Fluencia

Note:
Aprovechando Node.js



<img class="logo" src="./img/logo_fluencia.png" alt="Fluencia">

Note:
- I'm William Bert. Senior Software Engineer at Fluencia. I've been here since 2012.
- What is Fluencia? Best way to learn Spanish online. Subscription. Over 100K users.
- We also run a reference site called SpanishDict.


<img class="logo" src="./img/logo_sd.png" alt="SpanishDict">

Note:
- SpanishDict gets around 10 million unique visitors a month.
- Top result if you google "Spanish".
- Both of these applications are backed by Node.
- Why? How did it come to be? Here's the story. Some of this was before my time,
  but I have it on good authority from some of the people who were there...


## (2011)

www.spanishdict.com is running PHP.

Running fine. Serving lots of traffic.

But... <!-- .element: class="fragment" data-fragment-index="1" -->

Is PHP the future? <!-- .element: class="fragment" data-fragment-index="1" -->

Note:
- Engineering team at the time (such as it was, really the CEO) was aware of
  PHP's limitations as a language.
- PHP community was not so great.
- Where to go in the future?
- Is PHP the future? Conclusion: not for us.



# What <em>is</em> the future?

## Ruby? <!-- .element: class="fragment" data-fragment-index="1" -->
## Python? <!-- .element: class="fragment" data-fragment-index="1" -->
## Node?? <!-- .element: class="fragment" data-fragment-index="2" -->

Note:
- Future is vague. Let's get concrete.
- I won't go through comparing the languages or choices, but here was the
  thinking about Node.


# Considerations
* Speed
* Stable (enough)
* Growing community
* Improving quickly
* Same language on server and client

Note:
* Google has made huge investment in making V8 fast.
* Node does async throughout, unlike other languages where it is bolted on, and
  not all libs support it.
* Node ecosystem is more modular. Double-edged sword: more choices, more
  innovation. Less clear what is best. Things might not be maintained.
* Node core is less opinionated.
* Node ecosystem was (is) immature. Original Mysql lib did not do connection
  pooling correctly.
* Node is cutting-edge. Cuts both ways: smaller pool of potential candidates,
  less experience with Node. But candidates who eager to learn something new.
  Excitement.
* Always bet on Javascript. Stack just makes sense.
* Common code between front-end and back-end. Lessons learned in one can often
  be applied to other. Reduced cost of context switching. Shared code makes
  validation easier.
* The future (for us) included an SPA. Would need to do heavy lifting in
  Javascript. Full stack JS benefits.



# How we use Node

* We are a small shop. 2 engineers, then 3, now a few more.
* Backs our two main products and their supporting services:
    * SpanishDict.com (~10M uniques per month) -- website
    * Atalanta -- Data access layer for spanishdict.com
    * Fluencia: (150K users) -- SPA with api
    * Cicero -- text to speech service
    * Aurora -- media transformation
    * Spotcheck -- Lightweight S3 log querying

TODO: Look at Chris's draft blog post

TODO: Grab logos


# Fluencia stack

* AWS
* MongoDB / Mongoose
* Node
* Express
* Require
* Backbone
* Jade + LESS + Handlebars
* Travis


# SpanishDict stack

* AWS
* MySQL
* Node
* Express
* Browserify
* Travis


# Shared code

Fluencia

src
client
server
shared

About 8K LOC

* access control
* constants
* a/b experiments
* Native Language Support (nls) dictionary
* validation


# Benefits

* Speed
* Lots of people know Javascript
* Lots of improvements



# Challenges

* Figuring out uptime, error handling and recovery
* Still experimental / unstable parts
* Bringing developers up to speed, learning async
* Lots of changes, not always clear what are best practices
* Lots of modules to sort through
* NPM point of failure


# Other: how work with core, adoption, knowledge sharing, onboarding

* We made nova node
* tracking issues?
* bugs?
* feature requests?
* doc updates
* looking at node 11 to see what's coming


marketing and efforts around Node

* -> cross-promote
* -> use case for Node

Communicate to audience that they should be caring about logging

They should handle errors, uncaught exceptions

Manage that deployment, how to debug, how to keep it up

Benefits that we're seeing, high-level reasons for selecting Node. Scalability,
stability, speed.

Where we started, where we are today.


## Onboarding

* small new tickets
* point them in right direction
* give examples,
* share patterns,
* pair programming
* code review.
* Be active in community.
* Has anyone used nodeschool? Read the docs.

doing personal projects, Googling solution and subscribe to RSS feed to read
interesting articles are my ways of learning Node

## Patterns

- No promises
- `async` lib.

- No generators or other ES6 features
- Small testable CoffeeScript "classes"


- we use coffeescript



# How to choose libs

## No perfect way.

- Who created it
- Who maintains it
- Who uses it
- NPM last-published date
- Recent activity
- Github stars / open issues / open PRs
- Quality of documentation
- etc.


# How to find modules

- Community
- Word of mouth
- Blog
- RSS
- Twitter



# How to learn Node


# Build something


Note:
Can only learn by doing.


# Read all the docs

Note:
You will learn something. They could still be improved, though.


# Give a talk

Note:
Pick something, anything that you want to learn about.
No better way to learn than putting yourself in the spotlight. It helps that the
community here is friendly, welcoming, supportive, fun.



# Some things we do with Node


# Towards 100% Uptime

- Experimental, unstable.
- Reading core cluster and child_process modules helped somewhat.

# Proxying rw


TODO network topology graph

engineering.fluencia.com
http://www.fluencia.com/about-us/careers/

node-http-proxy



# Productivity

- many 100s of unit tests that run in seconds (SpanishDict) or minutes
  (Fluencia)
- 10 minute deploys, deploy once a day
- Speed continues not to be a problem
- 2-3 boxes running each application, mostly for redundancy, not load
