+++
date = "2018-01-17"
title = "Google Analytics - Real-time sound notification on new visitors"
url = "2018/google-analytics-real-time-sound-notification/"
image = "/images/posts/2018/ga_play_sound/google_analytics_live_play_sound_alert.png"
description = " In this post you'll find a bookmarklet that allows you to hear a sound notification whenever you have a new visitor showing up in your Real-Time Google Analytics view."
tags = ["science", "colors", "light"]
+++

Have you ever wanted **Google Analytics to play a sound when a new visitor hits your site**? Look no further, I have a small script for you.

While I was debugging a project's Google Analytics settings recently, I wondered if I could have a warning about when a new visitor visited the website while I was doing something else. I came up with a [bookmarklet](https://en.wikipedia.org/wiki/Bookmarklet) that gives superpowers to your GA setup.

I will teach you here how to do it step by step, but if you are just interested in the bookmarklet, you can get it in the [last section](#play-a-sound-in-google-analytics-when-a-new-visitor-hits-your-site-bookmarklet).



## Explanation

The whole idea relies on **observing changes on Google Analytics real-time view**. One can look for change on the Visitor Count DOM element, and trigger a javascript event when it updates. The whole scenario can be played in your **browser's developper tab**. Here is the code to do that, explaination follows.

<script src="https://gist.github.com/tanzaho/5fbac33b9bb58251b2bfa96f04be811f.js"></script>

The first line lets you change the audio file you might want to use.
Then, we initalize `mActiveUsers` the count of active users on your site.
The setInterval function allows you to run repeatedily the function `getActiveUsers` at a 1000 millisecond interval.

Finally, the function will get the DOM element `ID-overviewCounterValue` (it's the ID from the big counter in GA - see picture below) and turn the string value to an integer.

If the count is greater than the previous value, we play a sound.

Then, at the end of the loop, we update the current active user value.

<img src="/images/posts/2018/ga_play_sound/google_analytics_real_time_div_id.png" />


## How to use this script ?

Browse Google Analytics to access the site you want to monitor, and visit the **Real-Time > Overview** section. The URL should now start by something like `https://analytics.google.com/analytics/web/#realtime/...`

Once you are on this page, you need to open your browser's console (if you don't know what and how to do it, Google it). You now just have to copy/paste the script in the input area (usually at the bottom of the console).

Now, open another tab and visit your website. If everything works, you should now hear a sound when the Real-Time counter updates.


## Turn JS into a bookmarklet

Running a script in this fashion is pretty annoying. It takes time, you need to save the code somewhere, then copy/paste it each time. There should be a better way to do this.

And, indeed there is. The magick comes through the use of a **bookmarklet**. They are not so popular these days, but a few years back, many people where using bookmarklets instead of plugins (for instance, to share on social networks).

### What is a bookmarklet?

A bookmarklet is like a classical link, but instead of visiting a target URL, **when you click on it, it will run javascript in your browser**... exactly as we did while using the console. The advantage here, is that you can bookmark bookmarklet (hence the name), so you can keep your scripts very accessible and run them quite easily.

To create a bookmarklet, it's very simple, you just need to prepend `javascript:` to your custom code. Here is an example, click on the following link to <a href="javascript:alert('Hello World');">print Hello World</a>.

The code is really simple : ```<a href="javascript:alert('Hello World');">print Hello World</a>``` .

### Get faster with bookmarklet generators

To create your custom bookmarklet, I advise you to use bookmarklet generators, [here is one](https://mrcoles.com/bookmarklet/). They will do all the dirty job for you (minifying, importing useful libraries like jquery, ...).

This is what I used to create the bookmarklet I'm sharing in the following section.

## Play a sound in Google Analytics when a new visitor hits your site: bookmarklet

So, if you want Google Analytics to play a sound when a new visitor reaches your website, it's very simple:

1. Drag the following link (the blue button) to your browser's bookmarks.
2. Visit Google Analytics : Real-Time > Overview section
3. In your bookmarks, click the link you saved at step 1.
4. Wait for a new visit, and after a few milli-seconds you will hear a sound.

<center><div ><a class="menu-button" href="javascript:(function()%7Bvar%20url%3D%20%5B%22https%22%2C%20%22%3A%2F%2Fsoundbible%22%2C%20%22.com%2Fgrab.php%3Fid%3D1446%26type%3Dmp3%22%5D.join(%22%22)%3BmCoinSound%20%3D%20new%20Audio(url)%3BmActiveUsers%20%3D%200%3BsetInterval(getActiveUsers%2C%201)%3Bfunction%20getActiveUsers()%7Bvar%20count%20%3D%20parseInt(document.getElementById(%22ID-overviewCounterValue%22).innerText)%3Bif(count%20%3E%20mActiveUsers)%7BmCoinSound.play()%3B%7DmActiveUsers%20%3D%20count%3B%7D%7D)()" style="text-decoration: none; display:inline-block; float:none; background-color: #4A90E2; color: #fff">[GA] Play a sound on new visitor</a></div></center>
<center><i>Drag this link to your favorites' toolbar to save it</i></center>

**How to stop it?**
When you run the script, the script will be kept running inside the opened tab. If you want to stop hearing that bell noise, just close the tab, or refresh the page.

## User Scripts

The initial code has been adapted from a **user script**. I must confess I had never heard about [user scripts](https://greasyfork.org/en) until today. I have not dug deep into it, but I think that basically they are scripts shared from a community, that you can run from your browser after installing an extension. It's a bit quicker than having to type the code in your browser's developper extension.

It's certainly a good alternative to the bookmarklet option. So, if you are a user script user, feel free to leave your comment about these scripts and how you are using them.




---

Credit : Teaser photo by [Jean-Christophe Lavocat](https://jice.lavocat.name)
