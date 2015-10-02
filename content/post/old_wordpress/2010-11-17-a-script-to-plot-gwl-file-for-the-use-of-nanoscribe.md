---
title: A script to plot GWL File (for the use of Nanoscribe)
author: Jice

date: 2010-11-17
url: /2010/11/a-script-to-plot-gwl-file-for-the-use-of-nanoscribe/
#image:
#  - images/posts/oldwordpress/uploads/2010/11/describe1.png
categories:
  - Python
  - Sciences
tags:
  - nanoscribe
  - nanotechnology
  - physics
  - python
---
<img class="alignleft size-full wp-image-1121" style="margin-left: 10px; margin-right: 10px;" title="describe - nanoscribe language GWL" src="/images/posts/oldwordpress/uploads/2010/11/describe1.png" alt="describe - nanoscribe language GWL" width="106" height="105" >The focus of this article is really small. It will only interest people involved in Research, who own a <a title="Nanoscribe" href="http://www.nanoscribe.de/" target="_blank">Nanoscribe</a> device.

I was a little bit annoyed by the software, very heavy, and running only on windows. I wanted to design my structures on Linux (or any plateform actually), and I wanted to plot the result with a light software.

I programmed a small script in Python to plot **2D structures written in gwl**. In order to run it, ou need to have Python 2.6, Matplotlib and SciPy (in order to have Numpy functions). You also have to use the preamble module I use and which is also included in the archive.

To use it, put the module, the script and the GWL file in the same folder. Then modify the script and include the name of your gwl file. Finally, open a consol, and type :

<pre>python plot_gwl.py</pre>

You can modify and improve this small script, and I would be happy to see the modifications (probably 3D would be a good step forward).

Download the archive : [Plot_GWL.1.0.zip](/images/posts/oldwordpress/uploads/2010/11/Plot_GWL.1.0.zip) (contains the script to plot and the module)

 

_Edit_ 22 Nov. 2010 : I implemented the **3D visualization** . The same command is required to use it (modify line 26  _&#8220;open(&#8216;your_filename.gwl&#8217;,&#8217;r&#8217;)&#8221;_ ) . Comments have been added to help you understading the script. A future addition will take in account an input parameter (instead of modifing the script every time to tell it which file to plot).

Download the new archive : [Plot_GWL.1.1.zip](/images/posts/oldwordpress/uploads/2010/11/Plot_GWL.1.1.zip)

Example of a 3D plot :

<p style="text-align: center;">
  <a href="images/posts/oldwordpress/uploads/2010/11/tour_eiffel.png"><img title="tour_eiffel" src="/images/posts/oldwordpress/uploads/2010/11/tour_eiffel-300x222.png" alt="Tour Eiffel with Nanoscribe" width="300" height="222" ></a>
</p>

 [1]: file:///tmp/moz-screenshot.png
 [2]: images/posts/oldwordpress/uploads/2010/11/Plot_GWL.1.0.zip
 [3]: images/posts/oldwordpress/uploads/2010/11/Plot_GWL.1.1.zip