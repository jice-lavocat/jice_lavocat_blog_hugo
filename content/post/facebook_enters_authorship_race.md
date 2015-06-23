+++
date = "2015-06-23T14:15:22+02:00"
title = "Facebook enters the authorship race"

+++

For those who know me, you know that I have been terribly impacted by Google's decision to stop promoting the **authorship tag**. This feature gave me the opportunity, at that time, to work toward my first startup project called **Elokenz**.

Google's decision took many people by surprise, and I was very sad the day George Muller [announced it on Google+](https://plus.google.com/u/0/+JohnMueller/posts/HZf3KDP1Dm8).


<center>

<script type="text/javascript" src="https://apis.google.com/js/plusone.js"></script>

<!-- Place this tag where you want the widget to render. -->
<div class="g-post" data-href="https://plus.google.com/+JohnMueller/posts/HZf3KDP1Dm8"></div>
</center>


## Facebook new decision to showcase authors

In a press release published on June 18th, Facebook officially announced that the social network will [support a new author tag](http://media.fb.com/2015/06/18/using-author-tags-to-grow-your-audience/).

<img src="/images/posts/facebook_authorship/melissa-korn-follow.png" />

The tag will add extra information when people share your post on Facebook. You know that exactly what it already does with the thumbnail, the title and summary. You can search about [og:tags](http://ogp.me/) if you are not already familiar with that technology. Tons of plugins exist to have them in your source if you use a wide-public CMS ( [wordpress](https://wordpress.org/plugins/tags/open-graph) , [joomla](http://extensions.joomla.org/extensions/extension?searchall=open+graph&filter[tags][]=&filter[core_catid]=&filter[includes]=&filter[versions]=&filter[type]=&filter[hasdemo]=&order=&filter[newupdated]=&filter[score]=&filter[favourites]=&dir=DESC&limitstart=0&controller=filter&view=extension&layout=list&Itemid=145&clearorders=0&clearfilters=1), ...) 

As you can see on the above picture, the new tag will be displayed under your photo summary and people can start following you. I didn't get if they were following your Facebook profile, or if a new feature was present which would be like a RSS feed for authors (any idea?).

## How to use it on your site ?
It's a great opportunity for bloggers/journalists to showcase their work. So how to turn it on ? Well, it's quite easy as with other OG tags. You just need to add a new line to your meta section. Here is a sample example :

{{< highlight html "style=colorful" >}}
 <head prefix="og: http://ogp.me/ns# fb: http://ogp.me/ns/fb# article: http://ogp.me/ns/article#">
  <meta property="fb:app_id" content="302184056577324" /> 
  <meta property="og:type"   content="article" /> 
  <meta property="og:url"    content="http://jice.lavocat.name/blog/article_slug" /> 
  <meta property="og:title"  content="My Super Sample Article" /> 
  <meta property="og:image"  content="https://s-static.ak.fbcdn.net/images/devsite/attachment_blank.png" />
  <meta property="article:author"   content="https://www.facebook.com/jean.christophe.gomez.lavocat" /> 
{{< /highlight >}}

You can see the last line who is using the *article:author* property. The associated content could either be a URL to your profile, or your facebook id. From the announcement, it also seems that one can use the URL of a facebook page :
	
	Journalists who manage a Facebook Profile will need to ensure “follow” is turned on on their profile. Journalists who manage a Facebook Page do not need to take any additional action steps.

Anyway, my personal opinion about authorship is that human should use it, not organization. There is (at Google) a different tag for that, for a better semantic. So, tagging your article with a Facebook page has less meaning for me.

## What about schema.org ?
Those who have used the Google+ authorship attribution in the past will wonder why their old tag is not already working for Facebook.

There is mainly two reasons : 

* first : with Google, you had to put a link toward Google+, and now you have to put a link toward your Facebook profile (seems obvious right) .
* second : the syntax used by Google was based on the widely adopted [Schema.org](http://schema.org/). Facebook never participated in the development of this syntax. It has its own syntax (Open Graph tags).


## A new era for authors
I am really really glad that Facebook took this move. I am in favor of a better link between content and their creators, and (even if Facebook graph is still an obscure black box) this announcement comes as real positive news.

It might be the occasion for me to start again on the main feature of **Elokenz**.

Thanks for reading my first post in a long long while.

### Additional reading 
The news is not fresh, so you might find other valuable info elsewhere, especially on Social Media Hat' [@Mike_Alton](https://twitter.com/mike_allton) post: [Facebook Adds Authorship. Bloggers Take Note!](http://www.thesocialmediahat.com/news/facebook-adds-authorship-bloggers-take-note-06192015)
