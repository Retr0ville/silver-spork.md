---
title: Best Practices for Scaling Your Node
tags: android blog rtrvl
author: retr0ville
source: https://www.freecodecamp.org/news/nodejs-api-best-practices-for-scaling/
---
Best Practices for Scaling Your Node.js REST APIs  
Search Submit your search query  
[![freeCodeCamp.org](https://cdn.freecodecamp.org/platform/universal/fcc_primary.svg)](https://www.freecodecamp.org/news)  
[Forum](https://forum.freecodecamp.org/) [Donate](https://www.freecodecamp.org/donate/)
<br />

September 15, 2022 / #node.js

Best Practices for Scaling Your Node.js REST APIs
=================================================

![Rishabh Rawat](https://www.freecodecamp.org/news/content/images/size/w60/2022/08/profile.jpeg) Rishabh Rawat
![Best Practices for Scaling Your Node.js REST APIs](https://www.freecodecamp.org/news/content/images/size/w2000/2022/09/Node.js-Best-Practices-1.png)

There is more to scalability than using cluster mode. In this tutorial, we'll explore 10 ways you can make your Node.js API ready to scale.

When working on a project, we often get a few real nuggets here and there on how to do something in a better way. We get to learn retrospectively, and then we're fully prepared to apply it next time around.

But how often does that actually work out? I don't even remember what I did yesterday sometimes. So I wrote this article.

This is my attempt to document some of the best Node.js scalability practices that are not talked about as often.

You can adopt these practices at any stage in your Node.js project. It doesn't have to be a last-minute patch.

With that said, here's what we will cover in this article:

1. 🚦Use throttling
2. 🐢 Optimize your database queries
3. ䷪ Fail fast with circuit breaker
4. 🔍 Log your checkpoints
5. 🌠 Use Kafka over HTTP requests
6. 🪝 Look out for memory leaks
7. 🐇 Use caching
8. 🎏 Use connection pooling
9. 🕋 Seamless scale-ups
10. 💎 OpenAPI compliant documentation

Use Throttling
--------------

Throttling allows you to limit access to your services to prevent them from being overwhelmed by too many requests. It has some clear benefits -- you can safeguard your application whether it's a large burst of users or a [denial-of-service attack](https://en.wikipedia.org/wiki/Denial-of-service_attack).

The common place to implement a throttling mechanism is where the rate of input and output don't match. Particularly, when there is more inbound traffic than what a service can (or wants to) handle.

Let's understand with a visualization.
![throttling between services](https://www.freecodecamp.org/news/content/images/2022/09/throttling-nodejs-best-practices-nodejs.drawio--5-.png) Your application is throttling requests from News Feed Service

There's throttling at the first junction point between your application and the News Feed Service:

1. *News Feed Service (NFS)*subscribes to your application for sending notifications.
2. It sends 1000 requests to your application every second.
3. Your application only handles 500 requests/sec based on the billing plan NFS subscribed to.
4. Notifications are sent for the first 500 requests.

Now it is very important to note that all the requests by NFS that exceed the quota of 500 requests/sec should fail and have to be retried by the NFS.

**Why reject the extra requests when you can queue them?** There are a couple of reasons:

1. Accepting all the requests will cause your application to start accumulating them. It will become a single point of failure (by RAM/disk exhaustion) for all the clients subscribed to your application, including NFS.
2. You should not accept requests that are greater than the scope of the subscription plan of your clients (in this case, NFS).

For application level rate limiting, you can use [express-rate-limit](https://www.npmjs.com/package/express-rate-limit) middleware for your Express.js API. For network level throttling, you can find solutions like [WAF](https://aws.amazon.com/waf/).

If you are using a pub-sub mechanism, you can throttle your consumers or subscribers as well. For instance, you can choose to consume only limited bytes of data when consuming a Kafka topic by setting the [maxBytes option](https://kafka.js.org/docs/consuming#a-name-options-a-options).  
ADVERTISEMENT

Optimize Your Database Queries
------------------------------

There will be times when querying the database is the only choice. You might have not cached the data or it could be stale.

When that happens, make sure your database is prepared for it. Having enough RAM and disk IOPS is a good first step.

Secondly, optimize your queries as much as possible. For starters, here are a couple of things that will set you on the right path:

1. Try to use indexed fields when querying. Don't over-index your tables in hopes of the best performance. [Indexes have their cost](https://www.mongodb.com/blog/post/performance-best-practices-indexing#:~:text=Eliminate%20Unnecessary%20Indexes).
2. For deletes, stick to soft deletes. If permanent deletion is necessary, delay it. ([interesting story](https://httpie.io/blog/stardust))
3. When reading data, only fetch the required fields using projection. If possible, strip away the unnecessary metadata and methods (for example, Mongoose has [lean](https://mongoosejs.com/docs/tutorials/lean.html)).
4. Try to decouple database performance from the user experience. If CRUD on the database can happen in the background (that is, non-blocking), do it. Don't leave the user waiting.
5. Directly update the desired fields using update queries. Don't fetch the document, update the field, and save the whole document back to the database. It has network and database overhead.

ADVERTISEMENT

Fail Fast with a Circuit Breaker
--------------------------------

Imagine you get burst traffic on your Node.js application, and one of the external services required to fulfill the requests is down. Would you want to keep hitting the dead end for every request thereafter? Definitely Not. We don't want to waste time and resources on the requests destined to fail.

This is the whole idea of a circuit breaker. **Fail early.** **Fail fast**.

For example, if 50 out of 100 requests fail, it doesn't allow any more requests to that external service for the next X seconds. It prevents firing requests that are bound to fail.

Once the circuit resets, it allows requests to go through. If they fail again, the circuit breaks and the cycle repeats.
![Node.js Opposum circuit breaker states](https://www.freecodecamp.org/news/content/images/2022/09/circuit-breaker-nodejs-best-practices-for-scale.drawio--1-.png) Node.js Opposum circuit breaker states

To learn more about how to add a circuit breaker to your Node.js application, check out [Opposum](https://github.com/nodeshift/opossum). You can read more on circuit breakers [here](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern).  
ADVERTISEMENT

Log Your Checkpoints
--------------------

A good logging setup allows you to spot errors quickly. You can create visualizations to understand your app's behavior, set up alerts, and debug efficiently.

You can check out the [ELK stack](https://www.elastic.co/what-is/elk-stack) for setting up a good logging and alerting pipeline.

While logging is an essential tool, it is very easy to overdo it. If you start logging everything, you can end up exhausting your disk IOPS causing your application to suffer.

**As a good rule of thumb is to only log checkpoints.**

Checkpoints can be:

1. Requests, as they enter the main control flow in your application and after they are validated and sanitized.
2. Request and response when interacting with an external service/SDK/API.
3. The final response to that request.
4. Helpful error messages for your catch handlers (with sane defaults for error messages).

**PS:** If a request goes through multiple services during the lifecycle, you can pass along a unique ID in the logs to capture a particular request across all the services.  
ADVERTISEMENT

Use Kafka Over HTTP Requests
----------------------------

While HTTP has its use-cases, it is easy to overdo it. Avoid using HTTP requests where it is not necessary.

Let's understand this with the help of an example.
![Overview of Kafka pub-sub using topics](https://www.freecodecamp.org/news/content/images/2022/09/kafka-over-http-nodejs-best-practices-for-scale.drawio.png) Overview of Kafka pub-sub using topics

Let's say you are building a product like Amazon and there are two services:

1. Vendor service
2. Inventory service

Whenever you receive new stock from the vendor service, you push the stock details to a [Kafka](https://kafka.apache.org/intro) topic. The inventory service listens to that topic and updates the database acknowledging the fresh restock.

To note that, you push the new stock data into the pipeline and move on. It is consumed by the inventory service at its own pace. **Kafka allows you to decouple services.**

Now, what happens if your inventory service goes down? It is not straightforward with HTTP requests. Whereas in the case of Kafka, you can replay the intended messages (for example using [kcat](https://github.com/edenhill/kcat)). **With Kafka, you do not lose data after consumption.**

When an item comes back in stock, you might want to send out notifications to the users who wishlisted it. To do that, your notification service can listen to the same topic as the inventory service. This way, **a single message bus is consumed at various places without** **HTTP overhead**.

The [Getting Started page](https://kafka.js.org/docs/getting-started) of KafkaJS shares the exact snippet to get you started with a basic setup in your Node.js application. I'd highly recommend checking it out, as there's a lot to explore.  
ADVERTISEMENT

Look Out for Memory Leaks
-------------------------

If you don't write memory-safe code and don't [profile](https://nodejs.org/en/docs/guides/simple-profiling/) your application often, you may end up with a crashed server.

You do not want your profiling results to look like this:
![setTimeout retaining 98% memory after execution is over](https://www.freecodecamp.org/news/content/images/2022/09/Image-Pasted-at-2022-9-6-14-58.png) setTimeout retaining 98% memory after execution is over

For starters, I would recommend the following:

1. Run your Node.js API with the `--inspect` flag.
2. Open `chrome://inspect/#devices` in your Chrome browser.
3. Click inspect \> `Memory` tab \> `Allocation instrumentation on timeline`.
4. Perform some operations on your app. You can use apache bench on macOS to fire off multiple requests. Run `curl cheat.sh/ab` in your terminal to learn how to use it.
5. Stop the recording and analyze the memory retainers.

If you find any large blocks of retained memory, try to minimize it. There are a lot of resources on this topic. Start by googling "how to prevent memory leaks in Node.js".

Profiling your Node.js application and looking for memory utilization patterns should be regular practice. Let's make "Profiling Driven Refactor" (PDR) a thing?  
ADVERTISEMENT

Use Caching to Prevent Excessive Database Lookup
------------------------------------------------

The goal is to not hit the database for every request your application gets. Storing the results in cache decreases the load on your database and boosts performance.

There are two strategies when working with caching.

**Write through**caching makes sure the data is inserted into the database and the cache when a write operation happens. This keeps the cache relevant and leads to better performance. Downsides? Expensive cache as you store infrequently used data to the cache as well.

Whereas in **Lazy loading**, the data is only written to the cache when it is first read. The first request serves the data from the database but the consequent requests use the cache. It has a smaller cost but increased response time for the first request.

To decide the TTL (or Time To Live) for the cached data, ask yourself:

1. How often the underlying data changes?
2. What is the risk of returning outdated data to the end user?

If it is okay, **having more TTL will help you with a better performance**.

Importantly, **add a slight delta to your TTLs**. If your application receives a large burst of traffic and all of your cached data expires at once, it can lead to unbearable load on the database, affecting user experience.

    final TTL = estimated value of TTL + small random delta

calculation of TTL

There are a number of policies to perform [cache eviction](https://redis.io/docs/manual/eviction/). But leaving it on default settings is a valid and accepted approach.  
ADVERTISEMENT

Use Connection Pooling
----------------------

Opening a standalone connection to the database is costly. It involves TCP handshake, SSL, authentication and authorization checks, and so on.

Instead, you can leverage connection pooling.
![Database connection pool](https://www.freecodecamp.org/news/content/images/2022/09/conection-pooling-nodejs-best-practices-for-scale.drawio--1-.png) Database connection pool

A connection pool holds multiple connections at any given time. Whenever you need it, the pool manager assigns any available/idle connection. You get to skip the cold start phase of a brand new connection.

Why not max out the number of connections in the pool, then? Because it highly depends on your hardware resources. If you ignore it, performance can take a massive toll.

The more the connections, the less RAM each connection has, and the slower the queries that leverage RAM (for example sort). The same principle applies to your disk and CPU. With every new connection, you are spreading your resources thin across the connections.

You can tweak the number of connections till it matches your needs. For starters, you can get an estimate on the size you need from [here](https://www.cybertec-postgresql.com/en/tuning-max_connections-in-postgresql/).

Read about the MongoDB connection pool [here](https://www.mongodb.com/docs/manual/administration/connection-pool-overview/). For PostgreSQL, you can use the `node-postgres` package. It has built-in support for [connection pooling](https://node-postgres.com/features/pooling).  
ADVERTISEMENT

Seamless Scale-ups
------------------

When your application's user base is starting to grow and you have already hit the ceiling on vertical scaling, what do you do? You scale horizontally.
> Vertical scaling means increasing the resources of a node (CPU, memory, etc.) whereas horizontal scaling involves adding more nodes to balance out the load on each node.

If you're using AWS, you can leverage Automatic Scaling Groups (ASG) which horizontally scales the number of servers based on a predefined rule (for example when CPU utilization is more than 50%).

You can even pre-schedule the scale up and scale down using [scheduled actions](https://docs.aws.amazon.com/autoscaling/application/userguide/examples-scheduled-actions.html) in case of predictable traffic patterns (for example during the World Cup finals for a streaming service).

Once you have your ASG in place, adding a load balancer in front will make sure the traffic is routed to all the instances based on a chosen strategy (like [round robin](https://en.wikipedia.org/wiki/Round-robin_scheduling), for example).
![Load balancing multiple targets based on predefined rules](https://www.freecodecamp.org/news/content/images/2022/09/alb-nodejs-best-practices-for-scale.drawio--2-.png) Load balancing multiple targets based on predefined rules

**PS:**It is always a good idea to estimate the requests your single server can handle (CPU, memory, disk, and so on) and allocate at least 30% more.  
ADVERTISEMENT

OpenAPI Compliant Documentation
-------------------------------

It might not directly affect your ability to scale a Node.js application, but I had to include this in the list. If you've ever done an API integration, you know it.

It is crucial to know everything about the API before you take a single step forward. It makes it easy to integrate, iterate, and reason about the design. Not to mention the gains in the speed of development.

Make sure to **create OpenAPI Specification (OAS) for your Node.js API**.

It allows you to create API documentation in an industry-standard manner. It acts as a single source of truth. When defined properly, it makes interacting with the API much more productive.

I have created and published a sample API documentation [here](https://app.swaggerhub.com/apis/Rishabh570/test-API/0.1). You can even inspect any API using the [swagger inspector](https://swagger.io/tools/swagger-inspector/).

You can find all of your API documentations and create new ones from the [Swagger Hub dashboard](https://app.swaggerhub.com/home).  
ADVERTISEMENT

Now you go, captain!
--------------------

We have looked at ten lesser-known best practices to prepare Node.js for scale and how you can take your first steps with each one of them.

Now it is your turn to go through the checklist and explore the ones you find lacking in your Node.js application.  

Grab your checklist ✨

I hope you found this helpful and it gave you some pointers to move forward in your scalability endeavor. This is not an exhaustive list of all the best practices -- I have just included the ones I found are not talked about as much based on my experience.

Feel free to reach out on [Twitter](https://twitter.com/Rishabh570). I'd love to hear your feedback and suggestions on other best practices that you are using.

Liked the article? [Get the improvement pills on backend web development](https://buttondown.email/rishabh570) 💌.  
![Rishabh Rawat](https://www.freecodecamp.org/news/content/images/size/w60/2022/08/profile.jpeg) Rishabh Rawat

Software Engineer

If you read this far, tweet to the author to show them you care. Tweet a thanks  
Learn to code for free. freeCodeCamp's open source curriculum has helped more than 40,000 people get jobs as developers. [Get started](https://www.freecodecamp.org/learn/)  
ADVERTISEMENT  
freeCodeCamp is a donor-supported tax-exempt 501(c)(3) nonprofit organization (United States Federal Tax Identification Number: 82-0779546)

Our mission: to help people learn to code for free. We accomplish this by creating thousands of videos, articles, and interactive coding lessons - all freely available to the public. We also have thousands of freeCodeCamp study groups around the world.

Donations to freeCodeCamp go toward our education initiatives, and help pay for servers, services, and staff.

You can [make a tax-deductible donation here](https://www.freecodecamp.org/donate/).  
Trending Guides  
[Python Parse JSON](https://www.freecodecamp.org/news/python-parse-json-how-to-read-a-json-file/) [HTML Cheat Sheet](https://www.freecodecamp.org/news/html-cheat-sheet-html-elements-list-reference/) [ROW_NUMBER in SQL](https://www.freecodecamp.org/news/row_number-in-sql-select-top-example-in-sql-and-sql-server2/) [HTML Center Image](https://www.freecodecamp.org/news/html-center-image-css-align-img-center-example/) [JavaScript Replace](https://www.freecodecamp.org/news/javascript-replace-how-to-use-the-string-prototype-replace-method-js-example/) [HTML HR Tag Example](https://www.freecodecamp.org/news/html-horizontal-line-hr-tag-example/) [JavaScript UpperCase](https://www.freecodecamp.org/news/javascript-uppercase-how-to-capitalize-a-string-in-js-with-touppercase/) [Ordered List in HTML](https://www.freecodecamp.org/news/ordered-list-in-html-ol-tag-example/) [Screenshot on Windows](https://www.freecodecamp.org/news/how-to-screenshot-on-windows-take-a-screen-shot-on-pc/) [Sort an Array in Java](https://www.freecodecamp.org/news/java-sort-array-how-to-reverse-an-array-in-ascending-or-descending-order-with-arrays-sort-2/)  
[HTML Video](https://www.freecodecamp.org/news/html-video-how-to-embed-a-video-player-with-the-html-5-video-tag/) [CSS Overflow](https://www.freecodecamp.org/news/css-overflow-visible-scroll-auto-hidden/) [What is REST?](https://www.freecodecamp.org/news/what-is-rest-rest-api-definition-for-beginners/) [VGA No Signal](https://www.freecodecamp.org/news/vga-no-signal-how-to-fix-a-monitor-connection-on-windows-10-pc/) [CSS Text Align](https://www.freecodecamp.org/news/css-text-align-centered-justified-right-aligned-text-style-example/) [HTML Label Tag](https://www.freecodecamp.org/news/html-label-label-tag-example/) [CSS Button Style](https://www.freecodecamp.org/news/css-button-style-hover-color-and-background/) [For Loop in Java](https://www.freecodecamp.org/news/for-loop-in-java-foreach-loop-syntax-example/) [Linux cp Command](https://www.freecodecamp.org/news/the-linux-cp-command-how-to-copy-files-in-linux/) [Link CSS to HTML](https://www.freecodecamp.org/news/how-to-link-css-to-html/)  
[Cast a Function in SQL](https://www.freecodecamp.org/news/cast-a-function-in-sql-convert-char-to-int-sql-server-example/) [Java Logical Operators](https://www.freecodecamp.org/news/java-operator-and-or-logical-operators/) [Chmod Command in Linux](https://www.freecodecamp.org/news/how-to-change-file-permissions-with-the-chmod-command-on-linux/) [Python Get Last Element](https://www.freecodecamp.org/news/python-get-last-element-in-list-how-to-select-the-last-item/) [Python Add to Dictionary](https://www.freecodecamp.org/news/python-add-to-dictionary-adding-an-item-to-a-dict/)  
[Declare an Array in Java](https://www.freecodecamp.org/news/java-array-how-to-declare-and-initialize-an-array-in-java-example/) [Get Current Time in Python](https://www.freecodecamp.org/news/python-get-current-time/) [Change Div Background Color](https://www.freecodecamp.org/news/div-background-color-how-to-change-background-color-in-css/) [Get Variable Type in Python](https://www.freecodecamp.org/news/python-print-type-of-variable-how-to-get-var-type/) [Logical Operators in Python](https://www.freecodecamp.org/news/operators-in-python-how-to-use-logical-operators-in-python/)  
Our Nonprofit  
[About](https://www.freecodecamp.org/news/about/) [Alumni Network](https://www.linkedin.com/school/free-code-camp/people/) [Open Source](https://github.com/freeCodeCamp/) [Shop](https://www.freecodecamp.org/news/shop/) [Support](https://www.freecodecamp.org/news/support/) [Sponsors](https://www.freecodecamp.org/news/sponsors/) [Academic Honesty](https://www.freecodecamp.org/news/academic-honesty-policy/) [Code of Conduct](https://www.freecodecamp.org/news/code-of-conduct/) [Privacy Policy](https://www.freecodecamp.org/news/privacy-policy/) [Terms of Service](https://www.freecodecamp.org/news/terms-of-service/) [Copyright Policy](https://www.freecodecamp.org/news/copyright-policy/)
