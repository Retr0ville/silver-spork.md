---
title: What do you use for background jobs? : golang
tags: android blog rtrvl
author: retr0ville
source: https://www.reddit.com/r/golang/comments/rtxbq7/what_do_you_use_for_background_jobs/
---
What do you use for background jobs? : golang  
Press J to jump to the feed. Press question mark to learn the rest of the keyboard shortcuts  
Search all of Reddit  
[Log In](https://www.reddit.com/login/?dest=https%3A%2F%2Fwww.reddit.com%2Fr%2Fgolang%2Fcomments%2Frtxbq7%2Fwhat_do_you_use_for_background_jobs%2F) [Sign Up](https://www.reddit.com/register/?dest=https%3A%2F%2Fwww.reddit.com%2Fr%2Fgolang%2Fcomments%2Frtxbq7%2Fwhat_do_you_use_for_background_jobs%2F)  
User account menu  
Found the internet!  

r/ golang  
Posts  
7  
Posted by 9 months ago  

What do you use for background jobs?
====================================

![](https://www.redditstatic.com/desktop2x/img/renderTimingPixel.png)  
In the Ruby world, [sidekiq](https://sidekiq.org) is a popular background job server. I can see that the same company makes [faktory](https://contribsys.com/faktory/), which is written in Go. I'm also aware of [Cadence](https://github.com/uber/cadence) and [Temporal](https://temporal.io), which are both written in Go.

What do you use for background jobs? Ideally I'm looking for something that supports batch jobs and configurable retry.  
20 comments  
share  
save  
hide  
report  
82% Upvoted  
Sort by: new (suggested)  
![](https://www.redditstatic.com/desktop2x/img/renderTimingPixel.png)

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hr6ucmo/?utm_source=reddit&utm_medium=web2x&context=3)  
Asynq! I was evaluating multiple available libraries and I found it to best suit my needs I.e. to schedule task to run at specific date time.  
1  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqxpbf4/?utm_source=reddit&utm_medium=web2x&context=3)  
i work at Temporal - we're pretty good in Go :) questions welcome  
2  
Reply  
Share
Report Save Follow  

level 2  
Op · [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqzv79y/?utm_source=reddit&utm_medium=web2x&context=3) · edited 9 mo. ago  
Temporal is definitely very intriguing to me. I do indeed have questions, having a surface-level understanding of the docs :)

1. Given the code in listing 1 below (modified slightly from the Temporal homepage), are the emails sent in parallel, or in sequence?

2. Same question for the code in listing 2, which is (I believe equivalent) TypeScript.

3. What if I change the `Promise.all` line to be another loop (`for (const userId of userIds) { ...`) and `await` each user id in that loop? Does that change the behavior at all?

4. Is there any way to redact, or better yet, not log at all, any job arguments / info such as PII? Can this be selectively done? Can I use some form of allow list rather than a deny list for this?

5. What happens in each process above when we tell the workflow to sleep for days at a time? Does the process remain running? Does the process suspend and resume at a later time? Does the process die and then resume at a later time?

6. Continuing that question, what happens during a long sleep if the server the process is running on is killed? What if we're somewhere farther along in the workflow?

**Code listings:**

If anyone knows of a smarter way to put code blocks inside reddit markdown lists I'm all ears. For some reason I couldn't get these for format as code above (old reddit).

**listing 1:**

    func PaymentWorkflow(ctx workflow.Context, userIds []string, intervals []int) error {
      // Send reminder emails, e.g. after 1, 7, and 30 days
      for _, interval := range intervals {
        _ = workflow.Sleep(ctx, days(interval)) // Sleep for days!
        for _, userId := range userIds {
          _ = workflow.ExecuteActivity(ctx, SendEmail, userId).Get(ctx, nil) 
        }
         // Activities have timeouts, and will be retried by default!
      }
      // ...
     }
**listing 2:**

    async function remindUserWorkflow(userIds: string[], intervals: number[]) {
      // Send reminder emails, e.g. after 1, 7, and 30 days
      for (const interval of intervals) {
        await wf.sleep(interval + " days");
        await Promise.all(userIds.map(userId => activities.sendEmail(interval, userId)));
      }
      // Easily cancelled when user unsubscribes
    }
2  
Reply  
Share
Report Save Follow  
Continue this thread  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqx0oek/?utm_source=reddit&utm_medium=web2x&context=3)  
Depending in the use case we go for goroutines, Google PubSub or rabbitmq.

I know redis has support for PubSub but never tested it.  
1  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwyf3b/?utm_source=reddit&utm_medium=web2x&context=3)  
We used <https://temporal.io/> at a job recently and it seemed really slick. I didn't personally get very hands on but I think it seemed pretty good from a distance  
2  
Reply  
Share
Report Save Follow  

