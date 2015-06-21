---
title: Python et Google PageRank
author: Jice

date: 2009-07-02
url: /2009/07/python-et-google-pagerank/
Image:
  - images/posts/oldwordpress/uploads/2009/06/python.png
categories:
  - Python
tags:
  - Google
  - Pagerank
  - python
---
<p style="text-align: justify;">
  {{<img class="alignleft size-full wp-image-422" style="margin: 5px;" title="python" src="images/posts/oldwordpress/uploads/2009/06/python.png" alt="python" width="75" height="75" >}}Suite à mes recherches pour trouver un script de calcul de Pagerank en python, je souhaitais vous présenter deux pages qui me sont tombées sous les yeux.
</p>

<p style="text-align: justify;">
  <!--more-->
</p>

<h2 style="text-align: justify;">
  Script de vérification de Pagerank en Python :
</h2>

<p style="text-align: justify;">
  Ce script permet d&#8217;aller chercher la valeur de Pagerank Google d&#8217;un site donné en argument. Cela sert pour toutes sortes de choses dans le monde du SEO. La page en question est là :
</p>

<p style="text-align: justify;">
  <a title="Script calcul pagerank python" href="http://blogmag.net/blog/read/91/Python_code_to_check_your_Google_PageRank" target="_blank">http://blogmag.net/blog/read/91/Python_code_to_check_your_Google_PageRank</a>
</p>

<p style="text-align: justify;">
  Testé aujourd&#8217;hui (1er Juillet 2009), le script fonctionne parfaitement bien. Ceux que j&#8217;ai pu trouver en php ne marchaient pas ( google me considère comme un pirate vous savez). Si vous en possédez en PHP, je suis preneur
</p>

<h2 style="text-align: justify;">
  Script de calcul de PageRank ( Google-like)
</h2>

<p style="text-align: justify;">
  La page suivante se base sur un <a title="Pagerank algorithme" href="http://www.ams.org/featurecolumn/archive/pagerank.html" target="_blank">article publié à l&#8217;AMS</a>, mais dont le principe <a href="http://www.mattcutts.com/blog/pagerank-sculpting/" target="_blank">ne décrit pas exactement le fonctionnement de Google</a>.
</p>

<p style="text-align: justify;">
  Le script écrit en python tente de reproduire le fonctionnement d&#8217;un algorithme de Pagerank. Je ne l&#8217;ai pas testé, mais ça peut interesser du monde :
</p>

<p style="text-align: justify;">
  <a title="Pagerank algorithme en Python" href="http://www.eioba.com/a69792/the_google_pagerank_algorithm_in_126_lines_of_python" target="_blank">http://www.eioba.com/a69792/the_google_pagerank_algorithm_in_126_lines_of_python</a>
</p>

<div id="_mcePaste" style="overflow: hidden; position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px;">
  <pre><span class="c">#!/usr/bin/env python</span>
<span class="c"># -*- coding: utf-8 -*-</span>
<span class="c"># (C) 2008 Fred Cirera</span>
<span class="c"># ported in Python from the Ruby code by Vsevolod S. Balashov</span>
<span class="c"># http://snippets.dzone.com/posts/show/3284</span>

<span class="k">import</span> <span class="nn">urllib2</span>
<span class="k">import</span> <span class="nn">re</span>
<span class="k">import</span> <span class="nn">time</span>
<span class="k">import</span> <span class="nn">sys</span>

<span class="k">from</span> <span class="nn">urllib</span> <span class="k">import</span> <span class="n">urlencode</span>
<span class="k">from</span> <span class="nn">pprint</span> <span class="k">import</span> <span class="n">pprint</span>

<span class="n">HOST</span> <span class="o">=</span> <span class="s">"toolbarqueries.google.com"</span>

