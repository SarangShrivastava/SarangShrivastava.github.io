---
layout: projects
permalink: /directory/
title: Reading Order Detection on Directory pages
tags: [directory]
modified: 26-7-2019
comments: false
---

   <img src="{{ site.url }}/images/directory-page-1.png" alt="Dp1" style="width:100%">
    
  * Curated a dataset depicting the reading order for the Directory page documents
  * Proposed a novel set of features and trained a random forest model for identifying Directory pages( usually a couple of pages in a 300 page long document) in Prospectuses
  * Proposed and implemented parsing of text present in directory pages in a tree-structured format. This
    enabled downstream Relation extraction tasks to be performed with ease
  
Till now we had seen problems which were tilted heavily towards one end of the spectrum, now lets talk about a problem which is a right mix of semantics and structure. 

By far the biggest challenge is offered by directory pages, as illustrated in the figure on the left.  Here the author chooses to provide the knowledge hierarchically, using 2-d visual information to carry some of the structure with it. One can look at such a page as consisting of multiple entries with an entry specifying (typically) an organization and an address and a header which provides some context for the entry, typically a portion of the role played by the organization (e.g. “Administrator of the Fund”). 

Notice that some portions of the page may be marked off, typically with a center panel running across the columns (e.g. “Legal Counsel to the Fund and Master Fund”); one can think of this as an entry with only a header. The role associated with an organization must sometimes be obtained by combining headers from multiple entries (e.g. “Legal Counsel to the Fund and Master Fund” and “(as per Hong Kong legal matters)”). Combining both tells us the correct organization which is the legal counsel to the fund specifically in the matters of Hong Kong. 

A key problem for directory pages is determining their reading order. The typical left-to-right , top-to-bottom reading order for English language pages does not work for directory pages since the organizing unit for directory pages is not columns but entries. Once we nail this problem, relation extraction on these pages becomes easy as the  root to leaf path of the directory tree that we see on the right gives us the natural reading order for a block of information. 

We solved this problem of parsing a directory page by first identifying these specific pages in the documents, segmenting the text in those documents into 2 parts – specifically headers which you see in pink and the bodies which you see in blue. Post this, we used a bottom up approach of parsing this segmented text and constructed this tree.

    <img src="{{ site.url }}/images/directory-page-2.png" alt="Dp2" style="width:100%">
