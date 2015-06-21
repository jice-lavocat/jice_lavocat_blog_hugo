---
title: Grover’s Search Algorithm in Python
author: Jice

date: 2009-08-15
url: /2009/08/grovers-search-algorithm-in-python/
Image:
  - images/posts/oldwordpress/uploads/2009/08/grover_simple-150x150.png
categories:
  - Quantum Information
tags:
  - python
  - Quantum Information
  - Quantum Oracle
---
<p style="text-align: justify;">
  As you may have read in some previous post I am actually working on a modified version of the <a title="Lee Grover" href="http://www1.bell-labs.com/user/lkgrover/" target="_blank">Grover</a>&#8216;s <a title="Grover's Search Algorithm" href="http://arxiv.org/abs/quant-ph/9605043" target="_blank">Algorithm</a>. For those who don&#8217;t know the <a title="Explanations of Grover's Algorithm" href="http://www.quantiki.org/wiki/index.php/Grover%27s_search_algorithm" target="_blank">principles of Grover&#8217;s Algorithm</a>, here is a quick explanation.
</p>

<p style="text-align: justify;">
  We have a function $$f : \mathbb{Z}_2^n\rightarrow \mathbb{Z}_2$$ that is True for only one $$a \in \mathbb{Z}_2^n$$. We also have a quantum oracle that returns the value of the function f. Classicaly, finding the value of $$a$$ will take n-1 steps. With the quantum version (Grover&#8217;s Algorithm) it takes only $$\sqrt{n}$$ steps.
</p>

<p style="text-align: justify;">
  The idea (without explanations) is to take an equally distributed weights vector as input $$x$$, and to iterate a sequence of unitary operations during a certain amount of time.  After this given number of steps a measurement on the input vector is made, and is has been proved that we will observed the correct answer with probability 1. The number of steps is proportional to $$\sqrt{n}$$.
</p>

<p style="text-align: justify;">
  Bellow I put the picture representing the evolution (step after step) of the probability to observe the correct answer. You can see the oscillations that are well explained by geometrical description of this algorithm.
</p>

<h2 style="text-align: center;">
  <a href="images/posts/oldwordpress/uploads/2009/08/grover_simple.png">{{<img class="aligncenter size-thumbnail wp-image-801" title="grover_simple" src="images/posts/oldwordpress/uploads/2009/08/grover_simple-150x150.png" alt="grover_simple" width="150" height="150" >}}</a>
</h2>

<h2 style="text-align: justify;">
  Python Code
</h2>

<p style="text-align: justify;">
  Bellow you&#8217;ll find the code associated to this example. You&#8217;ll also be able to visualize the animation of the probabilities distribution according to the time.  The code is written in <a title="Python" href="http://www.python.org/" target="_blank">Python</a> and requires <a title="Numpy" href="http://numpy.scipy.org/" target="_blank">Numpy</a> to work. The associated functions classes are not useful for this simple case, but you&#8217;ll understand in the coming post why I need them.
</p>

  * [Grover Algorithm &#8211; Python][1] (run _python grover.py_)[<p style="text-align: justify;">
  As you may have read in some previous post I am actually working on a modified version of the <a title="Lee Grover" href="http://www1.bell-labs.com/user/lkgrover/" target="_blank">Grover</a>&#8216;s <a title="Grover's Search Algorithm" href="http://arxiv.org/abs/quant-ph/9605043" target="_blank">Algorithm</a>. For those who don&#8217;t know the <a title="Explanations of Grover's Algorithm" href="http://www.quantiki.org/wiki/index.php/Grover%27s_search_algorithm" target="_blank">principles of Grover&#8217;s Algorithm</a>, here is a quick explanation.
</p>

<p style="text-align: justify;">
  We have a function $$f : \mathbb{Z}_2^n\rightarrow \mathbb{Z}_2$$ that is True for only one $$a \in \mathbb{Z}_2^n$$. We also have a quantum oracle that returns the value of the function f. Classicaly, finding the value of $$a$$ will take n-1 steps. With the quantum version (Grover&#8217;s Algorithm) it takes only $$\sqrt{n}$$ steps.
</p>

<p style="text-align: justify;">
  The idea (without explanations) is to take an equally distributed weights vector as input $$x$$, and to iterate a sequence of unitary operations during a certain amount of time.  After this given number of steps a measurement on the input vector is made, and is has been proved that we will observed the correct answer with probability 1. The number of steps is proportional to $$\sqrt{n}$$.
</p>

<p style="text-align: justify;">
  Bellow I put the picture representing the evolution (step after step) of the probability to observe the correct answer. You can see the oscillations that are well explained by geometrical description of this algorithm.
</p>

<h2 style="text-align: center;">
  <a href="images/posts/oldwordpress/uploads/2009/08/grover_simple.png">{{<img class="aligncenter size-thumbnail wp-image-801" title="grover_simple" src="images/posts/oldwordpress/uploads/2009/08/grover_simple-150x150.png" alt="grover_simple" width="150" height="150" >}}</a>
</h2>

<h2 style="text-align: justify;">
  Python Code
</h2>

<p style="text-align: justify;">
  Bellow you&#8217;ll find the code associated to this example. You&#8217;ll also be able to visualize the animation of the probabilities distribution according to the time.  The code is written in <a title="Python" href="http://www.python.org/" target="_blank">Python</a> and requires <a title="Numpy" href="http://numpy.scipy.org/" target="_blank">Numpy</a> to work. The associated functions classes are not useful for this simple case, but you&#8217;ll understand in the coming post why I need them.
</p>

  * [Grover Algorithm &#8211; Python][1] (run _python grover.py_)][1] 

<h2 style="text-align: justify;">
  Interesting fact:
</h2>

<p style="text-align: justify;">
  If you use more than one correct possible answer (as in the case of perceptron learning) and a different matrix (namely with two -1 instead of only one), the behaviour could be close to the Grover&#8217;s Algorithm. Since I was studying perceptron, I implemented a function that output an oracle given a certain threshold. If this threshold is 0, then only one correct answer exist. If it&#8217;s one, then n+1 correct answers are possible &#8230; but they are all in relation with the initial <strong>teacher</strong>.
</p>

<p style="text-align: center;">
  If we fix the teacher, select a threshold of 1, and use the matrix H.diag(-1,1,&#8230;,1,-1).H and apply the same algorithm we get the following probability distribution for the teacher :
</p>

<p style="text-align: center;">
  <a href="images/posts/oldwordpress/uploads/2009/08/grover_thresh_1.png">{{<img class="aligncenter size-thumbnail wp-image-804" title="grover_thresh_1" src="images/posts/oldwordpress/uploads/2009/08/grover_thresh_1-150x150.png" alt="grover_thresh_1" width="150" height="150" >}}</a>
</p>

<p style="text-align: justify;">
  <p style="text-align: justify;">
    If you want to use my code, you have to put <em>teachers=mat_teacher_bin(N,1) </em>on line 36 and uncomment line 69
  </p>
  
  <p style="text-align: justify;">
    Explainations? For the moment none. But I plan to read the following paper : <a href="http://www.sciencedirect.com/science?_ob=ArticleURL&_udi=B6V1G-4MMWHMX-1&_user=10&_rdoc=1&_fmt=&_orig=search&_sort=d&_docanchor=&view=c&_searchStrId=980896614&_rerunOrigin=google&_acct=C000050221&_version=1&_urlVersion=0&_userid=10&md5=7c1272e80f23322e994db33251e2d2df" target="_blank">Improved bond in Oracle identification</a>
  </p>
  
  <p style="text-align: justify;">

 [1]: images/posts/oldwordpress/uploads/2009/08/Grover.zip