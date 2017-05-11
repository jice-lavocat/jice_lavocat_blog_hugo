+++
date = "2016-07-31"
title = "Using a Live Chat on your app - Setting up Drift with Google Tag Manager"
image = "/images/posts/2016/patents/lock.jpg"
+++

This post is not a review about Drift, but rather about how to use Google Tag Manager and how to make the most of 'events' collected on your application : here I will use Drift as a concrete example.

A few days ago, <a href="http://hiten.com/">Hiten Shah</a> ({{<twitto hnshah>}}) submitted <a href="https://www.drift.com/">Drift</a> on Product Hunt. Drift is nothing new : it's just an in-app chat for your application. If you're looking for in-app chat solutions, you will find dozens : Intercom, Tawkto, Zopim, Olark, Smooch...

A few years ago I was satisfied with Zopim, but recently a quote from Guillaume Cabane gave me to revise my criteria : "We use too many apps, for support chat we wanted it to be connected to Slack since we're using it daily". Since at Elokenz we are also using Slack a lot, I thought it would be great to avoid the multiplication of apps too, and went for Smooch. However, Smooch is certainly great for big multi-platforms project and if you have some time to set it up correctly. But my experience with it was a bit frustrating. With Zopim I could initiate a chat with an online user (I knew who was online and which page they were visiting). I was missing that "initiate the chat" feture with Smooch.

So, whenever I find a new chat app, I look at their features. Drift has a Slack integration, and I can intiate chats with online users too. I'm aware that other apps might do it as the day of writing, but this marlet is really crowded, and it's difficult to have a clear view of all competitors features.

I decided to give a quick shot at Drift. My frontend is powered by AngularJS, and I managed to get things done very quickly by using Google Tag Manager (GTM) and angulartics, an Angular library that you should be using if you're not already.

## In-app events

When you have a website, the first thing you often do is to add Analytics (Google Analytics, Clicky, Piwik, ...) to get the number of visitors and the most visited pages. When you have an application, this kind of information, despite being important, needs to be completed by activity metrics such as the most common actions on your app. You probably want to know who are your active users to discover patterns that drive them to purchasing a subscription.

When I'll be a bit more expert into this field I might write a post about how we are using Mixpanel, but at the omment I'm just a basic user. I use the funnel and retention analysis offered out of the box by Mixpanel. However, pushing your event to Mixpanel can give you a lot of quick insights about your users most triggered actions... anyway, this might be for another post.

When it's the first time you need to send event to a remote tool, you might be wondering what to track. I found a quick and easy way to decide which actions should be sent to my analytics tools. Our architecture if the following : we have a Django backend, that serves data to an AngularJS frontend. The connection if made via an API (here, we're using the wonderful Django Rest Fraework library). If you are not familiar with what REST is, you might need to read this before going on.

So, we have **endpoints** that basically correspond to our data. The frontend can use the 4-5 common commands : GET, POST, PUT/PATCH and DELETE. From this list, GET is the only one that does not modify the data. It's also the most used one: whenever you need to retrieve some object, you perform a GET. Therefore, the other 3 commands are less frequent, and modify data.

I decided to define in-app events for each non-GET REST commands.

Let me give you an example here. I have an endpoint called "/articles". If the user GET /articles, it retrieves his list of articles. On my app, many pages are triggering GET /articles, without even the user knowing it, so I'm not creating an event for that. If he POST /articles he will create a new article, so I'm creating an event "Created Article". If you PATCH /articles/[:id] it will modify one field from the given article, I'm creating an event "Updated Article". If he DELETE /articles/[:id], well, he will deletes the given article from his database, I'm creating an event "Deleted Article".

In addition to those, I decided to also track the visited page (so when a user visits my frontend /your_articles, this triggers the event "Viewed Page - Articles"). I also created the event "Signed Up" that is triggered on the first connection, as well as "Login" and "Logout" to follow in app dis/connection.

## Events lifetime

Events are then sent directly to Google Tag Manager which is a central hub for me. One might also been using Segment for that, but at Elokenz we cannot afford it, so we stick with GTM which is one of the most powerful tool I have ever used.

When your app triggers events and send them to GTM, GTM can trigger internal events, and based on your configuration, launch some scripts (under GTM they're called containers') to forward events and data to remote analytics app. For instance, I might decide to send the event "Created Article" to Mixpanel and not to Google Analytics.

Google Tag Manager can also receive variables from your frontend. So you might send some extra data with each event, or separately. For instance, you can send the username, user email and user age as separate variables (they won't change during the current session). You could also send the number of updated fields during a PATCH, or the title of the article created during the POST (this might not be very useful, but it's to provide some example).

## Events required for most marketing apps

Most of the time you will need to _identify_ your user (send username/email as data) and you'll need to send the current visited page. Everything else is up to you.




<img src="/images/posts/2016/patents/fork_in_road.jpg"><center><i>To patent or not to patent when you are a young software startup</i></center>

## Startups karma and Patents
When you are a young startup, on a low budget, your most valuable assets are :

* Your team
* Your founders motivation
* Your startup ideas

Your **ideas** will help to **define your startup** (market segment, market pain, growth strategies) and to **build your product** (features, algorithms, interfaces).

In order to progress, you will have to **reveal some ideas little by little**. For instance, as you try to confirm that your market segment is valid, you will set up some targeted messages and see if it resonates out there. By doing this, competitors on this segment might hear about you. Another example, if you have an idea for a fancy interface, publish it. If it gets popular, chances are that **someone tries to replicate it on his own product**.

## The Pros and Cons of a patent for a small startup

What's [good](https://www.linkedin.com/pulse/20141203055818-39381830-intellectual-property-rights-awareness-a-must-for-all-start-up) and what's [bad](http://www.entrepreneur.com/article/269495) if you are a software startup and file a patent ?

### Reasons to file a patent

1. **Entry barrier** : If you own a patent, your idea might be less prone to copycat versions. Since you, in theory, should be the only one who has the right to exploit the ideas claimed in the patent, you create an **entry barrier** .

2. **Get better initial funding deals** : A patent gives a tangible value to your intellectual property. If your startup is raising funds, this is an important asset that increase the positive signals investors can receive from your application. Patent possession allows to [reduce the information asymmetry](http://startupticker.ch/en/news/march-2015/patents-and-their-impact-on-the-fundraising-success) between a startup and investors, therefore [allowing better deals in average](http://www.oecd.org/site/stipatents/5-3-Patents-signal.pdf).

3. **Marketing/sales pitch** : Intellectual Property is a **marketing tool**. You can promote your patent portfolio to your prospects and get notified easier.

4. **New revenue stream through licensing** : Licensing is the fact of granting a license to another company to allow an activity based on your patent. In some cases, licensing is the main source of revenues. However, most of the time, this is rather an optional source of revenue.

5. **Protection against lawsuits** Avoiding patent infringement and lawsuits. If you want to avoid the [hassle of going to a court](http://www.bothsidesofthetable.com/2015/05/10/why-your-co-founder-may-just-sue-you/) about the technology you use, a patent can be a good protection. One of the reason is that, to file a patent, you need to look for any other possible infringement you might already be doing. A patent won't be granted if you are reusing someone else's idea. This step will allow you to adjust your internal processes.


---

Credit : Teaser photo by [Henrik Lehnerer](https://marketplace.500px.com/hlehnerer)
