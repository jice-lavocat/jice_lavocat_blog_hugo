---
title: Yootheme Zoo – Modifying the Frontend submission editor
author: Jice

date: 2011-03-16
url: /2011/03/yootheme-zoo-%e2%80%93-modifying-the-frontend-submission-editor/
Image: http://www.yootheme.com/images/stories/top/home/zoo.png
categories:
  - Informatique
tags:
  - Joomla
  - Zoo
---
[<img class="size-full wp-image-1212 alignleft" alt="zoo joomla module" src="/images/posts/oldwordpress/uploads/2011/08/zoo.png" width="150" height="120" >][1]A quick note to let you know how I hacked Yootheme Zoo 2.3. I wanted to have a wysiwyg editor while my users were submitting article in frontend with ZOO. Usually you can activate the &#8220;trusted mode&#8221; to have this wysiwyg editor. But you will also have several other fields which are too much for normal users. In order to have a wysiwyg editor, even in the non-trusted mode, here is the modification you should implement.

&nbsp;

Here is the trick. Activate the trusted mode, but then, made a code modification to hide the &#8220;administration&#8221; panel in frontend. Here is the code you have to change on **line 40** in **_/joomla\_base\_dir_/components/com\_zoo/partials/\_submission.php**** __**

[cc lang=&#8221;php&#8221;]echo $this->partial(&#8216;administration&#8217;);[/cc]

should be commented :

[cc lang=&#8221;php&#8221;]// echo $this->partial(&#8216;administration&#8217;);[/cc]

[Edit] The old hack was the following<span style="text-decoration: line-through;"><br /> </span>

<span style="text-decoration: line-through;">Here is the line you have to change on<strong> line 265 </strong>in <strong><em>/joomla_base_dir</em>/administrator/components/com_zoo/elements/textarea/textarea.php</strong><strong><em> </em></strong></span>

<span style="text-decoration: line-through;">[cc lang=&#8221;php&#8221;]if ($trusted_mode) {[/cc]</span>

<span style="text-decoration: line-through;">should be transformed to</span>

<span style="text-decoration: line-through;">[cc lang=&#8221;php&#8221;]if ($trusted_mod || !$trusted_mode) {[/cc]Or some other modification on the &#8220;if&#8221; instruction.That&#8217;s it, you are done with the hack.</span>

 [1]: images/posts/oldwordpress/uploads/2011/08/zoo.png
