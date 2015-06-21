---
title: Nohup, Comsol and Matlab
author: Jice

date: 2010-06-07
url: /2010/06/nohup-comsol-and-matlab/
categories:
  - Informatique
tags:
  - Comsol
  - matlab
  - nohup
---
<p style="text-align: justify;">
  When you want to use a <strong>Matlab </strong>script to perform simulations with <strong>Comsol</strong>,  a remote server is often used. This post is a quick note to help you creating matlab scripts that would be run on a remote server.
</p>

<p style="text-align: justify;">
  The strategy is the following. We will use the <em>nohup </em>command to let the server do the simulations while we will turn off our computer. Without the nohup, turning off your computer would result in breaking the <strong>ssh connexion</strong>, and thus, the matlab/comsol processes that were running. Another solution could have been the use of the command <em>screen</em>.
</p>

<p style="text-align: justify;">
  First you have to be sure that you Matlab script won&#8217;t output graphical windows which would need X to be printed. If such windows appear during your calculation, then the script would have to stop. In order to prevent java windows to be created, add this at the beginning of your Matlab script :
</p>

  * flreport(&#8216;off&#8217;)

Second, you have to force your script to close the matlab process after the simulation. So you have to add this at the end of your script :

  * exit

Now, you just have to create a directory for your simulation of the day, upload all your script&#8217;s files, and launch the following command via a terminal when you&#8217;ll be located in your simulation&#8217;s folder :

  * nohup comsol matlab -ml -nodesktop -ml -nosplash -mlr &#8220;Script_matlab&#8221; &

&nbsp;

**<span style="text-decoration: underline;">Note</span>** : here we assumed that the script was called _Script_matlab.m_. Be carefull, and don&#8217;t forget to remove the extension &#8220;.m&#8221; when you use nohup.