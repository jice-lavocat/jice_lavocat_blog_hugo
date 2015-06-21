---
title: How-to get the electromagnetic scattered far field using Comsol RF Module
author: Jice

date: 2010-04-27
url: /2010/04/how-to-get-the-electromagnetic-scattered-far-field-using-comsol-rf-module/
Image:
  - http://fralbe.files.wordpress.com/2008/05/comsol.gif
categories:
  - Informatique
  - Sciences
  - Scientific Computations
tags:
  - Comsol
  - Electromagnetism
  - Scattered Field
---
<p style="text-align: justify;">
  If you use Comsol Multiphysics &#8211; RF Module, you may have noticed that there is a far field option when you edit any Boundary settings. This feature will allow you to compute the <strong>scattered far field</strong> of an object using some tricks.
</p>

<h2 style="text-align: justify;">
  Initial Setting : Simple simulation using Comsol
</h2>

<p style="text-align: justify;">
  This tutorial will allow you to compute the scattered field of an ideal magnetic conducting circle in 2D. First, let&#8217;s design a square with PML around to absorb the outgoing light. Create a problem using <strong>Plane TM waves</strong> (we will change this latter to scattered TM waves, but the tutorial was made for an initial TM problem, and not for Scattered TM). We will assume you know how to use Comsol as a beginner user, so you know how to design the following structure :
</p>

  * a square centered in (0,0), of length 0.2
  * 4 additional rectangular borders to this square, of thickness 0.02
  * a centered circle of radius 0.01
  * a centered circle of radius 0.8

 

 

 

<div id="attachment_1053" style="width: 310px" class="wp-caption aligncenter">
  <a href="images/posts/oldwordpress/uploads/2010/04/setting_base.png">{{<img class="size-medium wp-image-1053" title="setting_base" src="images/posts/oldwordpress/uploads/2010/04/setting_base-300x220.png" alt="" width="300" height="220" >}}</a>
  
  <p class="wp-caption-text">
    Basic Setting
  </p>
</div>

<p style="text-align: justify;">
   
</p>

