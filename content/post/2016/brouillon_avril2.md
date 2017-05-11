+++
date = "2016-04-15"
title = "brouillon avril 2"
image = "/images/posts/2016/blue_planet/the-blue-planet.jpg"
tags = ["science", "colors", "light"]
+++

lazy = startup ideas
visibility challenge summary
demo product
lean startup strategy + yves peynaud
push notification introduction

repost steps before first users : yves peynaud
meilleurs ou pires surprises durant la création de repost

---

# so we made up a landing page.. now what ?


I have been a great proponent of landing pages to validate business ideas and key concepts. I got really convinced about their potential after reading Will Mitchell's post [3 steps to validate your business ideas for free](http://startupbros.com/3-steps-to-validate-your-business-idea-for-free/). I've created landing pages using all kind of tools like Unbounce, Wishpond or custom html.

## Validate hypothesis with landing pages

When you design a landing page, you need a purpose, you need an hypothesis to validate. Be it the name of a product, a content tone, a price, a value proposition (more generally a product idea). The way you validate your idea is by collecting **leads** : emails or contact information of interested persons. The expected confirmation might be different in function of your purpose.

If you want to know if a product idea is worth developing, you might just count the conversion rate of your landing page. The conversion rate is an easy metric to collect. Conversion Rate =  Total leads / Total visitors (x 100 if you want percentage). This is mainly what I'll discuss in the rest of this post.

