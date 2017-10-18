---
title: 'Numpy error – ValueError: setting an array element with sequence'
author: Jice

date: 2009-06-04
url: /2009/06/numpy-error-valueerror-setting-an-array-element-with-sequence/
aktt_notify_twitter:
  - no
Image: images/posts/oldwordpress/uploads/2009/06/python.png
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
tags:
  - numpy
  - python
---
<p style="text-align: justify;">
  You have struggled during hours and hours to understand why you got this damned error while compiling a complex array structure? I did. In my case I was trying to create an array of the following shape :
</p>

<p style="text-align: center;">
  [  [ [0,0,1,0] , 0.5] , [ [0,1,1,0] , 0.3] , [ [1,0,1,0] , 0.2] ]
</p>

<p style="text-align: justify;">
  With the basic syntax, it was impossible. I first didn&#8217;t notice the problem because I wasn&#8217;t using the &#8216;<em>array</em>&#8216; constructor, but when I tried to <strong>append </strong>some value to my initial vector, I got the error : <strong>ValueError: setting an array element with sequence</strong>.<!--more-->
</p>

<p style="text-align: left;">
  Even the simple construction : <em>array([( [0,0,1,0],0.5)]) </em>would give the error.
</p>

<p style="text-align: justify;">
  the problem is that <strong>numpy </strong>is made to calculate vectors and arrays. It doesn&#8217;t like the fact you give it table with different sizes. Ok, then you can try to change the second value 0.5 to [0.5,0,0,0]. It would work&#8230;. but it&#8217;s not really clean. Your code will look messy.
</p>

<p style="text-align: justify;">
  <p style="text-align: justify;">
    Instead, here is the solution I found after 4 hours looking everywhere on the web&#8230; finding nothing. This is my own solution, so if helped you, I would be very glad :-D
  </p>

  <p style="text-align: justify;">
    In order to help numpy to accept your vector&#8230; tell it it&#8217;s not a vector :
  </p>

  <p style="text-align: center;">
    <em>array([( [0,0,1,0],0.5)],<span style="color: #ff0000;">object</span>)</em>
  </p>

  <p style="text-align: justify;">
    By doing this you change de dtype of your array, and it can accept even personnal classes.
  </p>

  <p style="text-align: justify;">
    <p style="text-align: justify;">
      Does that work for you?<em><br /> </em>
    </p>