<span class="k">def</span> <span class="nf">mix</span><span class="p">(</span><span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span><span class="p">):</span>
    <span class="n">M</span> <span class="o">=</span> <span class="k">lambda</span> <span class="n">v</span><span class="p">:</span> <span class="n">v</span> <span class="o">%</span> <span class="mf"></span><span class="n">x100000000</span> <span class="c"># int32 modulo</span>
    <span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span> <span class="o">=</span> <span class="p">(</span><span class="n">M</span><span class="p">(</span><span class="n">a</span><span class="p">),</span> <span class="n">M</span><span class="p">(</span><span class="n">b</span><span class="p">),</span> <span class="n">M</span><span class="p">(</span><span class="n">c</span><span class="p">))</span>

    <span class="n">a</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">c</span> <span class="o">&gt;&gt;</span> <span class="mf">13</span><span class="p">)</span>
    <span class="n">b</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">a</span> <span class="o">&lt;&lt;</span>  <span class="mf">8</span><span class="p">)</span>
    <span class="n">c</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">b</span> <span class="o">&gt;&gt;</span> <span class="mf">13</span><span class="p">)</span>

    <span class="n">a</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">c</span> <span class="o">&gt;&gt;</span> <span class="mf">12</span><span class="p">)</span>
    <span class="n">b</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">a</span> <span class="o">&lt;&lt;</span> <span class="mf">16</span><span class="p">)</span>
    <span class="n">c</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">b</span> <span class="o">&gt;&gt;</span> <span class="mf">5</span><span class="p">)</span>

    <span class="n">a</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">c</span> <span class="o">&gt;&gt;</span>  <span class="mf">3</span><span class="p">)</span>
    <span class="n">b</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">b</span><span class="o">-</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">a</span> <span class="o">&lt;&lt;</span> <span class="mf">10</span><span class="p">)</span>
    <span class="n">c</span> <span class="o">=</span> <span class="n">M</span><span class="p">(</span><span class="n">c</span><span class="o">-</span><span class="n">a</span><span class="o">-</span><span class="n">b</span><span class="p">)</span> <span class="o">^</span> <span class="p">(</span><span class="n">b</span> <span class="o">&gt;&gt;</span> <span class="mf">15</span><span class="p">)</span>

    <span class="k">return</span> <span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span>

<span class="k">def</span> <span class="nf">checksum</span><span class="p">(</span><span class="n">iurl</span><span class="p">):</span>
    <span class="n">C2I</span> <span class="o">=</span> <span class="k">lambda</span> <span class="n">s</span><span class="p">:</span> <span class="nb">sum</span><span class="p">(</span><span class="n">c</span> <span class="o">&lt;&lt;</span> <span class="mf">8</span><span class="o">*</span><span class="n">i</span> <span class="k">for</span> <span class="n">i</span><span class="p">,</span> <span class="n">c</span> <span class="ow">in</span> <span class="nb">enumerate</span><span class="p">(</span><span class="n">s</span><span class="p">[:</span><span class="mf">4</span><span class="p">]))</span>
    <span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span> <span class="o">=</span> <span class="mf"></span><span class="n">x9e3779b9</span><span class="p">,</span> <span class="mf"></span><span class="n">x9e3779b9</span><span class="p">,</span> <span class="mf"></span><span class="n">xe6359a60</span>
    <span class="n">lg</span>  <span class="o">=</span> <span class="nb">len</span><span class="p">(</span><span class="n">iurl</span><span class="p">)</span>
    <span class="n">k</span> <span class="o">=</span> <span class="mf"></span>
    <span class="k">while</span> <span class="n">k</span> <span class="o">&lt;=</span> <span class="n">lg</span><span class="o">-</span><span class="mf">12</span><span class="p">:</span>
        <span class="n">a</span> <span class="o">=</span> <span class="n">a</span> <span class="o">+</span> <span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="p">:</span><span class="n">k</span><span class="o">+</span><span class="mf">4</span><span class="p">])</span>
        <span class="n">b</span> <span class="o">=</span> <span class="n">b</span> <span class="o">+</span> <span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="o">+</span><span class="mf">4</span><span class="p">:</span><span class="n">k</span><span class="o">+</span><span class="mf">8</span><span class="p">])</span>
        <span class="n">c</span> <span class="o">=</span> <span class="n">c</span> <span class="o">+</span> <span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="o">+</span><span class="mf">8</span><span class="p">:</span><span class="n">k</span><span class="o">+</span><span class="mf">12</span><span class="p">])</span>
        <span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span> <span class="o">=</span> <span class="n">mix</span><span class="p">(</span><span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span><span class="p">)</span>
        <span class="n">k</span> <span class="o">+=</span> <span class="mf">12</span>

    <span class="n">a</span> <span class="o">=</span> <span class="n">a</span> <span class="o">+</span> <span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="p">:</span><span class="n">k</span><span class="o">+</span><span class="mf">4</span><span class="p">])</span>
    <span class="n">b</span> <span class="o">=</span> <span class="n">b</span> <span class="o">+</span> <span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="o">+</span><span class="mf">4</span><span class="p">:</span><span class="n">k</span><span class="o">+</span><span class="mf">8</span><span class="p">])</span>
    <span class="n">c</span> <span class="o">=</span> <span class="n">c</span> <span class="o">+</span> <span class="p">(</span><span class="n">C2I</span><span class="p">(</span><span class="n">iurl</span><span class="p">[</span><span class="n">k</span><span class="o">+</span><span class="mf">8</span><span class="p">:])</span><span class="o">&lt;&lt;</span><span class="mf">8</span><span class="p">)</span> <span class="o">+</span> <span class="n">lg</span>
    <span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span> <span class="o">=</span> <span class="n">mix</span><span class="p">(</span><span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span><span class="p">)</span>
    <span class="k">return</span> <span class="n">c</span>