If you want to decide which logo or product name is better, then you need to run multiple variations and compare the conversion rate (CR) of both variations. The higher CR wins. This method is often called AB Testing. In a previous post, I already described [how to decide for the name of a product (or a logo) using AB Testing](http://jice.lavocat.name/blog/2013/05/30dstart-day-4-startup-name/).

I am now taking our personal example at [Repost](http://repost.elokenz.com). We made a multi page landing, where visitor first discover the concept, then IF they are interested they might check the pricing page and IF it seems correct to them, want to register. We are therefore testing two assumptions here, the concept and the pricing. However, we're not collecting emails everytime, so tracking and measuring get a bit tricky.

## Do's and Do's for landing pages

Well, I wanted to keep this section short, but as the writing went on, I realized that many points seemed important to me. So, sorry for the length here... you can just skim through the titles to pick the information you need. You'll find tips and apps to help you get the most out of your landing pages.

### Read some starting material

Before starting, I always recommend people to read Unbounce's [conversion centered design](http://unbounce.com/conversion-centered-design-guide/) white paper. It gives you very important insight on how to get started.

### Ask for feedback

Landing pages design is an art : it's not something you can master in few days. It requires a lot of trials and errors, and you need to practice in order to get some result. Also, as any creation, you can ask for feedback from experts and they'll teach you a lot.

###  Always be testing

Even if you are just testing an idea, you should have some AB Tests running on your page, to improve your CR. Your AB tests might be there to optimize your call to actions, your value proposition, colors, ... whatever. Since you will probably be paying for the traffic on your landing page, you'd want to have the lowest cost of acquisition possible.

AB tests are native in the app if you use some landing page application. If not, you might want to give a shot at premium tools such as [VWO](https://vwo.com/), [Optimizely](https://www.optimizely.com) and the tons of [existing alternatives](http://alternativeto.net/software/optimizely/). If you are on a tight budget, you should consider using [Google Experiments](https://developers.google.com/analytics/solutions/experiments) : this solution is free but requires much more development time and (as always with Google products) the documentation is somewhat obscure. Though I'm using it right now, I don't recommend Google Experiments for the amount of headache it'll give you.

### Watch your funnels

Landing pages can have single or multiple pages. Most of the time you should prefer the first case for the sake of simplicity and for a higher CR. But in some cases you will want to ask your visitor to make several decisions, therefore you need multiple pages. This always leads to lower conversion rates : the more pages you have, the more distracted your visitor will be, and the more tempted to leave he'll be.

So, try to restrict yourself to single pages. In case of a single app landing page, tracking is easy, you only have a single conversion point to watch.

However, if you really can't do otherwise, in case of a multi-page landing, your visitor will need to progress along a decision tree. This navigation if called a **funnel**. You will need to track the CR at every step. You might discover that one step is harder than others and you are losing your prospects here.

Again, you have dozens of tools to do funnel analytics. Some solutions, like [Kiss Metrics](https://www.kissmetrics.com) or [Mixpanel](https://mixpanel.com/), are very expensive and dedicated to e-commerces or big applications. Some others are made for smaller applications such as landing pages : [Hotjar](https://www.hotjar.com/), [MouseFlow](https://mouseflow.com), [ClickTale](https://www.clicktale.com)... the list extends much more.

The free solution if offered in Google Analytics. KissMetrics offers a useful [starter guide about google analytics](https://blog.kissmetrics.com/conversion-funnel-survival-guide/).

### Don't mess with javascript

If you don't know about coding, you will prefer all in one Landing Page applications such as already cited [Unbounce](http://unbounce.com/), [LeadPage](http://www.leadpages.net) or [Wishpond](https://www.wishpond.com/).

However, if you want to do it by yourself, since you are going to add a lot of external scripts (analytics, conversion tracking, pixel trackers, funnel analysis, ab testing, ...), you will need to quickly insert few javascript lines every time. In order to save some time and get a better workflow, I suggest you to use a script container such as [Google Tag Manager](https://www.google.com/analytics/tag-manager/) or [Segment](https://segment.com/). As an exception, here, I suggest you to use Google Tag Manager (GTM) instead of other alternatives. Thoug the documentation, agin, is troublesome, the tool is really powerful and will give you a strong control over the script and event you might be tracking on your page.

These tag managers works in the following way. Instead of adding a new line of javascript on your website every time you want to use a new marketing application, you just need to have the tag manager script on your website installed by your webmaster once. Then, everything happens onto the tag manager website, and you don't need to modify your source code anymore. If you hired a webmaster for the landing page, this prevents additional cost for minor modifications.

### Don't forget tracking pixels

Many of your landing pages will receive traffic from online advertising channels : [adwords](http://www.google.com/adwords/), [facebook ads](https://www.facebook.com/business/products/ads), [twitter ads](https://ads.twitter.com/), ...
To optimize the CR and to optimize the cost of acquisition of new leads these platforms always offer you the possibility of inserting a conversion pixel on your page. A conversion pixel is a small hack that allows a remote website to get information about your visitor without the need of javascript. If you are interested about that, you might find an old post I wrote (in French) about how to [create your own conversion pixel](http://jice.lavocat.name/blog/2009/06/cookie-stuffing-and-click-hidding/) for (growth) hacking purposes.

Even if you are not using Facebook ads for the moment, you will benefit from installing the pixel from the start. This will allow you to get some feeling about your audience later on, by using [Facebook audience insight](https://www.facebook.com/business/news/audience-insights).

Adwords or Twitter conversion pixels are optional and you should install them only if you use these channels.

## Sending traffic to your landing page

Now that you have a purpose for your page and tools to track your result, you need to bring some traffic there. Several channels are available with different strategy each time. If your landing page is just used to test an idea (not to sell a product or to get leads with a long term campaign), you might prefer quick paid solutions. Instead, if you're trying to sell something time might not be the first issue, so you might prefer slower solutions like SEO and content marketing.

The book *Traction* by Gabriel Weinberg and Justin Mares gives a broad overview of what acquisition channels can be used. Here's a quick landscape summarizing their framework :
https://s-media-cache-ak0.pinimg.com/736x/1e/5a/11/1e5a117621fc2a4d8e49010ff0734114.jpg

For our [Repost](http://repost.elokenz.com) landing page, we have decided to use three channels to test the idea :

* Facebook ads : targeting social media professionals
* Content marketing : writing blogpost and providing content about web visibility
* Email marketing : cold emailing using applications such as prospect.io

We haven't started yet, but we commited ourselves to describe what we do and if it works, so if you subscribe to our newsletter, you will receive our news about how it goes.

## Goal, Measure, Traffic

As a conclusion, remember that you need these 3 points in order to have a relevant landing page campaign :

1. A goal : an hypothesis that you want to track
2. A measure : get a tool to measure your success
3. Some traffic : send some relevant traffic to your page

As a side note, since I find the whole process really interesting , I created a small service called Jetlead to [assist you to create your landing page](http://jetlead.help/). The webpage is only available in French, but if you require some help, don't hesitate to contact me via the above-mentioned website. I'll be happy to help you.


---

### Facebook ads
preparing audience, text and budget

### Content marketing
Writing blog weekly, sending two newsletters, visibility challenge. Trying to add links to repost each time

### Email marketing
finding prospects, preparing cold email, tracking opening and clicks
