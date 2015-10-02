---
title: 'How-to : Make a SEF image-map navigation system with Joomla'
author: Jice

date: 2010-02-09
url: /2010/02/how-to-make-a-sef-image-map-navigation-system-with-joomla/
Image:
  - images/posts/oldwordpress/uploads/2010/02/joomla-symbol-color.png
categories:
  - Informatique
  - SEO
tags:
  - breadcrumb
  - image map
  - Joomla
  - LinkR
  - menu
  - SEF
  - SEO
---
<p style="text-align: justify;">
  You always wondered how to create a navigation system with an image? Nothing could be easier; just use the <a title="Image Map" href="http://www.w3.org/TR/REC-html40/struct/objects.html#h-13.6" target="_blank">image map property</a> of html.
</p>

<p style="text-align: justify;">
  But, obviously, it gets a little bit trickier when you have to add several links to an image. Moreovre, people are nowadays using a lot of  Content Management Systems (CMS) to help in developping websites. I personnaly use <a title="Joomla - CMS" href="http://www.joomla.org/" target="_blank">Joomla</a> a lot, and this article will explain how to add an efficient Search Engine Friendly (SEF) Image Map navigation system for Joomla.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<h2 style="text-align: justify;">
  Creation of Image Map
</h2>

In order to easily create image maps with Joomla, I installed a plugin for TinyMCE. You can find it on it&#8217;s <a title="Image Map" href="http://code.google.com/p/imgmap/" target="_blank">google project&#8217;s page</a> a version for :

  * <a title="Plugin Image Map for Tiny MCE" href="http://code.google.com/p/imgmap/wiki/Joomla_setup" target="_blank">Tiny MCE</a>
  * <a title="Plugin Image Map for FCK" href="http://code.google.com/p/imgmap/wiki/FCKEditor_setup" target="_blank">FCK</a>

In order to use it, just follow their instructions for installation, and, when you edit an image, click on the new button that has been created. It will open the imagemap plugin.

## Creation of a menu system

<p style="text-align: justify;">
  <img class="alignleft size-full wp-image-1023" style="margin: 0px 20px;" title="content-management-system-joomla-free" src="/images/posts/oldwordpress/uploads/2010/02/content-management-system-joomla-free.png" alt="Joomla Menu System" width="185" height="171" >In order to have a coherent navigation system with Joomla, I mean, to have a coherent SEF strategy, you have to create a unique link for each page.  In order to have a unique link for your content, the only solution is to use Joomla&#8217;s menu system. If you need to create two links for the same item, use an &#8220;<strong>alias</strong>&#8221; for the second one, in order to <strong>prevent duplicate URLs</strong>.
</p>

<p style="text-align: justify;">
  You could have avoided this menu creation if you don&#8217;t care about Search Engine Optimization (SEO), but my recommandation would be to follow the following steps.
</p>

<p style="text-align: justify;">
  This trick (of always using Joomla&#8217;s menu system) will allow you to publish <strong>coherent and working breadcrumbs</strong>. You won&#8217;t have the famous <a title="Joomla Breadcrumbs and Categories" href="http://forum.joomla.org/viewtopic.php?f=47&t=372518" target="_blank">menu vs category dilemma</a>.
</p>

<h2 style="text-align: justify;">
  Creation of links from article to Joomla content
</h2>

The creation of SEF links with google when the SEF option is activited is not always obvious. The first trick that came in mind is to use the research tool, or to copy a link from a menu. But these options fails if our navigation system is an image and not a menu. If you unpublish the menu, the link won&#8217;t appear. If you change an alias for a menu-item you will loose the link you put in your article.

The only solution is to put a link which is not SEF. So you could unable the SEF option, copy/paste a link and activate the SEF option again. But it&#8217;s quite annoying for a hundreds of links isn&#8217;t it? So, we will use a famous plugin for that. This plugin allow you to create a link to articles in your Joomla! site when you are creating content. This plugin is called <a title="LinkR" href="http://extensions.joomla.org/extensions/structure-a-navigation/site-links/4010" target="_blank">LinkR</a>.

To use it : after the installation, when editing your article, you&#8217;ll see a new button bellow your article (<a title="Demo of LinkR" href="http://j.l33p.com/linkr/demo" target="_blank">click for a demo</a>).

<span style="text-decoration: underline;"><strong>IMPORTANT :</strong></span> In order to use the trick of &#8220;menu system&#8221;, when you create a link with LinkR, don&#8217;t select an artcile (by clicking on &#8220;Article&#8221;) , but instead, the menu item you created (by clicking on &#8220;Menu&#8221;), and which is linked to the article.

## Make everything working smoothly

<p style="text-align: justify;">
  So, you have everything installed and tested? Right, let&#8217;s go for the creation process!
</p>

  * First, create your page with the image which will be your navigation system. Make a link from the menu, in order for it to be accessible.
  * Second, create your content, and for each page, a link from the menu. It could be an hidden menu, so your visitors will only see the navigation image (in my case I put everything on the main menu, but the template doesn&#8217;t show more than one sub-menu hierarchy). But, when you create your content, **be careful** and use the &#8220;child property&#8221;, to get SEF URLs like &#8220;_http://www.mysite.com/parent-menu/parent2/item_&#8220;.
  * Third, come back to your article with the image, and create (temporary) text links to your content, by using LinkR, and pointing to the menu items, and not the article items. Copy the URL that has been created. It should look like : _index.php?option=com_content&view=article&id=23&Itemid=30_ and nothing else.
  * Edit your image, create your links map, and for the link, use the URL you just copied from the (temporary) text links.
  * Finally you can choose to keep the text links or to remove it. I choosed to keep them to help my visitors who can&#8217;t see images. And it&#8217;s a safety measure in the case your image won&#8217;t show up.

## Enjoy

It&#8217;s done. You can check that your image maps to SEF Url, that the links are going to your articles (specified by the menu), and that, if you change the menu link alias, the URL of your article will change coherently.

Moreover you can use breadcrumbs {{<img src="http://localhost/oldblog/wp-includes/images/smilies/icon_biggrin.gif" alt=":-D" class="wp-smiley" >}}

<p style="text-align: center;">
  <strong>A demo on one of my website : <a title="Liste de spots en Corse : Corsica Windsurf" href="http://www.corsica-windsurf.com/fr/windsurf/spots-corse" target="_blank">http://www.corsica-windsurf.com/fr/windsurf/spots-corse</a></strong>
</p>

Don&#8217;t hesitate to comment to ask precisions.

In addition you can use a very powerful extension, but probably not easy to use for a large amount of links : <a title="HTMLMap Manager" href="http://extensions.joomla.org/extensions/style-a-design/design/7332" target="_blank">HTMLMap manager</a>