level 2  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqxpcjt/?utm_source=reddit&utm_medium=web2x&context=3)  
happy to answer any q's! i work there  
2  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwuv1k/?utm_source=reddit&utm_medium=web2x&context=3)  
Depends entirely on the desired complexity. If you simply want to have a queue so you can cope with back pressure, I would use NATS JetStream with a workqueue stream. Write every async task in it, let your workers subscribe to it, profit.

If you have more complicated requirements (priority queues, unique jobs, revoking jobs, checking their status, etc), this will not suffice on its own. Then I would likely look towards Temporal. But that is a lot heavier and therefore slower (since it offers transactional guarantees).  
2  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwu09g/?utm_source=reddit&utm_medium=web2x&context=3)  
<https://github.com/owlint/maestro> Not very well documented at the moment but support interesting features (I am the author).  
1  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwfj1k/?utm_source=reddit&utm_medium=web2x&context=3)  
Details are important, but most likely most sidekiq things will just be a goroutine you spawn ad-hoc. Retry, concurrency limits, etc can all be done natively in Go. Until you need something more elaborate, this will carry you through, and once you have a requirement that it can't satisfy it'll make it much easier to narrow the solution space.  
2  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqw4op3/?utm_source=reddit&utm_medium=web2x&context=3)  
I asked this same question 2 or 3 days ago, here is what I got <https://www.reddit.com/r/golang/comments/rsxrhl/orchestration_engine_recommendations/>  
3  
Reply  
Share
Report Save Follow  

level 2  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwlvpk/?utm_source=reddit&utm_medium=web2x&context=3)  
One thing missing in that thread is asynq.  
3  
Reply  
Share
Report Save Follow  

level 2  
Op · [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqwf64q/?utm_source=reddit&utm_medium=web2x&context=3)  
Thank you!  
1  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqw4f6j/?utm_source=reddit&utm_medium=web2x&context=3)  
I'd say it depends on your stack. However, I tend to lean towards things like AWS SQS and Lambda functions... One lambda function can server as an API and the "queue" worker function can be triggered based on SQS events, so the worker is only invoked when there are messages in the queue. Plus the handlers are typed based on your events so the code ends up being really clean.  
1  
Reply  
Share
Report Save Follow  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqvodu7/?utm_source=reddit&utm_medium=web2x&context=3) · edited 9 mo. ago  
You're writing Go, you can write background jobs natively using go routines and channels! :-)

There are many durable options for background processing available; it really comes down to your use case. What are you trying to do?  
18  
Reply  
Share
Report Save Follow  

level 2  
Op · [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqvp1x3/?utm_source=reddit&utm_medium=web2x&context=3)  
I want to offload expensive work to a pool of worker servers. I want to do the work out of process so the web services can be short-lived.  
4  
Reply  
Share
Report Save Follow  
Continue this thread  

level 1  
· [9 mo. ago](https://www.reddit.com/r/golang/comments/rtxbq7/comment/hqvjtu9/?utm_source=reddit&utm_medium=web2x&context=3)  
Rabbitmq has always been great with a library on top for pushing and pulling jobs, but I'm not familiar with the go libraries for it  
3  
Reply  
Share
Report Save Follow  
View Entire Discussion (20 Comments)  
More posts from the golang community


Continue browsing in r/golang  

About Community
---------------

![Subreddit Icon](https://styles.redditmedia.com/t5_2rc7j/styles/communityIcon_wy4riduoe9k11.png?width=256&s=0d681daaa8d4b6271e6be788d0f9379f0661e04a)  
r/golang  
Ask questions and post articles about the Go programming language and related tools, events etc.  
Created Nov 11, 2009  
189k

gophers  
566

Online
[Top 1%
Ranked by Size](https://www.reddit.com/best/communities/4/#t5_2rc7j "r/golang is in the top 1% of largest communities on Reddit")  
Join  
[![](https://www.redditstatic.com/desktop2x/img/widgets/rereddit-promo/left.png) ![](https://www.redditstatic.com/desktop2x/img/widgets/rereddit-promo/center.png) ![](https://www.redditstatic.com/desktop2x/img/widgets/rereddit-promo/right.png) ![](https://www.redditstatic.com/desktop2x/img/widgets/rereddit-promo/upvotes.png)
![](https://www.redditstatic.com/desktop2x/img/widgets/rereddit-promo/line.png)](https://www.reddit.com/posts/2022/january-2-1/)  
[Top posts january 2nd 2022](https://www.reddit.com/posts/2022/january-2-1/) [Top posts of january, 2022](https://www.reddit.com/posts/2022/january/) [Top posts 2022](https://www.reddit.com/posts/2022/)  
Back to Top  
Advertisement  
