---
layout: projects
permalink: /projects/
title: 
tags: [projects]
modified: 26-7-2019
comments: false
---

## Projects

### 1) [**Stanza Graph Construction**](http://{{ site.url }}/stanza)<br>

  <img src="{{ site.url }}/images/stanza-1.png" alt="Snow" style="width:100%">
    
  * Task - Identifying Section headers, Distinguishing Enumeration lists start ( folded and unfolded ) with Section references and finding hierarchy between them
  * Curated a span detection dataset for section starts and section references from Credit agreements
  * Developed a model for distinguishing between sections starts and section references using BERT and
CNN-based technique
  * Developed an algorithm for finding links between various section starts and created a tree-based
representation for the entire document
  * Converted a raw pdf document into a navigable HTML for faster navigation and readability
    
  <img src="{{ site.url }}/images/Stanza-2.png" alt="Forest" style="width:100%">

### 2) [**Reading order detection on Directory pages**](http://)<br>

  <img src="{{ site.url }}/images/directory-page-1.png" alt="Dp1" style="width:100%">
    
  * Curated a dataset depicting the reading order for the Directory page documents
  * Proposed a novel set of features and trained a random forest model for identifying Directory pages( usually a couple of pages in a 300 page long document) in Prospectuses
  * Proposed and implemented parsing of text present in directory pages in a tree-structured format. This
    enabled downstream Relation extraction tasks to be performed with ease
  
    <img src="{{ site.url }}/images/directory-page-2.png" alt="Dp2" style="width:100%">

### * [**Ternary Relation extraction in Prospectuses**](http://)<br>

  <img src="{{ site.url }}/images/relation-extraction-1.png" alt="Dp1" style="width:100%">
      
  * Answering questions like ”Who is the Legal advisor of Amazon for this fund offerring?
  * Curated a ternary relation extraction dataset amongst organizations, person names and roles
  * Developed a BERT-based model leveraging entity markers to enrich entity embeddings sent to the relation head
  * Reduced review time of cases from a few hours to a couple of minutes when a new onboarding of a client takes place

### * [**Mathematical Constraint Extraction - Extraction of Negative Covenants from Credit Agreements**](http://)<br>


