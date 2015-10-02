---
title: How-to fix Ja_News module’s auto-resize problem?
author: Jice

date: 2009-11-02
url: /2009/11/how-to-fix-ja_news-modules-auto-resize-problem/
categories:
  - Informatique
tags:
  - JA News
  - Joomla
---
<h2 style="text-align: justify;">
  <img style="margin: 20px; float: left;" src="/http://www.joomlart.com/templates/default/images/logo.gif" alt="Joomlart" width="200" >The problem
</h2>

<p style="text-align: justify;">
  During a long time I encountered this problem using the Joomla&#8217;s module JA_News. When I wanted to use the auto-resize functionality, a problem line appeared preventing me to use it in frontend. The warning said :
</p>

<p style="text-align: justify; padding-left: 30px;">
  <strong>Warning</strong>: imagejpeg() [function.imagejpeg]: Unable to open &#8216;www/images/resized/images/stories/path_to_image/image.jpg&#8217; for writing: No such file or directory in <strong>www/modules/mod_janews/helper.php</strong> on line <strong>138</strong>
</p>

<p style="text-align: justify;">
  Depending on your Janews module, the line in helper could be different.
</p>

<p style="text-align: justify;">
  I searched across many forums without any concrete solutions. The only facts which came again and again were related to permissions (put your image folder in 777 and image files in 666) but it didn&#8217;t change anything in my case.
</p>

<p style="text-align: justify;">
  I finally found a <a title="Joomla News problem" href="http://www.joomlart.com/forums/showthread.php?t=14923" target="_blank">post on the Joomlart forum</a> saying that the problem was <strong><em>case sensitive</em></strong>. So the fix for the problem was easy.
</p>

<h2 style="text-align: justify;">
  How to fix it?
</h2>

<p style="text-align: justify;">
  In order to fix the module, just search through your file <strong>/modules/mod_janews/helper.php</strong> and look for a line looking like :
</p>

<p style="text-align: center;">
  <code lang="php">$rzname = strtolower(substr($image, 0, strpos($image,'.')))."_{$tn_width}_{$tn_height}.{$ext}"; // get the file extension</code>
</p>

<p style="text-align: justify;">
  In order to fix the problem, you just have to remove the <strong>strtolower</strong> function. It has no use there and prevent the function to work properly. Your new line should look like :
</p>

<p style="text-align: center;">
  <code lang="php">$rzname = (substr($image, 0, strpos($image,'.')))."_{$tn_width}_{$tn_height}.{$ext}"; // Jice fixed version</code>
</p>

<p style="text-align: justify;">
  If you have time, don&#8217;t forget to signal the bug to Joomla Art, I didn&#8217;t have time to do it, but it can help future users.
</p>