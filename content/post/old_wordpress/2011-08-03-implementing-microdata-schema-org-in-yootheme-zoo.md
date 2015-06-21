---
title: 'Implementing microdata schema.org in  Yootheme ZOO'
author: Jice

date: 2011-08-03
url: /2011/08/implementing-microdata-schema-org-in-yootheme-zoo/
Image:
  - /images/posts/oldwordpress/uploads/2011/08/schema-org-logo1.jpg
efs_price:
  - 5.00
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
tags:
  - Joomla
  - Schema.org
  - web sémantique
  - YOOtheme
  - Zoo
---
<p style="text-align: justify;">
  <a href="/images/posts/oldwordpress/uploads/2011/08/schema-org-logo1.jpg"><img class="alignleft size-full wp-image-1211" style="margin: 0pt 10px;" title="schema-org-logo" src="/images/posts/oldwordpress/uploads/2011/08/schema-org-logo1.jpg" alt="" width="128" height="80" /></a>Recently, the three major search engins (Bing/Yahoo and Google) agreed on using the<strong> microdata system</strong> <a href="http://schema.org/">Schema.org</a>. This allow any website to provide <strong>semantic information</strong> to the <strong>search spiders</strong>. For instance, you can specify<em> what kind of content you are publishing</em>, like a recipe of an apple pie, or a movie review. More than that, depending on the type, you can give the various important information directly to the search robot : what is the movie title, what is its director, or how long you should cook your pie. To find all the piece of information you can select, you should read : <a href="http://schema.org/">http://schema.org/</a>
</p>

<p style="text-align: justify;">
  <a href="/images/posts/oldwordpress/uploads/2011/08/zoo.png"><img class="alignright size-full wp-image-1212" title="zoo" src="/images/posts/oldwordpress/uploads/2011/08/zoo.png" alt="" width="150" height="120" /></a>As a Joomla fan, and <a href="http://www.yootheme.com/zoo/">Yootheme ZOO</a> frequent user, I had to implement this for my websites. I made a custom set of elements that allows me to provide schema.org names to my text fields. The change will add a new configuration field to your text / textarea / image inputs, and you will be able to add microdata properties to your object. This is very versatile and very easy to use.
</p>

<p style="text-align: justify;">
  You can download it straith away, or read the &#8216;readme&#8217; file below to get an idea of the product :
</p>

<p style="text-align: justify;">
  [easyfileshop id=1202]
</p>

<p style="text-align: justify;">
  <em>Tested only with <strong>Zoo 2.4 for Joomla 1.5</strong></em>
</p>

<p style="text-align: justify;">
  <em>You can try it for free if you have an existing working platform Joomla 1.6 with ZOO 2.4 installed. You should contact me directly and I&#8217;ll send you the file. You&#8217;ll tell me if some bugs are present, and you&#8217;ll help the community.</em>
</p>

 

<h2 style="text-align: left;">
  Read Me File
</h2>

\*\* Schema.org implementation under Yootheme ZOO component \*\*  
Author : Jean-Christophe Lavocat  
Email : jice@nauka-websites.com  
Date : July 2011  
\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\****

## Introduction

Add a new option to the text and image fields of ZOO. This new option helps to give a context to the content types you create by using ZOO. For example : your create a recipe content type, it could give the following information : <http://schema.org/Recipe>.

## Installation

Browse your website installation, and go to the ZOO application that you want to update. The installation have to be done application by application. For instance, if you are using the application &#8220;Blog&#8221; got to : &#8220;joomlabase/media/zoo/applications/blog&#8221;. You should unzip the folder &#8220;elements&#8221; there.

Go to your administration panel and check which template you are using for your content type. Remember this template name as &#8220;templatename&#8221;. You should then go to &#8220;joomlabase/media/zoo/applications/blog/templates/templatename/&#8221; and unzip the folder &#8220;renderer&#8221; there.

The new architecture should add the following folders.

/applications/blog/   
elements/   
&#8230;/

/applications/blog/template/templatename/renderer/   
/element/   
&#8230;

Finally, go to the view you want to include schema.org : probably it will be the &#8220;full&#8221; view. Go to &#8220;/joomlabase/media/zoo/applications/blog/templates/templatename/renderer/item&#8221; and open &#8220;full.php&#8221;. You have to manually add the good schema type at the beginning of the file, and close it at the end. Suppose you are displaying a recipe, put the line :

<pre>&lt;div itemscope itemtype="http://schema.org/Recipe"&gt;</pre>

in the first html output (say, after the first &#8220;?>&#8221;). Add a &#8220;</div>&#8221; at the very end of this file :

<pre>&lt;/div&gt;</pre>

## Configuration

Go to the setting of your content type in the administration panel. Edit the fields of the view you just modified.   
You should now be able to :  
1) give a schema.org label to all the text field  
2) give a schema.org label to the main title, or specify if it is an author profile page.  
3) add a default picture label to one of your picture  
4) give the label &#8220;url&#8221; to the links

 

 

<div id="attachment_1214" style="width: 310px" class="wp-caption alignright">
  <a href="/images/posts/oldwordpress/uploads/2011/08/schemafield.png"><img class="size-medium wp-image-1214" title="schemafield" src="/images/posts/oldwordpress/uploads/2011/08/schemafield-300x245.png" alt="" width="300" height="245" /></a>
  
  <p class="wp-caption-text">
    A new "Schema.org Label" appears now, where you can specify your content
  </p>
</div>

 

## Verification

To verify your item pages, copy paste their url to :   
http://www.google.com/webmasters/tools/richsnippets

## Help / Troubleshootings / FAQ

Any questions should be sent to jice@nauka-websites.com. You should specify in your email :  
1) which version of ZOO you are using  
2) the description of your problem  
3) the URL where the error is visible

 

The files are available to download on the following link :

[easyfileshop id=1202]

_Tested only with **Zoo 2.4 for Joomla 1.5**_

_You can try it for free if you have an existing working platform Joomla 1.6 with ZOO 2.4 installed. You should contact me directly and I&#8217;ll send you the file. You&#8217;ll tell me if some bugs are present, and you&#8217;ll help the community._