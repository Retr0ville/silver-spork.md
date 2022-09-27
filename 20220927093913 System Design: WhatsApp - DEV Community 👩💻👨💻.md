---
title: System Design: WhatsApp - DEV Community 👩💻👨💻
tags: android blog rtrvl
author: retr0ville
source: https://dev.to/karanpratapsingh/system-design-whatsapp-fld
---
System Design: WhatsApp - DEV Community 👩💻👨💻  
Skip to content  
Navigation menu ![DEV Community 👩‍💻👨‍💻](https://dev-to-uploads.s3.amazonaws.com/uploads/logos/resized_logo_UQww2soKuUsjaOGNB38o.png)  
Search  
Search  
Log in Create account  

DEV Community 👩‍💻👨‍💻
------------------------

Close  

DEV Community 👩‍💻👨‍💻 is a community of 914,438 amazing developers
---------------------------------------------------------------------

We're a place where coders share, stay up-to-date and grow their careers.  
Create account Log in

* Home
* Listings
* Podcasts
* Videos
* Tags
* FAQ
* [Forem Shop](https://shop.forem.com)
* Sponsors
* About
* Contact
* Guides
* image/svg+xml Software comparisons

Other
-----

* Code of Conduct
* Privacy Policy
* Terms of use

[Twitter](https://twitter.com/thepracticaldev) [Facebook](https://facebook.com/thepracticaldev) [Github](https://github.com/forem) [Instagram](https://instagram.com/thepracticaldev) [Twitch](https://twitch.com/thepracticaldev)  
Like Unicorn Save  
More...  
Copy link Copy link  
Copied to Clipboard  
[Share to Twitter](https://twitter.com/intent/tweet?text=%22System%20Design%3A%20WhatsApp%22%20by%20%40karan_6864%20%23DEVCommunity%20https%3A%2F%2Fdev.to%2Fkaranpratapsingh%2Fsystem-design-whatsapp-fld) [Share to LinkedIn](https://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fdev.to%2Fkaranpratapsingh%2Fsystem-design-whatsapp-fld&title=System%20Design%3A%20WhatsApp&summary=Let%27s%20design%20a%20Whatsapp%20like%20instant%20messaging%20service%2C%20similar%20to%20services%20like%20Whatsapp%2C%20Facebook...&source=DEV%20Community%20%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB%F0%9F%91%A8%E2%80%8D%F0%9F%92%BB) [Share to Reddit](https://www.reddit.com/submit?url=https%3A%2F%2Fdev.to%2Fkaranpratapsingh%2Fsystem-design-whatsapp-fld&title=System%20Design%3A%20WhatsApp) [Share to Hacker News](https://news.ycombinator.com/submitlink?u=https%3A%2F%2Fdev.to%2Fkaranpratapsingh%2Fsystem-design-whatsapp-fld&t=System%20Design%3A%20WhatsApp) [Share to Facebook](https://www.facebook.com/sharer.php?u=https%3A%2F%2Fdev.to%2Fkaranpratapsingh%2Fsystem-design-whatsapp-fld)
Share Post via... Report Abuse  
![Cover image for System Design: WhatsApp](https://res.cloudinary.com/practicaldev/image/fetch/s--_TxEvRiR--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/banner.png)  
![Karan Pratap Singh](https://res.cloudinary.com/practicaldev/image/fetch/s--7GrdBPf3--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/350819/b3e261fa-d88e-4cb4-80a2-233ab491af4e.jpg)  
Karan Pratap Singh

Posted on Sep 21 • Originally published at [github.com](https://github.com/karanpratapsingh/system-design#whatsapp)

System Design: WhatsApp
=======================

#distributedsystems #architecture #tutorial  

System Design (57 Part Series)
------------------------------

1 System Design: The complete course 2 System Design: What is system design? ... 53 more parts... 3 System Design: IP 4 System Design: OSI Model 5 System Design: TCP and UDP 6 System Design: Domain Name System (DNS) 7 System Design: Load Balancing 8 System Design: Clustering 9 System Design: Caching 10 System Design: Content Delivery Network (CDN) 11 System Design: Proxy 12 System Design: Availability 13 System Design: Scalability 14 System Design: Storage 15 System Design: Databases and DBMS 16 System Design: SQL databases 17 System Design: NoSQL databases 18 System Design: SQL vs NoSQL databases 19 System Design: Database Replication 20 System Design: Indexes 21 System Design: Normalization and Denormalization 22 System Design: ACID and BASE consistency models 23 System Design: CAP theorem 24 System Design: PACELC Theorem 25 System Design: Transactions 26 System Design: Distributed Transactions 27 System Design: Sharding 28 System Design: Consistent Hashing 29 System Design: Database Federation 30 System Design: N-tier architecture 31 System Design: Message Brokers 32 System Design: Message Queues 33 System Design: Publish-Subscribe 34 System Design: Enterprise Service Bus (ESB) 35 System Design: Monoliths and Microservices 36 System Design: Event-Driven Architecture (EDA) 37 System Design: Event Sourcing 38 System Design: Command and Query Responsibility Segregation (CQRS) 39 System Design: API Gateway 40 System Design: REST, GraphQL, gRPC 41 System Design: Long polling, WebSockets, Server-Sent Events (SSE) 42 System Design: Geohashing and Quadtrees 43 System Design: Circuit breaker 44 System Design: Rate Limiting 45 System Design: Service Discovery 46 System Design: SLA, SLO, SLI 47 System Design: Disaster recovery 48 System Design: Virtual Machines (VMs) and Containers 49 System Design: OAuth 2.0 and OpenID Connect (OIDC) 50 System Design: Single Sign-On (SSO) 51 System Design: SSL, TLS, mTLS 52 System Design: System Design Interviews 53 System Design: URL Shortener 54 System Design: WhatsApp 55 System Design: Twitter 56 System Design: Netflix 57 System Design: Uber  
Let's design a [Whatsapp](https://whatsapp.com) like instant messaging service, similar to services like [Whatsapp](https://www.whatsapp.com), [Facebook Messenger](https://www.messenger.com), and [WeChat](https://www.wechat.com).

What is Whatsapp?
-----------------

Whatsapp is a chat application that provides instant messaging services to its users. It is one of the most used mobile applications on the planet connecting over 2 billion users in 180+ countries. Whatsapp is also available on the web.

Requirements
------------

Our system should meet the following requirements:

### Functional requirements

* Should support one-on-one chat.
* Group chats (max 100 people).
* Should support file sharing (image, video, etc.).

### Non-functional requirements

* High availability with minimal latency.
* The system should be scalable and efficient.

### Extended requirements

* Sent, Delivered, and Read receipts of the messages.
* Show the last seen time of users.
* Push notifications.

Estimation and Constraints
--------------------------

Let's start with the estimation and constraints.

*Note: Make sure to check any scale or traffic-related assumptions with your interviewer.*

### Traffic

Let us assume we have 50 million daily active users (DAU) and on average each user sends at least 10 messages to 4 different people every day. This gives us 2 billion messages per day.

50 m i l l i o n × 20 m e s s a g e s = 2 b i l l i o n / d a y 50 \\space million \\times 20 \\space messages = 2 \\space billion/day 50 million×20 messages=2 billion/day
Messages can also contain media such as images, videos, or other files. We can assume that 5 percent of messages are media files shared by the users, which gives us additional 200 million files we would need to store.  
5 p e r c e n t × 2 b i l l i o n = 200 m i l l i o n / d a y 5 \\space percent \\times 2 \\space billion = 200 \\space million/day 5 percent×2 billion=200 million/day
**What would be Requests Per Second (RPS) for our system?**

2 billion requests per day translate into 24K requests per second.  
2 b i l l i o n ( 24 h r s × 3600 s e c o n d s ) = ∼ 24 K r e q u e s t s / s e c o n d \\frac{2 \\space billion}{(24 \\space hrs \\times 3600 \\space seconds)} = \\sim 24K \\space requests/second (24 hrs×3600 seconds)2 billion=∼24K requests/second
### Storage

If we assume each message on average is 100 bytes, we will require about 200 GB of database storage every day.  
2 b i l l i o n × 100 b y t e s = ∼ 200 G B / d a y 2 \\space billion \\times 100 \\space bytes = \\sim 200 \\space GB/day 2 billion×100 bytes=∼200 GB/day
As per our requirements, we also know that around 5 percent of our daily messages (100 million) are media files. If we assume each file is 50 KB on average, we will require 10 TB of storage every day.  
100 m i l l i o n × 100 K B = 10 T B / d a y 100 \\space million \\times 100 \\space KB = 10 \\space TB/day 100 million×100 KB=10 TB/day
And for 10 years, we will require about 38 PB of storage.  
( 10 T B + 0.2 T B ) × 10 y e a r s × 365 d a y s = ∼ 38 P B (10 \\space TB + 0.2 \\space TB) \\times 10 \\space years \\times 365 \\space days = \\sim 38 \\space PB (10 TB+0.2 TB)×10 years×365 days=∼38 PB
### Bandwidth

As our system is handling 10.2 TB of ingress every day, we will a require minimum bandwidth of around 120 MB per second.  
10.2 T B ( 24 h r s × 3600 s e c o n d s ) = ∼ 120 M B / s e c o n d \\frac{10.2 \\space TB}{(24 \\space hrs \\times 3600 \\space seconds)} = \\sim 120 \\space MB/second (24 hrs×3600 seconds)10.2 TB=∼120 MB/second
### High-level estimate

Here is our high-level estimate:  

|           Type            |  Estimate  |
|---------------------------|------------|
| Daily active users (DAU)  | 50 million |
| Requests per second (RPS) | 24K/s      |
| Storage (per day)         | \~10.2 TB  |
| Storage (10 years)        | \~38 PB    |
| Bandwidth                 | \~120 MB/s |

Data model design
-----------------

This is the general data model which reflects our requirements.

[![whatsapp-datamodel](https://res.cloudinary.com/practicaldev/image/fetch/s--k901lG9X--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-datamodel.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--k901lG9X--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `phoneNumber`, and other details.

**messages**

As the name suggests, this table will store messages with properties such as `type` (text, image, video, etc.), `content`, and timestamps for message delivery. The message will also have a corresponding `chatID` or `groupID`.

**chats**

This table basically represents a private chat between two users and can contain multiple messages.

**users_chats**

This table maps users and chats as multiple users can have multiple chats (N:M relationship) and vice versa.

**groups**

This table represents a group between multiple users.

**users_groups**

This table maps users and groups as multiple users can be a part of multiple groups (N:M relationship) and vice versa.

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

API design
----------

Let us do a basic API design for our services:

### Get all chats or groups

This API will get all chats or groups for a given `userID`.  

    getAll(userID: UUID): Chat[] | Group[]

Enter fullscreen mode Exit fullscreen mode

**Parameters**

User ID (`UUID`): ID of the current user.

**Returns**

Result (`Chat[] | Group[]`): All the chats and groups the user is a part of.

### Get messages

Get all messages for a user given the `channelID` (chat or group id).  

    getMessages(userID: UUID, channelID: UUID): Message[]

Enter fullscreen mode Exit fullscreen mode

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) from which messages need to be retrieved.

**Returns**

Messages (`Message[]`): All the messages in a given chat or group.

### Send message

Send a message from a user to a channel (chat or group).  

    sendMessage(userID: UUID, channelID: UUID, message: Message): boolean

Enter fullscreen mode Exit fullscreen mode

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) user wants to send a message to.

Message (`Message`): The message (text, image, video, etc.) that the user wants to send.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Join or leave a group

Send a message from a user to a channel (chat or group).  

    joinGroup(userID: UUID, channelID: UUID): boolean
    leaveGroup(userID: UUID, channelID: UUID): boolean
Enter fullscreen mode Exit fullscreen mode

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) the user wants to join or leave.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

High-level design
-----------------

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This is an HTTP-based service that handles user-related concerns such as authentication and user information.

**Chat Service**

The chat service will use WebSockets and establish connections with the client to handle chat and group message-related functionality. We can also use cache to keep track of all the active connections sort of like sessions which will help us determine if the user is online or not.

**Notification Service**

This service will simply send push notifications to the users. It will be discussed in detail separately.

**Presence Service**

The presence service will keep track of the last seen status of all users. It will be discussed in detail separately.

**Media service**

This service will handle the media (images, videos, files, etc.) uploads. It will be discussed in detail separately.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

*Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other.*

### Real-time messaging

How do we efficiently send and receive messages? We have two different options:

**Pull model**

The client can periodically send an HTTP request to servers to check if there are any new messages. This can be achieved via something like [Long polling](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#long-polling).

**Push model**

The client opens a long-lived connection with the server and once new data is available it will be pushed to the client. We can use [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) or [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) for this.

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) is a better choice because then we can push data to the client once it's available without any delay given the connection is open with the client. Also, WebSockets provide full-duplex communication, unlike [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) which are only unidirectional.

*Note: Learn more about [Long polling, WebSockets, Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events).*

### Last seen

To implement the last seen functionality, we can use a [heartbeat](https://en.wikipedia.org/wiki/Heartbeat_(computing)) mechanism, where the client can periodically ping the servers indicating its liveness. Since this needs to be as low overhead as possible, we can store the last active timestamp in the cache as follows:  

|  Key   |        Value        |
|--------|---------------------|
| User A | 2022-07-01T14:32:50 |
| User B | 2022-07-05T05:10:35 |
| User C | 2022-07-10T04:33:25 |

This will give us the last time the user was active. This functionality will be handled by the presence service combined with [Redis](https://redis.io) or [Memcached](https://memcached.org) as our cache.

Another way to implement this is to track the latest action of the user, once the last activity crosses a certain threshold, such as *"user hasn't performed any action in the last 30 seconds"*, we can show the user as offline and last seen with the last recorded timestamp. This will be more of a lazy update approach and might benefit us over heartbeat in certain cases.

### Notifications

Once a message is sent in a chat or a group, we will first check if the recipient is active or not, we can get this information by taking the user's active connection and last seen into consideration.

If the recipient is not active, the chat service will add an event to a [message queue](https://karanpratapsingh.com/courses/system-design/message-queues) with additional metadata such as the client's device platform which will be used to route the notification to the correct platform later on.

The notification service will then consume the event from the message queue and forward the request to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) based on the client's device platform (Android, iOS, web, etc). We can also add support for email and SMS.

**Why are we using a message queue?**

Since most message queues provide best-effort ordering which ensures that messages are generally delivered in the same order as they're sent and that a message is delivered at least once which is an important part of our service functionality.

While this seems like a classic [publish-subscribe](https://karanpratapsingh.com/courses/system-design/publish-subscribe) use case, it is actually not as mobile devices and browsers each have their own way of handling push notifications. Usually, notifications are handled externally via Firebase Cloud Messaging (FCM) or Apple Push Notification Service (APNS) unlike message fan-out which we commonly see in backend services. We can use something like [Amazon SQS](https://aws.amazon.com/sqs) or [RabbitMQ](https://www.rabbitmq.com) to support this functionality.

### Read receipts

Handling read receipts can be tricky, for this use case we can wait for some sort of [Acknowledgment (ACK)](https://en.wikipedia.org/wiki/Acknowledgement_(data_networks)) from the client to determine if the message was delivered and update the corresponding `deliveredAt` field. Similarly, we will mark message the message seen once the user opens the chat and update the corresponding `seenAt` timestamp field.

### Design

Now that we have identified some core components, let's do the first draft of our system design.

[![whatsapp-basic-design](https://res.cloudinary.com/practicaldev/image/fetch/s--i0woH4ao--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-basic-design.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--i0woH4ao--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-basic-design.png)

Detailed design
---------------

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

* Hash-Based Partitioning
* List-Based Partitioning
* Range Based Partitioning
* Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

*For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).*

### Caching

In a messaging application, we have to be careful about using cache as our users expect the latest data, but many users will be requesting the same messages, especially in a group chat. So, to prevent usage spikes from our resources we can cache older messages.

Some group chats can have thousands of messages and sending that over the network will be really inefficient, to improve efficiency we can add pagination to our system APIs. This decision will be helpful for users with limited network bandwidth as they won't have to retrieve old messages unless requested.

**Which cache eviction policy to use?**

We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) and cache 20% of the daily traffic but what kind of cache eviction policy would best fit our needs?

[Least Recently Used (LRU)](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

*For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching).*

### Media access and storage

As we know, most of our storage space will be used for storing media files such as images, videos, or other files. Our media service will be handling both access and storage of the user media files.

But where can we store files at scale? Well, [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) is what we're looking for. Object stores break data files up into pieces called objects. It then stores those objects in a single repository, which can be spread out across multiple networked systems. We can also use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs) or [GlusterFS](https://www.gluster.org).

*Fun fact: Whatsapp deletes media on its servers once it has been downloaded by the user.*

We can use object stores like [Amazon S3](https://aws.amazon.com/s3), [Azure Blob Storage](https://azure.microsoft.com/en-in/services/storage/blobs), or [Google Cloud Storage](https://cloud.google.com/storage) for this use case.

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.

### API gateway

Since we will be using multiple protocols like HTTP, WebSocket, TCP/IP, deploying multiple L4 (transport layer) or L7 (application layer) type load balancers separately for each protocol will be expensive. Instead, we can use an [API Gateway](https://karanpratapsingh.com/courses/system-design/api-gateway) that supports multiple protocols without any issues.

API Gateway can also offer other features such as authentication, authorization, rate limiting, throttling, and API versioning which will improve the quality of our services.

We can use services like [Amazon API Gateway](https://aws.amazon.com/api-gateway) or [Azure API Gateway](https://azure.microsoft.com/en-in/services/api-management) for this use case.

Identify and resolve bottlenecks
--------------------------------

[![whatsapp-advanced-design](https://res.cloudinary.com/practicaldev/image/fetch/s--SuH4tPBA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-advanced-design.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--SuH4tPBA--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

* "What if one of our services crashes?"
* "How will we distribute our traffic between our components?"
* "How can we reduce the load on our database?"
* "How to improve the availability of our cache?"
* "Wouldn't API Gateway be a single point of failure?"
* "How can we make our notification system more robust?"
* "How can we reduce media storage costs"?
* "Does chat service has too much responsibility?"

To make our system more resilient we can do the following:

* Running multiple instances of each of our services.
* Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
* Using multiple read replicas for our databases.
* Multiple instances and replicas for our distributed cache.
* We can have a standby replica of our API Gateway.
* Exactly once delivery and message ordering is challenging in a distributed system, we can use a dedicated [message broker](https://karanpratapsingh.com/courses/system-design/message-brokers) such as [Apache Kafka](https://kafka.apache.org) or [NATS](https://nats.io) to make our notification system more robust.
* We can add media processing and compression capabilities to the media service to compress large files similar to Whatsapp which will save a lot of storage space and reduce cost.
* We can create a group service separate from the chat service to further decouple our services.

*This article is part of my open source [System Design Course](https://github.com/karanpratapsingh/system-design) available on Github.*  

![GitHub logo](https://res.cloudinary.com/practicaldev/image/fetch/s--566lAguM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev.to/assets/github-logo-5a155e1f9a670af7944dd5e12375bc76ed542ea80224905ecaf878b9157cdefc.svg) [karanpratapsingh](https://github.com/karanpratapsingh) / [system-design](https://github.com/karanpratapsingh/system-design)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Learn how to design systems at scale and prepare for system design interviews

System Design Course
====================

Hey, welcome to the course. I hope this course provides a great learning experience.

*This course is also available on my [website](https://karanpratapsingh.com/courses/system-design). Please leave a ⭐ as motivation if this was helpful!*

Table of contents
=================

* **Getting Started**

  * [What is system design?](https://github.com/karanpratapsingh/system-design#what-is-system-design)
* **Chapter I**

  * [IP](https://github.com/karanpratapsingh/system-design#ip)
  * [OSI Model](https://github.com/karanpratapsingh/system-design#osi-model)
  * [TCP and UDP](https://github.com/karanpratapsingh/system-design#tcp-and-udp)
  * [Domain Name System (DNS)](https://github.com/karanpratapsingh/system-design#domain-name-system-dns)
  * [Load Balancing](https://github.com/karanpratapsingh/system-design#load-balancing)
  * [Clustering](https://github.com/karanpratapsingh/system-design#clustering)
  * [Caching](https://github.com/karanpratapsingh/system-design#caching)
  * [Content Delivery Network (CDN)](https://github.com/karanpratapsingh/system-design#content-delivery-network-cdn)
  * [Proxy](https://github.com/karanpratapsingh/system-design#proxy)
  * [Availability](https://github.com/karanpratapsingh/system-design#availability)
  * [Scalability](https://github.com/karanpratapsingh/system-design#scalability)
  * [Storage](https://github.com/karanpratapsingh/system-design#storage)
* **Chapter II**

  * [Databases and DBMS](https://github.com/karanpratapsingh/system-design#databases-and-dbms)
  * [SQL databases](https://github.com/karanpratapsingh/system-design#sql-databases)
  * [NoSQL databases](https://github.com/karanpratapsingh/system-design#nosql-databases)
  * [SQL vs NoSQL databases](https://github.com/karanpratapsingh/system-design#sql-vs-nosql-databases)
  * [Database Replication](https://github.com/karanpratapsingh/system-design#database-replication)
  * [Indexes](https://github.com/karanpratapsingh/system-design#indexes)
  * [Normalization and Denormalization](https://github.com/karanpratapsingh/system-design#normalization-and-denormalization)
  * [ACID and BASE consistency models](https://github.com/karanpratapsingh/system-design#acid-and-base-consistency-models)
  * [CAP theorem](https://github.com/karanpratapsingh/system-design#cap-theorem)
  * [PACELC Theorem](https://github.com/karanpratapsingh/system-design#pacelc-theorem)
  * [Transactions](https://github.com/karanpratapsingh/system-design#transactions)
  * [Distributed Transactions](https://github.com/karanpratapsingh/system-design#distributed-transactions)
  * [Sharding](https://github.com/karanpratapsingh/system-design#sharding)
  * [Consistent Hashing](https://github.com/karanpratapsingh/system-design#consistent-hashing)
  * [Database Federation](https://github.com/karanpratapsingh/system-design#database-federation)
* **Chapter III**

  * [N-tier architecture](https://github.com/karanpratapsingh/system-design#n-tier-architecture)
  * [Message Brokers](https://github.com/karanpratapsingh/system-design#message-brokers)
  * [Message Queues](https://github.com/karanpratapsingh/system-design#message-queues)
  * [Publish-Subscribe](https://github.com/karanpratapsingh/system-design#publish-subscribe)
  * [Enterprise Service Bus (ESB)](https://github.com/karanpratapsingh/system-design#enterprise-service-bus-esb)
  * [Monoliths and Microservices](https://github.com/karanpratapsingh/system-design#monoliths-and-microservices)
  * [Event-Driven Architecture (EDA)](https://github.com/karanpratapsingh/system-design#event-driven-architecture-eda)
  * [Event Sourcing](https://github.com/karanpratapsingh/system-design#event-sourcing)
  * [Command and Query Responsibility Segregation (CQRS)](https://github.com/karanpratapsingh/system-design#command-and-query-responsibility-segregation-cqrs)
  * [API Gateway](https://github.com/karanpratapsingh/system-design#api-gateway)
  * [REST, GraphQL, gRPC](https://github.com/karanpratapsingh/system-design#rest-graphql-grpc)
  * [Long polling, WebSockets, Server-Sent Events (SSE)](https://github.com/karanpratapsingh/system-design#long-polling-websockets-server-sent-events-sse)
* **Chapter IV**

  * [Geohashing and Quadtrees](https://github.com/karanpratapsingh/system-design#geohashing-and-quadtrees)
  * [Circuit breaker](https://github.com/karanpratapsingh/system-design#circuit-breaker)
* ...  
[View on GitHub](https://github.com/karanpratapsingh/system-design)

System Design (57 Part Series)
------------------------------

1 System Design: The complete course 2 System Design: What is system design? ... 53 more parts... 3 System Design: IP 4 System Design: OSI Model 5 System Design: TCP and UDP 6 System Design: Domain Name System (DNS) 7 System Design: Load Balancing 8 System Design: Clustering 9 System Design: Caching 10 System Design: Content Delivery Network (CDN) 11 System Design: Proxy 12 System Design: Availability 13 System Design: Scalability 14 System Design: Storage 15 System Design: Databases and DBMS 16 System Design: SQL databases 17 System Design: NoSQL databases 18 System Design: SQL vs NoSQL databases 19 System Design: Database Replication 20 System Design: Indexes 21 System Design: Normalization and Denormalization 22 System Design: ACID and BASE consistency models 23 System Design: CAP theorem 24 System Design: PACELC Theorem 25 System Design: Transactions 26 System Design: Distributed Transactions 27 System Design: Sharding 28 System Design: Consistent Hashing 29 System Design: Database Federation 30 System Design: N-tier architecture 31 System Design: Message Brokers 32 System Design: Message Queues 33 System Design: Publish-Subscribe 34 System Design: Enterprise Service Bus (ESB) 35 System Design: Monoliths and Microservices 36 System Design: Event-Driven Architecture (EDA) 37 System Design: Event Sourcing 38 System Design: Command and Query Responsibility Segregation (CQRS) 39 System Design: API Gateway 40 System Design: REST, GraphQL, gRPC 41 System Design: Long polling, WebSockets, Server-Sent Events (SSE) 42 System Design: Geohashing and Quadtrees 43 System Design: Circuit breaker 44 System Design: Rate Limiting 45 System Design: Service Discovery 46 System Design: SLA, SLO, SLI 47 System Design: Disaster recovery 48 System Design: Virtual Machines (VMs) and Containers 49 System Design: OAuth 2.0 and OpenID Connect (OIDC) 50 System Design: Single Sign-On (SSO) 51 System Design: SSL, TLS, mTLS 52 System Design: System Design Interviews 53 System Design: URL Shortener 54 System Design: WhatsApp 55 System Design: Twitter 56 System Design: Netflix 57 System Design: Uber  

Top comments (13)
-----------------

Crown

### Sort discussion:

*
  Selected Sort Option Top

  Most upvoted and relevant comments will be first
*
  Latest

  Most recent comments will be first
*
  Oldest

  The oldest comments will be first

Subscribe  
![pic](https://res.cloudinary.com/practicaldev/image/fetch/s--RmY55OKL--/c_limit,f_auto,fl_progressive,q_auto,w_256/https://practicaldev-herokuapp-com.freetls.fastly.net/assets/devlogo-pwa-512.png)  
Personal Trusted User ![loading](https://dev.to/assets/loading-ellipsis-b714cf681fd66c853ff6f03dd161b77aa3c80e03cdc06f478b695f42770421e9.svg)  
Create template

Templates let you quickly answer FAQs or store snippets for re-use.  
Submit Preview Dismiss  
Collapse Expand  
[![crayoncode profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--y2EN2JD9--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/498407/d3355612-d12d-4189-b335-b1a7eae27fd8.png)](https://dev.to/crayoncode)  
[crayoncode](https://dev.to/crayoncode)  
crayoncode  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--SEHLYSbD--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/498407/d3355612-d12d-4189-b335-b1a7eae27fd8.png) crayoncode  
Follow  
All about coding (and occasionally other topics) and explaining it through beautiful visualizations.  
  * Joined  
  Oct 25, 2020
• [Sep 21](https://dev.to/crayoncode/comment/21n1h)  
Dropdown menu  
* [Copy link](https://dev.to/crayoncode/comment/21n1h)
* 
* Hide
* 
* 
*  
Great article! Love how you estimated the traffic 😅
Like comment: Like comment: 5 likes Like Comment button Reply
Collapse Expand  
[![othimar profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--81RxTGK1--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/877823/f8573a7a-c34a-4eb7-ba72-45e119aa6b5b.jpg)](https://dev.to/othimar)  
[Pélé Oussoumanou](https://dev.to/othimar)  
Pélé Oussoumanou  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--5UOqSPDd--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/877823/f8573a7a-c34a-4eb7-ba72-45e119aa6b5b.jpg) Pélé Oussoumanou  
Follow  
Hi I'm a young developer searching experiences.  
  * Location  
  Garoua, Cameroon
  * Education  
  Faculty of Sciences, University of Ngaoundéré
  * Joined  
  Jun 16, 2022
• [Sep 21](https://dev.to/othimar/comment/21n5p)  
Dropdown menu  
* [Copy link](https://dev.to/othimar/comment/21n5p)
* 
* Hide
* 
* 
*  
Impressive. I was skimming the article and those estimations caught my attention. I will read it later.
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![andrewbaisden profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--oztBbot4--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/333889/dd8bedde-89c4-45a0-9620-627131cf32de.png)](https://dev.to/andrewbaisden)  
[Andrew Baisden](https://dev.to/andrewbaisden)  
Andrew Baisden  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--n393t-_I--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/333889/dd8bedde-89c4-45a0-9620-627131cf32de.png) Andrew Baisden  
Follow  
⚛️ Software Developer @CGI_Global \| 🌅 Technical Writer @ThePracticalDev @hashnode @Medium @LogRocket \| 🎨 Content Creator \| 📝 5k+ Blog Subscribers  
  * Location  
  London, UK
  * Education  
  Bachelor Degree Computer Science
  * Work  
  Software Developer @CGI
  * Joined  
  Feb 11, 2020
• [Sep 25](https://dev.to/andrewbaisden/comment/21pdd)  
Dropdown menu  
* [Copy link](https://dev.to/andrewbaisden/comment/21pdd)
* 
* Hide
* 
* 
*  
Wow, so detailed good article.
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![krishgokul profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--Z2tSRLab--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/898320/c63fe7e9-e660-41c9-b1bb-08157124584d.jpeg)](https://dev.to/krishgokul)  
[Gokula Krishnan](https://dev.to/krishgokul)  
Gokula Krishnan  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--Zl5i2Y1m--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/898320/c63fe7e9-e660-41c9-b1bb-08157124584d.jpeg) Gokula Krishnan  
Follow  
  * Work  
  Programmer Analyst Trainee at Cognizant Technology Solutions
  * Joined  
  Jul 26, 2022
• [Sep 22](https://dev.to/krishgokul/comment/21o44)  
Dropdown menu  
* [Copy link](https://dev.to/krishgokul/comment/21o44)
* 
* Hide
* 
* 
*  
Great work! Will try to go through all other topics too. May I know the tool used to make the diagrams please?
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![karanpratapsingh profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--7GrdBPf3--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/350819/b3e261fa-d88e-4cb4-80a2-233ab491af4e.jpg)](https://dev.to/karanpratapsingh)  
[Karan Pratap Singh Author](https://dev.to/karanpratapsingh)  
Karan Pratap Singh  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--ZojEd3KA--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/350819/b3e261fa-d88e-4cb4-80a2-233ab491af4e.jpg) Karan Pratap Singh  
Follow  
A software engineer who values learning and growing with people, teams, and technologies.  
  * Email  
  [contact@karanpratapsingh.com](mailto:contact@karanpratapsingh.com)
  * Work  
  Senior Software Engineer
  * Joined  
  Mar 15, 2020
Author
• [Sep 24](https://dev.to/karanpratapsingh/comment/21p3c)  
Dropdown menu  
* [Copy link](https://dev.to/karanpratapsingh/comment/21p3c)
* 
* Hide
* 
* 
*  
Thanks, I used excalidraw for diagrams
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![dhanushnehru profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--X0yirsFJ--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/457133/3b2b1b89-fa77-4855-a8f6-a685b417ac95.png)](https://dev.to/dhanushnehru)  
[Dhanush N](https://dev.to/dhanushnehru)  
Dhanush N  
![](https://res.cloudinary.com/practicaldev/image/fetch/s---7yC-i3d--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/457133/3b2b1b89-fa77-4855-a8f6-a685b417ac95.png) Dhanush N  
Follow  
Tech autodidact 👑 Full Stack Dev 🖱️ Puzzle Solver 🧩 Chess Player ♟️  
  * Location  
  Chennai
  * Education  
  B.E. Computer Science \& Engineering
  * Work  
  Software Engineer
  * Joined  
  Aug 23, 2020
• [Sep 22](https://dev.to/dhanushnehru/comment/21nj0)  
Dropdown menu  
* [Copy link](https://dev.to/dhanushnehru/comment/21nj0)
* 
* Hide
* 
* 
*  
Well written article.

I just made a [personal WhatsApp](https://dev.to/dhanushnehru/whatsapp-portfolio-website-3fdo) kindoff, Just felt like mentioning it here
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![emil profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--6OvOOocj--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/570128/4f86a197-7310-431e-b6c8-1f9c0851811a.jpg)](https://dev.to/emil)  
[Emil](https://dev.to/emil)  
Emil  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--UNzVWYT1--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/570128/4f86a197-7310-431e-b6c8-1f9c0851811a.jpg) Emil  
Follow  
  * Education  
  Computer Science
  * Work  
  Senior Software Developer at Syskron GmbH
  * Joined  
  Jan 30, 2021
• [Sep 22 • Edited on Sep 22](https://dev.to/emil/comment/21o1a)  
Dropdown menu  
* [Copy link](https://dev.to/emil/comment/21o1a)
* 
* Hide
* 
* 
*  
As you are using microservices you should mention that you might not want to share a single database instance. The benefit of microservices is an independent deployment which might not work out in your setup.

But I like your explanations and thoughts
Like comment: Like comment: 1 like Like Comment button Reply
Collapse Expand  
[![juanvegadev profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--QZ7a3ISa--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/141711/add58eef-3934-4b7a-87c1-ab9043a287be.jpg)](https://dev.to/juanvegadev)  
[Juan Vega](https://dev.to/juanvegadev)  
Juan Vega  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--UVvzLSe6--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/141711/add58eef-3934-4b7a-87c1-ab9043a287be.jpg) Juan Vega  
Follow  
Always sharing, always learning. I am a software engineer, who values a good work-life balance and working with a great team making an impact product over technology.  
  * Location  
  Spain
  * Education  
  University Degree on Software Engineer
  * Work  
  Software Engineer at Typeform
  * Joined  
  Mar 3, 2019
• [Sep 22](https://dev.to/juanvegadev/comment/21nkn)  
Dropdown menu  
* [Copy link](https://dev.to/juanvegadev/comment/21nkn)
* 
* Hide
* 
* 
*  
Nice article.

I think there is a typo on number of message estimations.
> each user sends at least 10 messages to 4 different people every day.

It says 10 messages to 4 people which would be 40 message and then you use 20 messages for the calculation.
Like comment: Like comment: 1 like Like Comment button Reply
Collapse Expand  
[![fk profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--hNBSQkBy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/101694/fff5f5cd-d3f7-4d23-a8cc-3474ccbd3c20.jpg)](https://dev.to/fk)  
[Fırat KÜÇÜK](https://dev.to/fk)  
Fırat KÜÇÜK  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--AxgbzIWO--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/101694/fff5f5cd-d3f7-4d23-a8cc-3474ccbd3c20.jpg) Fırat KÜÇÜK  
Follow  
Lifetime developer, Sci-fi addicted, cat squeezer, the last baklava bender, good lyrics detector, meeting doodler, bench activist, entrepreneur-ish.  
  * Location  
  The Netherlands
  * Joined  
  Sep 16, 2018
• [Sep 22](https://dev.to/fk/comment/21njl)  
Dropdown menu  
* [Copy link](https://dev.to/fk/comment/21njl)
* 
* Hide
* 
* 
*  
Good article, tables should not contain messages. Whatsapp uses end to end encryption. Communications are handled without an intermediate server.
Like comment: Like comment: Like Comment button Reply
Collapse Expand  
[![lweiner profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--GdqnW6tt--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/771561/ca1f3c6c-12ba-425d-8eea-706ad11630be.jpeg)](https://dev.to/lweiner)  
[Lukas Weiner](https://dev.to/lweiner)  
Lukas Weiner  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--UPPBec-N--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/771561/ca1f3c6c-12ba-425d-8eea-706ad11630be.jpeg) Lukas Weiner  
Follow  
  * Joined  
  Dec 9, 2021
• [Sep 23](https://dev.to/lweiner/comment/21oe1)  
Dropdown menu  
* [Copy link](https://dev.to/lweiner/comment/21oe1)
* 
* Hide
* 
* 
*  
They are handled and stored in a database, but they are encrypted and decrypted on your phone. So that's why you can't load all message from the server as soon as you are changing your device. If you want to go deeper into the topic you can search for asymmetric cryptography. So yes the author is right with storing the message on the server, the only difference is that they are not stored as plain text, they are stored encrypted.
Like comment: Like comment: 1 like Like Comment button Reply
Collapse Expand  
[![fk profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--hNBSQkBy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/101694/fff5f5cd-d3f7-4d23-a8cc-3474ccbd3c20.jpg)](https://dev.to/fk)  
[Fırat KÜÇÜK](https://dev.to/fk)  
Fırat KÜÇÜK  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--AxgbzIWO--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/101694/fff5f5cd-d3f7-4d23-a8cc-3474ccbd3c20.jpg) Fırat KÜÇÜK  
Follow  
Lifetime developer, Sci-fi addicted, cat squeezer, the last baklava bender, good lyrics detector, meeting doodler, bench activist, entrepreneur-ish.  
  * Location  
  The Netherlands
  * Joined  
  Sep 16, 2018
• [Sep 24 • Edited on Sep 24](https://dev.to/fk/comment/21oml)  
Dropdown menu  
* [Copy link](https://dev.to/fk/comment/21oml)
* 
* Hide
* 
* 
*  
[techuntold.com/where-whatsapp-mess...](https://www.techuntold.com/where-whatsapp-messages-stored/)
> The only time a message is stored on WhatsApp's servers is if the recipient cannot receive it (maybe they're offline or don't have a WhatsApp account). In cases like those, the message(s) you sent are automatically deleted off of WhatsApp's server in 30 days' time.
>
> So this probably has you wondering if WhatsApp doesn't store your messages on its servers, then where are they stored? The answer is, your WhatsApp messages are stored locally on your phone in the form of encrypted backups.
Like comment: Like comment: 1 like Like Thread Thread  
[![lweiner profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--GdqnW6tt--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/771561/ca1f3c6c-12ba-425d-8eea-706ad11630be.jpeg)](https://dev.to/lweiner)  
[Lukas Weiner](https://dev.to/lweiner)  
Lukas Weiner  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--UPPBec-N--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/771561/ca1f3c6c-12ba-425d-8eea-706ad11630be.jpeg) Lukas Weiner  
Follow  
  * Joined  
  Dec 9, 2021
• [Sep 24](https://dev.to/lweiner/comment/21ona)  
Dropdown menu  
* [Copy link](https://dev.to/lweiner/comment/21ona)
* 
* Hide
* 
* 
*  
Ah I didn't knew that, thanks for correcting me. Really interesting.
Like comment: Like comment: 2 likes Like Comment button Reply
Collapse Expand  
[![alexigbokwe profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--ErcgkIeF--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/368617/f96c2f56-e714-4c92-ad19-3ac749e4a749.jpeg)](https://dev.to/alexigbokwe)  
[Alex Igbokwe](https://dev.to/alexigbokwe)  
Alex Igbokwe  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--8o9oQUQP--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/368617/f96c2f56-e714-4c92-ad19-3ac749e4a749.jpeg) Alex Igbokwe  
Follow  
Software engineer, lover of good quality code, Javascript, Typescript, PHP, C#, Java  
  * Location  
  Nigeria
  * Education  
  Federal University Of Technology Owerri (Computer Science )
  * Joined  
  Apr 17, 2020
• [Sep 22](https://dev.to/alexigbokwe/comment/21o78)  
Dropdown menu  
* [Copy link](https://dev.to/alexigbokwe/comment/21o78)
* 
* Hide
* 
* 
*  
Fantastic job. Nice one
Like comment: Like comment: 1 like Like Comment button Reply  
Code of Conduct • Report abuse  
Are you sure you want to hide this comment? It will become hidden in your post, but will still be visible via the comment's permalink.

Hide child comments as well

Confirm

For further actions, you may consider blocking this person and/or reporting abuse  

#### 🌚 Life is too short to browse without [dark mode](https://dev.to/settings/customization)

Read next
---------


![devrohit0 profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--2-VeAx6w--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/744748/09db49af-a1a8-4adf-87b6-f597db97a776.jpg)  

### Create an Accordion with Tailwind CSS and Alpine JS

Rohit Sharma - Sep 19

![devpishaili profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--ch4n1_Dg--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/916132/3df09c33-44d0-40c5-be94-a0fb0168311d.jpeg)  

### HTML Tables Simplified

Dev P Ishaili - Sep 10

![tutorialinhindi profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--3NwOcGX3--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/595947/6ba0afdf-2c30-4d57-99c6-cb3360e8d4a4.png)  

### FREE Python Course in Hindi (Download Free PDF)

Tutorial In Hindi - Sep 5

![mbarzeev profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--YxwIAkII--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/210953/29b527cd-2c72-4a08-af7b-a8e4eb778637.png)  

### Introducing esbuild To Your Monorepo

Matti Bar-Zeev - Sep 9  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--ZojEd3KA--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/350819/b3e261fa-d88e-4cb4-80a2-233ab491af4e.jpg) Karan Pratap Singh  
Follow  
A software engineer who values learning and growing with people, teams, and technologies.  
  * Work  
  Senior Software Engineer
  * Joined  
Mar 15, 2020  

### More from Karan Pratap Singh

System Design: Uber  
#distributedsystems #architecture #tutorial System Design: Netflix  
#distributedsystems #architecture #tutorial System Design: Twitter  
#distributedsystems #architecture #tutorial  
Once suspended, karanpratapsingh will not be able to comment or publish posts until their suspension is removed.  
Note:

Submit \& Suspend  
Once unsuspended, karanpratapsingh will be able to comment and publish posts again.  
Note:

Submit \& Unsuspend  
Once unpublished, all posts by karanpratapsingh will become hidden and only accessible to themselves.

If karanpratapsingh is not suspended, they can still re-publish their posts from their dashboard.  
Unpublish all posts  
Once unpublished, this post will become invisible to the public and only accessible to Karan Pratap Singh.

They can still re-publish the post if they are not suspended.  
Unpublish post  
Thanks for keeping DEV Community 👩‍💻👨‍💻 safe. Here is what you can do to flag karanpratapsingh:  
Make all posts by karanpratapsingh less visible

karanpratapsingh consistently posts content that violates DEV Community 👩‍💻👨‍💻's code of conduct because it is harassing, offensive or spammy.  
Report other inappropriate conduct  
Confirm Flag  
Unflagging karanpratapsingh will restore default visibility to their posts.  
Confirm Unflag  
DEV Community 👩‍💻👨‍💻 --- A constructive and inclusive social network for software developers. With you every step of your journey.  
Built on [Forem](https://www.forem.com) --- the [open source](https://dev.to/t/opensource) software that powers [DEV](https://dev.to) and other inclusive communities.

Made with love and [Ruby on Rails](https://dev.to/t/rails). DEV Community 👩‍💻👨‍💻 © 2016 - 2022.
[Forem logo](https://www.forem.com)  
![DEV Community 👩‍💻👨‍💻](https://res.cloudinary.com/practicaldev/image/fetch/s--pcSkTMZL--/c_limit,f_auto,fl_progressive,q_80,w_190/https://practicaldev-herokuapp-com.freetls.fastly.net/assets/devlogo-pwa-512.png)  
We're a place where coders share, stay up-to-date and grow their careers.  
Log in Create account  
