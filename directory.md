---
layout: projects
permalink: /directory/
title: Reading Order Detection on Directory pages
tags: [directory]
modified: 26-7-2019
comments: false
---
<p align="center">
   <img src="{{ site.url }}/images/directory-page-1.png" alt="Dp1" style="width:75%"></p> <br>

<p align="justify">
The determination of the reading sequence of text is fundamental to document understanding. 
This problem is easily solved in pages where the text is organized into a sequence of lines and 
vertical alignment runs the height of the page (producing multiple columns which can be read from 
left to right). This is a situation -- the directory page parsing problem -- where information is
presented on the page in an irregular, visually-organized, two-dimensional format. Directory pages 
are fairly common in financial prospectuses and carry information about organizations, their addresses
and relationships that is key to business tasks in client onboarding. Interestingly, directory pages 
sometimes have hierarchical structure, motivating the need to generalize the reading sequence to a 
reading tree. </p> <br>

<p align="justify">
Notice that some portions of the page may be marked off, typically with a center panel running across 
the columns (e.g. “Legal Counsel to the Fund and Master Fund”); one can think of this as an entry with
only a header. The role associated with an organization must sometimes be obtained by combining headers 
from multiple entries (e.g. “Legal Counsel to the Fund and Master Fund” and “(as per Hong Kong legal 
matters)”). Combining both tells us the correct organization which is the legal counsel to the fund
specifically in the matters of Hong Kong.</p> <br>

<p align="justify">
The typical left-to-right across-the-column / top-to-bottom reading order for English language pages 
does not work for directory pages since the organizing unit for directory pages is not columns but 
entries. Consider the figure above, a standard reading order would give:</p> <br>

<p align="justify">
“Legal Counsel to the Fund and the Master Fund” / “(as per Hong Kong legal matters)” /
“(as per Singapore legal matters)” / “RAM (LUX) SYSTEMATIC FUNDS 14, boulevard Royal L2449 LUXEMBOURG” 
/ “BANQUE DE LUXEMBOURG Société anonyme (public limited company) 14, boulevard Royal L-2449 LUXEMBOURG ”</p> <br>

<p align="justify">
We can get a better representation by recognizing that the text on the page should not be represented
as a sequence, but rather as a tree, (the reading tree) as illustrated in the figure below. Here,
the hierarchy captures that the header of a parent node applies also to the child nodes.</p> <br>

<p align="justify">
Once we nail this problem, relation extraction on these pages becomes easy as the  root to leaf path 
of the directory tree that we see on the right gives us the natural reading order for a block of 
information. </p> <br>

<p align="justify">
We solved this problem of parsing a directory page by first identifying these specific pages in the
documents using a random forest model, segmenting the text in those pages into 2 parts – specifically headers which you see 
in pink and the bodies which you see in blue. Post this, we used a bottom up approach of parsing this
segmented text and constructed this tree.</p> <br>

<p align="center">
<img src="{{ site.url }}/images/directory-page-1.png" alt="Dp1" style="width:75%"></p>