<p style="text-align: justify;">
  Now you should modify the design a little bit in terms of properties. First, select the big circle, and transform it to a curve (&#8220;Coerce to curve&#8221;). You should also remove the small circle from the main substrate to latter change its properties. In order to do that, select the small circle and the main square, and click on &#8220;difference&#8221;. Then, add some cartesian PML to the 4 rectangles : <strong>Physics </strong>> <strong>Subdomain settings</strong> > <em>select the areas</em> > <strong>PML</strong> ><strong><em> </em>Cartesian</strong> <em>>  Try to figure out which PML you need to inser</em> (left/righ absorb along <strong>x</strong>, top and bottom along <strong>y</strong>, corners along <strong>x</strong> and <strong>y</strong> directions)).
</p>

<p style="text-align: justify;">
  The following image shows the resulting construction. In order to highlight the construction I changed my <strong>Options </strong>> <strong>Preferences </strong>> <strong>Visualization</strong>, and checked the &#8220;Render Face&#8221; button.
</p>

 

 

 

 

<div id="attachment_1055" style="width: 310px" class="wp-caption aligncenter">
  <a href="images/posts/oldwordpress/uploads/2010/04/Setting_normal.png">{{<img class="size-medium wp-image-1055" title="Setting_normal" src="images/posts/oldwordpress/uploads/2010/04/Setting_normal-300x220.png" alt="" width="300" height="220" >}}</a>
  
  <p class="wp-caption-text">
    Normal Setting
  </p>
</div>

 

## Collecting the Far-Field

<p style="text-align: justify;">
  In order to collect the far field using Comsol Multiphysics, you need to change some &#8220;Physics&#8221; values. First, let&#8217;s explain what will be our simulation case. A plane wave will come from the inner-left boundary of the small square. We will use TM waves, with Hz=1 A (magnetic field) emerging from this inner boundary. So the source is located on <strong>x=-0.1</strong>. We thus need to indicate this to comsol. Go to <strong>Physics </strong>> <strong>Scalar variables</strong> > <em>Change the value of </em><strong>H0iz_rfwh</strong><em> to</em> <strong>exp(-j*k0_rfwh*(x+0.1)).</strong>
</p>

<p style="text-align: justify;">
  Now we need to indicate Comsol that we want to integrate the far field on the big circle we draw during the first step. Modify the <strong>Boundary settings</strong> to add a far fiel value, called <strong>Efar</strong> on the curves representing the circle.
</p>

<p style="text-align: justify;">
   
</p>

 

 

<div id="attachment_1057" style="width: 310px" class="wp-caption aligncenter">
  <a href="images/posts/oldwordpress/uploads/2010/04/Efar.png">{{<img class="size-medium wp-image-1057" title="Efar" src="images/posts/oldwordpress/uploads/2010/04/Efar-300x220.png" alt="" width="300" height="220" >}}</a>
  
  <p class="wp-caption-text">
    Efar is defined on the big circle
  </p>
</div>

<p style="text-align: justify;">
  Note that you just need to write the name of the variable <strong>Efar</strong>, and comsol will automatically create resulting variables.
</p>

<p style="text-align: justify;">
  Next you need to inser a relation to get <strong>Hfar</strong> from <strong>Efar. </strong>Indeed, we are looking at the magnetic field, Hz, and not at Ez. Go to <strong>Options</strong> > <strong>Expressions > Global Expressions.</strong> Add the following expressions :
</p>

  * r : sqrt(x^2+y^2)
  * Hfar : (x/r\*Efary-y/r\*Efarx)*sqrt(epsilon0\_rfwh/mu0\_rfwh)

Now you are almost done. To get a better scattered result, you need to change the way comsol solve the problem. go to **Physics > Properties >** change **Field type** to **Scattered TM.**

You can finally start the solving process.

## Visualizing the scattered far-field

<p style="text-align: justify;">
  You can now visualize the scattered field in the <strong>Plot paramaters</strong> > <strong>Surface </strong>section (Scattered Magnetic Field, z component). Nevertheless, the great feature is that you can now plot an angular far field plot using matlab.
</p>

<p style="text-align: justify;">
  First, in Comsol, <strong>Postprocessing</strong> > <strong>Domain Plot Parameters</strong> > <strong>Line/ Extrusion</strong> > <em>select the big circle&#8217;s curves</em>. In the <strong>y-axis data</strong>, change the expression to <strong>abs(Hfar)</strong>. In the <strong>x-axis data</strong>, select &#8220;<strong>Expression&#8221; </strong>and inser the following expression &#8220;<strong>atan2(y,x)</strong>&#8220;. It is used to display the data along the circle, using an angular representation. Clik <strong>Ok</strong>, you should get something similar to the following.
</p>

 

 

<div id="attachment_1061" style="width: 310px" class="wp-caption aligncenter">
  <a href="images/posts/oldwordpress/uploads/2010/04/Hfar_Comsol1.png">{{<img class="size-medium wp-image-1062" title="Hfar_Comsol" src="images/posts/oldwordpress/uploads/2010/04/Hfar_Comsol1-300x261.png" alt="" width="300" height="261" >}}</a>
  
  <p class="wp-caption-text">
    Hfar using comsol
  </p>
</div>

<p style="text-align: justify;">
  In order to visualize this with Matlab, click on th <strong>ASCII</strong> button, and save the plot data on your computer. Let&#8217;s call it <em>scat_circ.txt</em>. Open Matlab. Import this data : <strong>File > Import Data > </strong><em>select scat_circ.txt (then </em><strong>Next </strong><em>, then </em><strong>Finish</strong><em>).</em>
</p>

<p style="text-align: justify;">
  Now, just use the following command lines :<em> </em>
</p>

  * scat\_data=sortrows(scatt\_circ); 
  * rho=scat_data(:,2); 
  * theta=scat_data(:,1); 
  * polar(theta,abs(rho))

You should get the resulting :

<p style="text-align: justify;">
  <em>
  
  <div id="attachment_1064" style="width: 310px" class="wp-caption aligncenter">
    <em><a href="images/posts/oldwordpress/uploads/2010/04/Hafr_Matlab.png">{{<img class="size-medium wp-image-1064" title="Hafr_Matlab" src="images/posts/oldwordpress/uploads/2010/04/Hafr_Matlab-300x219.png" alt="" width="300" height="219" >}}</a></em>
    
    <p class="wp-caption-text">
      Hfar of a scattering circle using Matlab
    </p>
  </div></em>
</p>

<p style="text-align: justify;">
   
</p>

<p style="text-align: justify;">
  <em>To follow</em> : You can also compared the resulting field with a theoretical diffracted circle. In the following article, I will explain how to compute the scattered field of a circle theoretically.
</p>