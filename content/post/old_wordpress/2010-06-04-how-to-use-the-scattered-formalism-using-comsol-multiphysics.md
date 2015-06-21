---
title: How to use the Scattered formalism using Comsol Multiphysics
author: Jice

date: 2010-06-04
url: /2010/06/how-to-use-the-scattered-formalism-using-comsol-multiphysics/
Image:
  - http://fralbe.files.wordpress.com/2008/05/comsol.gif
categories:
  - Sciences
  - Scientific Computations
tags:
  - Comsol
  - RF module
  - Scattered Field
---
<p style="text-align: justify;">
  After my last post about &#8216;<a title="Far field Comsol" href="http://localhost/oldblog/2010/04/how-to-get-the-electromagnetic-scattered-far-field-using-comsol-rf-module/">getting the scattered far field using ComsolRF module</a> &#8216; a bunch of problems appeared. Actually, the definition of the incident field, using a line of current is wrong. It prevent the PML to work nicely, and thus, the overall field (and of course the scattered field) will be wrong.
</p>

<p style="text-align: justify;">
  To correct this behaviour, one should first start a problem by using the <em>Scattered Formalism Equation Resolution</em>. If you already have your setup, just go to <strong>Physics</strong> > <strong>Properties</strong> and change the <strong>Field Type</strong> to &#8216;Scattered xxxxx waves&#8217; (where xxxxx is your polarization system : TE, TM or hybrid).
</p>

<p style="text-align: justify;">
  Now, instead of including a source inside your setup, Comsol will use a theoretical field that we have to define. With this formalism, no boundaries problem can appear again.
</p>

<p style="text-align: justify;">
  First create your setup, and add your PML. As an exeternal boundary condition, choose <strong>Scattering Boundary Condition </strong>(and specify the type of field you want to use). For a regular geometry there is no difference with the initial condition (ie. Perfect Electrice Conductor), but I guess that differences could appear if your domain is a little bit tricky.
</p>

<p style="text-align: justify;">
  Now you have to tell Comsol what is the field that you want to use. For that, just go to<strong> Physics</strong> > <strong>Scalar Variables</strong> and change <strong>H0iz_rfweh. </strong>Now, you should want to use a plane wave or a cylindrical wave :
</p>

  * Plane wave : use **exp(-j\*k0_rfweh\*(cos(alpha)\*x+sin(alpha)\*y))**

<p style="padding-left: 60px;">
  - you have to define alpha \in (0, 2*pi), the angle of incidence in <strong>Options > Expressions > Global Expressions</strong>.
</p>

  * Cylindrical wave : use **besselj(0,k0_rfweh*(r))**

<p style="padding-left: 60px;">
  - you have to define r = sqrt((x-xc)^2+(y-yc)^2), the center of your source in <strong>Options > Expressions > Global Expressions</strong>.
</p>

<p style="padding-left: 60px;">
  - you have to define xc and yc, the coordinates of your source, in <strong>Options > Expressions > Global Expressions</strong>.
</p>

<p style="padding-left: 60px;">
  <a href="/images/posts/oldwordpress/uploads/2010/06/comsol_plane.png"><img class="aligncenter size-medium wp-image-1077" title="Field Definition Comsol" src="/images/posts/oldwordpress/uploads/2010/06/comsol_plane-300x220.png" alt="" width="300" height="220" /></a>
</p>

<p style="padding-left: 60px;">
   
</p>

<p style="padding-left: 60px;">
   
</p>

Hope this will help.

Any feedback appreciated.