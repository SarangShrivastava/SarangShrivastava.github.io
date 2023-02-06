---
layout: projects
permalink: /nuances/
title: Text is not Text- Nuances of Legal text
tags: [nuances]
modified: 26-7-2019
comments: false
---
   
   <img src="{{ site.url }}/images/finance_nuance.png" alt="Dp1" style="width:100%">
   
  <p align="justify">
   The financial industry is built on data and information. We want to build systems 
   that leverage background knowledge, learn from experience, explain 
   themselves and interact naturally with professionals. Hence understanding 
of the nuances of legal text and treating it as first class citizen is crucial before we solve any downstream
machine learning task involving them.</p> <br>

  <p align="justify">
   Financial documents are carefully written by 
   professionals, typically designed to be precise and unambiguous. Typical examples can be 
   prospectuses, memoranda of association, trust agreements, credit agreements, NDAs, investment 
   management agreements M&A etc, the list just goes on and on. These may be made available as 
   pdfs which are typically programmatic but sometimes scanned as well. Sometimes they are 
   available in formats that are at higher level than pdf, such as Word, HTML, XML etc.
   These documents are not just a big blob of running text, they are much more than that.
   Extraction of knowledge from these documents revolves around two key concepts  -  
   understanding the structure of documents and exploiting the semantics of the language in these
   documents. Lets get into some of the details of why they are different from vanilla running text. </p> <br>

   <p align="center"><img src="{{ site.url }}/images/nuance-complete.png" alt="Dp1" style="width:100%"></p>

   * <p align="justify">
   The below image is a snippet of a Title page which usually talks about the entity name, 
   some details about the type of the document and other similar facts, scattered across the page.
   Similar to this there are Directory pages which present information in an irregular, 
   visually-organized, two-dimensional format. Directory pages are fairly common in financial 
   prospectuses and carry information about organizations, their addresses and relationships 
   between those; and understanding their structure is a key to various business tasks. 
   Another example of this sort can be signature pages which are often accompanied by a lot of
   hand written text and identifying things like the signature blocks becomes crucial to figure 
   out if a given agreement is executed or not. </p> <br>

   <p align="center"><img src="{{ site.url }}/images/nuance-1.png" alt="Dp1" style="width:75%"></p>

   * <p align="justify">
   The text in these documents is formally organized into sections and sub sections. There are 
   enumerated and bulleted lists which are often wrapped up to look like a paragraph. These are 
   quite common in Credit agreements which are full of clauses and in order to correctly extract 
   the underlying mathematical constraints represented in english text, we need to understand 
   this sentence hierarchy in depth.</p> <br>

   <p align="center"><img src="{{ site.url }}/images/nuance-3.png" alt="Dp1" style="width:75%"></p>
   
   * <p align="justify"> 
   This snippet is full of hyperlinks. Since these documents are quite long, there is often a 
   definition section present in the beginning of the document and then there are references to 
   those all over the documents. If we have sections and sub sections , we’ll also have references
   to them. In order to understand the text in detail we need to follow those references and get 
   the details out. </p> <br>

   <p align="center"><img src="{{ site.url }}/images/nuance-2.png" alt="Dp1" style="width:75%"></p>

   * <p align="justify">
   Another interesting paradigm that you will find in financial documents is the notion of 
   temporality. There are inline edits and strikethroughs present in the text. If that was not 
   enough, often these documents are accompanied by amendments which play an important role in 
   understanding the bigger picture.  The problem even becomes more complicated when these 
   amendments are often attached at the bottom of the main document, which forces us then to first 
   establish the notion of a main document span and then attend to all the exhibits and amendments 
   that come in the later part of the document.</p> <br>

   <p align="center"><img src="{{ site.url }}/images/nuance-4.png" alt="Dp1" style="width:75%"></p>