---
layout: projects
permalink: /nuances/
title: Text is not Text: Nuances of Legal text
tags: [nuances]
modified: 26-7-2019
comments: false
---

   <img src="{{ site.url }}/images/finance_nuance.png" alt="Dp1" style="width:100%">

   <p align="justify">
   The financial industry is built on data and information. Over the coming years, AI can transform 
   the way this information is developed, communicated and deployed.  We build systems that realize 
   this vision of AI: systems that leverage background knowledge, learn from experience, explain 
   themselves and interact naturally with professionals. We do all of this in the context of 
   concrete applications for our business partners which is of use to them today. </p>>
 
   <p align="justify">
   If we look at the past decade, The landscape of NLP and NLU in general has changed drastically. 
   We have come a long way from word Embeddings and recurrent neural networks to the 
   transformer/self attention based architectures to the latest buzz word in the industry GPT 3 
   which has about 175 billion parameters. </p>

   We believe extraction of knowledge from documents revolves around two key concepts  -  
   understanding the structure of documents and exploiting the semantics of the language in these
   documents.

   We are guided by the vision that the finance industry runs on documents, and it will be 
   fundamentally reshaped by the development of a computational system that can extract knowledge 
   from millions of documents (in minutes), represent it in knowledge bases, link with existing 
   databases, and deploy this knowledge for a large variety of professional tasks.

   To achieve this vision, we need to thoroughly understand the financial documents with 
   which we deal with on a day to day basis. These documents are carefully written by 
   professionals, typically designed to be precise and unambiguous. Typical examples can be 
   prospectuses, memoranda of association, trust agreements, credit agreements, NDAs, investment 
   management agreements M&A etc, the list just goes on and on. These may be made available as 
   pdfs which are typically programmatic but sometimes scanned as well. Sometimes they are 
   available in formats that are higher level than pdf, such as Word, HTML, XML etc.

   Documents are not just a big blob of running text, they are much more than that. Now lets 
   get into the details of why they are different from vanilla running text.

   The below image is a snippet of a title page which usually talks about the entity name, 
   some details about the type of the document and other similar facts scattered across the page.
   Similar to this there are Directory pages which present information in an irregular, 
   visually-organized, two-dimensional format. Directory pages are fairly common in financial 
   prospectuses and carry information about organizations, their addresses and relationships 
   between those  ; and understanding their structure is a key to various business tasks. 
   Another example of this sort can be signature pages which are often accompanied by a lot of
   hand written text and identifying things like the signature blocks becomes crucial to figure 
   out if a given agreement is executed or not.

   <img src="{{ site.url }}/images/nuance-1.png" alt="Dp1" style="width:100%">

   The text in these documents  is formally organized into sections and sub sections. There are enumerated and bulleted lists which are often wrapped up to look like a paragraph. These are quite common in Credit agreements which are full of clauses and in order to correctly extract the underlying mathetical equation, we need to understand this sentence hierarchy in depth.

   <img src="{{ site.url }}/images/nuance-2.png" alt="Dp1" style="width:100%">
   
   This snippet is full of hyperlinks. Since these documents are quite long, there is often a definition section present in the beginning of the document and then there are references to those all over the documents. If we have sections and sub sections , we’ll also have references to them. In order to understand the text in detail we need to follow those references and get the details out. 

   <img src="{{ site.url }}/images/nuance-3.png" alt="Dp1" style="width:100%">
   
4)  Another interesting paradigm that you will find in financial documents is the notion of temporality. There are inline edits and strikethroughs present in the text. If that was not enough, often these documents are accompanied by amendments which play an important role in understanding the bigger picture.  The problem even becomes more complicated when these amendments are often attached at the bottom of the main document and then we need to first establish the notion of a main doc span and then attend to all the exhibits and amendments that come in the later part of the document.

   <img src="{{ site.url }}/images/nuance-4.png" alt="Dp1" style="width:100%">