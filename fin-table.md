---
layout: projects
permalink: /fin-table/
title: Understanding and Resolving Hierarchical Table Structure
tags: [fin-table]
modified: 26-7-2019
comments: false
---


<img src="{{ site.url }}/images/table.png" alt="Snow" style="width:100%">
    
While many pipelines for extracting information from tables assume simple table structure, 
tables in the financial domain frequently have complex, hierarchical structure. 
The main example would be parent-child relationships between header cells. 

The key point here is to respect the layout information of the document along with the text to learn better Embeddings which captures best of both the structural and the semantic worlds. Often a pipeline based approach in ML leadds to drastically impacting the performance of the model.  So doing things in one shot gives better results and reduces the scope of errors which the model can make.

The tables are selected from IBM FinTabNet, a much larger dataset of more than 100,000 financial 
tables having cell, row, and column bounding boxes extracted by deep learning, but not including 
semantic cell type or cell-to-cell relation labels, which we add.

We fine-tune models based on LayoutLM on the cell-type classification task and on the 
identification of hiearchical relations among column headers. We achieve F1 scores of 95% 
and 70% on the respective tasks.


