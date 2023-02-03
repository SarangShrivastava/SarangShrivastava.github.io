---
layout: projects
permalink: /table/
title: Understanding and Resolving Hierarchical Table Structure
tags: [table]
modified: 26-7-2019
comments: false
---

  <img src="{{ site.url }}/images/table.png" alt="Snow" style="width:100%">
    
 While many pipelines for extracting information from tables assume simple table structure, tables in the financial domain frequently have complex, hierarchical structure. The main example would be parent-child relationships between header cells.

The tables are selected from IBM FinTabNet, a much larger dataset of more than 100,000 financial tables having cell, row, and column bounding boxes extracted by deep learning, but not including semantic cell type or cell-to-cell relation labels, which we add.

We fine-tune models based on LayoutLM on the cell-type classification task and on the identification of hiearchical relations among column headers. We achieve F1 scores of 95% and 70% on the respective tasks.