<span class="k">def</span> <span class="nf">GoogleHash</span><span class="p">(</span><span class="n">value</span><span class="p">):</span>
    <span class="n">I2C</span> <span class="o">=</span> <span class="k">lambda</span> <span class="n">i</span><span class="p">:</span> <span class="p">[</span><span class="n">i</span> <span class="o">&</span> <span class="mf"></span><span class="n">xff</span><span class="p">,</span> <span class="n">i</span> <span class="o">&gt;&gt;</span> <span class="mf">8</span> <span class="o">&</span> <span class="mf"></span><span class="n">xff</span><span class="p">,</span>  <span class="n">i</span> <span class="o">&gt;&gt;</span> <span class="mf">16</span> <span class="o">&</span> <span class="mf"></span><span class="n">xff</span><span class="p">,</span> <span class="n">i</span> <span class="o">&gt;&gt;</span> <span class="mf">24</span> <span class="o">&</span> <span class="mf"></span><span class="n">xff</span><span class="p">]</span>
    <span class="n">ch</span> <span class="o">=</span> <span class="n">checksum</span><span class="p">([</span><span class="nb">ord</span><span class="p">(</span><span class="n">c</span><span class="p">)</span> <span class="k">for</span> <span class="n">c</span> <span class="ow">in</span> <span class="n">value</span><span class="p">])</span>
    <span class="n">ch</span> <span class="o">=</span> <span class="p">((</span><span class="n">ch</span> <span class="o">%</span> <span class="mf"></span><span class="n">x0d</span><span class="p">)</span> <span class="o">&</span> <span class="mf">7</span><span class="p">)</span> <span class="o">|</span> <span class="p">((</span><span class="n">ch</span><span class="o">/</span><span class="mf">7</span><span class="p">)</span> <span class="o">&lt;&lt;</span> <span class="mf">2</span><span class="p">)</span>
    <span class="k">return</span> <span class="s">"6</span><span class="si">%s</span><span class="s">"</span> <span class="o">%</span> <span class="n">checksum</span><span class="p">(</span><span class="nb">sum</span><span class="p">((</span><span class="n">I2C</span><span class="p">(</span><span class="n">ch</span><span class="o">-</span><span class="mf">9</span><span class="o">*</span><span class="n">i</span><span class="p">)</span> <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mf">20</span><span class="p">)),</span> <span class="p">[]))</span>

<span class="k">def</span> <span class="nf">make_url</span><span class="p">(</span><span class="n">host</span><span class="p">,</span> <span class="n">site_url</span><span class="p">):</span>
    <span class="n">url</span> <span class="o">=</span> <span class="s">"info:"</span> <span class="o">+</span> <span class="n">site_url</span>
    <span class="n">params</span> <span class="o">=</span> <span class="nb">dict</span><span class="p">(</span><span class="n">client</span><span class="o">=</span><span class="s">"navclient-auto"</span><span class="p">,</span> <span class="n">ch</span><span class="o">=</span><span class="s">"</span><span class="si">%s</span><span class="s">"</span> <span class="o">%</span> <span class="n">GoogleHash</span><span class="p">(</span><span class="n">url</span><span class="p">),</span>
                  <span class="n">ie</span><span class="o">=</span><span class="s">"UTF-8"</span><span class="p">,</span> <span class="n">oe</span><span class="o">=</span><span class="s">"UTF-8"</span><span class="p">,</span> <span class="n">features</span><span class="o">=</span><span class="s">"Rank"</span><span class="p">,</span> <span class="n">q</span><span class="o">=</span><span class="n">url</span><span class="p">)</span>
    <span class="k">return</span> <span class="s">"http://</span><span class="si">%s</span><span class="s">/search?</span><span class="si">%s</span><span class="s">"</span> <span class="o">%</span> <span class="p">(</span><span class="n">host</span><span class="p">,</span> <span class="n">urlencode</span><span class="p">(</span><span class="n">params</span><span class="p">))</span>

<span class="c"># Where the fun begins</span>

<span class="k">if</span> <span class="n">__name__</span> <span class="o">==</span> <span class="s">"__main__"</span><span class="p">:</span>
    <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">sys</span><span class="o">.</span><span class="n">argv</span><span class="p">)</span> <span class="o">!=</span> <span class="mf">2</span><span class="p">:</span>
        <span class="n">url</span> <span class="o">=</span> <span class="s">'http://www.google.com/'</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">url</span> <span class="o">=</span> <span class="n">sys</span><span class="o">.</span><span class="n">argv</span><span class="p">[</span><span class="mf">1</span><span class="p">]</span>

    <span class="k">if</span> <span class="ow">not</span> <span class="n">url</span><span class="o">.</span><span class="n">startswith</span><span class="p">(</span><span class="s">'http://'</span><span class="p">):</span>
        <span class="n">url</span> <span class="o">=</span> <span class="s">'http://</span><span class="si">%s</span><span class="s">'</span> <span class="o">%</span> <span class="n">url</span>

    <span class="c"># print make_url(HOST, url)</span>
    <span class="n">req</span> <span class="o">=</span> <span class="n">urllib2</span><span class="o">.</span><span class="n">Request</span><span class="p">(</span><span class="n">make_url</span><span class="p">(</span><span class="n">HOST</span><span class="p">,</span> <span class="n">url</span><span class="p">))</span>
    <span class="k">try</span><span class="p">:</span>
        <span class="n">f</span> <span class="o">=</span> <span class="n">urllib2</span><span class="o">.</span><span class="n">urlopen</span><span class="p">(</span><span class="n">req</span><span class="p">)</span>
        <span class="n">response</span> <span class="o">=</span> <span class="n">f</span><span class="o">.</span><span class="n">readline</span><span class="p">()</span>
    <span class="k">except</span> <span class="ne">Exception</span><span class="p">,</span> <span class="n">err</span><span class="p">:</span>
        <span class="k">print</span> <span class="n">err</span>
        <span class="c"># print err.read()</span>
        <span class="n">sys</span><span class="o">.</span><span class="n">exit</span><span class="p">(</span><span class="mf">1</span><span class="p">)</span>

    <span class="k">try</span><span class="p">:</span>
        <span class="n">rank</span> <span class="o">=</span> <span class="n">re</span><span class="o">.</span><span class="n">match</span><span class="p">(</span><span class="s">r'^Rank_\d+:\d+:(\d+)'</span><span class="p">,</span> <span class="n">response</span><span class="o">.</span><span class="n">strip</span><span class="p">())</span><span class="o">.</span><span class="n">group</span><span class="p">(</span><span class="mf">1</span><span class="p">)</span>
    <span class="k">except</span> <span class="ne">AttributeError</span><span class="p">:</span>
        <span class="k">print</span> <span class="s">"This page is not ranked"</span>
        <span class="n">rank</span> <span class="o">=</span> <span class="o">-</span><span class="mf">1</span>

    <span class="k">print</span> <span class="s">"PagerRank: </span><span class="si">%d</span><span class="se">\t</span><span class="s">URL: </span><span class="si">%s</span><span class="s">"</span> <span class="o">%</span> <span class="p">(</span><span class="nb">int</span><span class="p">(</span><span class="n">rank</span><span class="p">),</span> <span class="n">url</span><span class="p">)</span></pre>
</div>