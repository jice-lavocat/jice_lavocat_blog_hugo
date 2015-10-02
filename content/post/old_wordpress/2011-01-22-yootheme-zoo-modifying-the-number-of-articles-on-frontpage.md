---
title: Yootheme Zoo – Modifying the number of articles on Frontpage
author: Jice

date: 2011-01-22
url: /2011/01/yootheme-zoo-modifying-the-number-of-articles-on-frontpage/
Image:
  - http://www.yootheme.com/images/stories/top/home/zoo.png
categories:
  - Informatique
tags:
  - Joomla
  - Zoo
---
[<img class="alignleft" alt="zoo joomla module" src="/images/posts/oldwordpress/uploads/2011/08/zoo.png" width="150" height="120" >][1]A quick note to let you know how I hacked Yootheme Zoo 2.3. I wanted to have a different numbers of articles on the frontpage, and in the classical category view.As I did not find an easy solution (a parameter should be added to the configuration for the front page), I decided to code it.

Here is the line you have to change on **line 232** in **_/joomla\_base\_dir/components/com_zoo/controllers/default.php_**

<pre>[cc lang="php"]// get item pagination 
$items_per_page = $params-&gt;get('config.items_per_page', 15);[/cc]</pre>

should be transformed to

<pre>[cc lang="php"]// get item pagination
$items_per_page = $category_id == 0 ? 3 : $params-&gt;get('config.items_per_page', 15)[/cc]</pre>

## Advanced hack

If you want you can add a new parameter in the configuration to be able to change that number in backend. Here is the code :

In the file_ **joomla\_base\_dir/media/zoo/applications/blog/application.xml**_ add the following new line at **line 22** :

<pre>[cc lang="php"][/cc]</pre>

Modify on **line 232** in **_/joomla\_base\_dir/components/com_zoo/controllers/default.php_** , it should now read :

<pre>[cc lang="php"]$items_per_page = $category_id == 0 ? $params-&gt;get('config.items_per_frontpage', 5) : $params-&gt;get('config.items_per_page', 15);[/cc]</pre>

 [1]: images/posts/oldwordpress/uploads/2011/08/zoo.png