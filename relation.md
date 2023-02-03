---
layout: projects
permalink: /relation/
title: Ternary Relation extraction in Prospectuses
tags: [relation]
modified: 26-7-2019
comments: false
---

   <img src="{{ site.url }}/images/relation-extraction-1.png" alt="Dp1" style="width:100%">
      
  * Answering questions like ”Who is the Legal advisor of Amazon for this fund offerring?
  * Curated a ternary relation extraction dataset amongst organizations, person names and roles
  * Developed a BERT-based model leveraging entity markers to enrich entity embeddings sent to the relation head
  * Reduced review time of cases from a few hours to a couple of minutes when a new onboarding of a client takes place

Now lets look at the Relation extraction task. Be it identification of the address of a particular organization or identifying their aliases, both the tasks are relation extraction tasks at the ground level.  The variability in the input again is the key here.  These relationships are present both in the structured / unstructured manner in these documents.  The example that you see in this slide specifically involves finding relation between Organizations and Roles form running text. We will shortly see an example where the same information is presented in a more structured manner. 

As you can see the task here can get quite complicated very easily.   Example - 

A , B acts as C , D to E and F     
2)   A , B acts as C , D to E and F respectively 

Just by adding an extra word towards the end of sentence , the number of relations present in the example changes.

We used a BERT based backbone with a relation head on top of it to solve this problem.  An important part of this task is to decide which specific token embedding would you take and forward it to the relation head. There are many techniques involved where people used max pooling or averaging all the token embeddings that represents the entities and feed that to the relation layer. To make the network aware of the presence of specific tokens, we also used entity markers around the Orgs and roles which helped us to achieve better results.