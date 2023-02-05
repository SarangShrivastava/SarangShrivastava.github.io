---
layout: projects
permalink: /fin-table/
title: Understanding and Resolving Hierarchical Table Structure
tags: [fin-table]
modified: 26-7-2019
comments: false
---

<img src="{{ site.url }}/images/table.png" alt="Snow" style="width:100%">
    
While many pipelines for extracting information from tables assume simple tabular structure, 
tables in the financial domain frequently have complex, hierarchical structure. 
The main example would be parent-child relationships between header cells. This is one of the long tail 
of problems when we start dealing with real world datasets. Often, understanding of this relationship is
important for many downstream ML algorithms. 

There are machine learning models that just work with the semantics of the text and then there are some which
try to understand the layout of the document. The key point here is to respect the layout information of 
the document along with the text to learn better representations which captures best of both the 
structural and the semantic world. We can often combine signals from different models but, often a pipeline
based approach in Machine learning impacts the performance of the model. So doing things in 
one shot gives better results and reduces the scope of errors which the model can make.

We can explore language models like LayoutLM which builds towards this idea and achieves state-of-the-art 
performance across many documentAI datasets. But, how much better can LayoutLM perform when we compare it
to BERT on this specific task? Is LayoutLM needed to detect the type of the cell or its real value is only
realized when we want to understand the hierarchy between column headers? We were curious about these questions
too. After a lot of experimentation, we found answers to some of these questions. We have documented our results and 
findings in this paper [here](https://openreview.net/pdf?id=B393CzcykVJ). 



