---
layout: projects
permalink: /stanza/
title: Stanza Graph Construction
tags: [stanza]
modified: 26-7-2019
comments: false
---

  <img src="{{ site.url }}/images/stanza-1.png" alt="Snow" style="width:100%">
    
  * Task - Identifying Section headers, Distinguishing Enumeration lists start ( folded and unfolded ) with Section references and finding hierarchy between them
  * Curated a span detection dataset for section starts and section references from Credit agreements
  * Developed a model for distinguishing between sections starts and section references using BERT and
CNN-based technique
  * Developed an algorithm for finding links between various section starts and created a tree-based
representation for the entire document
  * Converted a raw pdf document into a navigable HTML for faster navigation and readability

The next problem that I want to talk about is of extracting the correct hierarchy of sections, sub sections, enumerated sentences etc and represent the content of the entire document in a graphical manner. 

The text on the left that you see is a wrapped around version of the enumerated lists that you see on the right. A part of getting this correct representation out is to nail this as well.  We start off by identifying sections and subsection headers using a similar technique which we mentioned for TOC. The next part of the puzzle is to differentiate between the text that represents the beginning of the list and the span of text which represents the section references.  We used a text classification head sitting on top of the BERT based back bone to solve this. Once we have all the section/ sub section headers and the start of the enumerated lists, we construct a hierarchy of it.  We developed classifiers that helped us in answering key questions like whether there is a parent child relationship between two candidates or not. 

The abstractions of page/paragraph/line and words is good but this graphical representation which we call as the “Stanzagraph” is even better.  There are many tasks which can directly benefit from this structure. For Example -  Extracting of complex clauses from Credit agreements,  Getting better paragraph embeddings out using the title stack which we can extract from this representation as well.

  <img src="{{ site.url }}/images/Stanza-2.png" alt="Forest" style="width:100%">
