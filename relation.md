---
layout: projects
permalink: /relation/
title: From Structure to Knowledge
tags: [relation]
modified: 26-7-2019
comments: false
---

<img src="{{ site.url }}/images/relation-extraction-0.png" alt="Dp1" style="width:100%"> <br>

<p align="justify">
Documents in the Client Onboarding space of the financial 
industry are rich with legal entities and their functions. These document are very long and they have information present in 
both structured and non structured format. People want to know what kind of a customer document is this 
? Who are the individuals and  organizations described in these documents, how are they related to the principals being 
on-boarded, what are their roles, addresses etc.? Is there documentation that this counter-party has the 
capacity to buy specific products from us? Has the beneficial owner authorized the counterparty to
operate on their behalf? Is the document executed? What is its effective date? These are some of 
the key facts that people are after and it requires us to understand the semantics of the language
of these documents. </p> <br>

<p align="justify">
The technical challenges behind addressing these tasks are diverse, immense and exciting. Some of 
them are achievable by directly using products in the marketplace, some require adaptation of 
existing technology (e.g. retraining of models based on GS data-sets, development of variants of 
these techniques), some require new research and some require the development of completely new 
approaches. </p><br>

<p align="center"><img src="{{ site.url }}/images/relation-extraction-3.png" alt="Dp1" style="width:50%"></p> <br>

<p align="justify">
The Named Entity Recognition task in general can span from identifying a few tokens like  in the case of Persons or 
Organizations to Addresses which are pretty long. People are specifically interested in knowing 
the various entities that are being talked about in these documents with their registered 
and mailing addresses. There are open source tools/libraries which help in identifying 
organizations and persons but none of them are trained in the financial domain.  Although 
this fact cannot be neglected that these models have been trained on very large datasets and 
they have learnt some latent representations to represent entities and we would want to leverage 
it. In order to leverage transfer learning, we created our own dataset and 
fine tuned Spacy. As expected we got much better results that what Spacy provided out of 
the box. Spacy underneath the hood uses a CNN based neural architecture with a few tweaks. Lately, Spacy 3.0 was 
released which supports fine tuning of transformer based architectures as well.</p> <br>

<p align="center">
<img src="{{ site.url }}/images/relation-extraction-4.png" alt="Dp1" style="width:50%"> </p> <br>

<p align="justify">
Since address extraction is much more custom and complex in nature, we used a BERT 
base backbone with a token classification head on top of it to solve this. To give a brief 
insight about the complexity around addresses, addresses of every country are represented in a 
different formats, lines like C/O Org are often appended at the beginning of these addresses, 
Addresses that are parts of islands are even more complex as there might not be a standard 
concept of cities and states in them. We used Libpostal to parse these address spans but 
unfortunately since it is trained on street addresses from google, it did not perform upto our 
expectations and we forced us to develop our own gazetteer for this. </p> <br>

<p align="center">
<img src="{{ site.url }}/images/relation-extraction-5.png" alt="Dp1" style="width:75%"></p> <br>

<p align="center">
<img src="{{ site.url }}/images/relation-extraction-1.png" alt="Dp1" style="width:75%"></p> <br>

<p align="justify"> 
Now lets look at the Relation extraction tasks. Be it identification of the address of a particular organization or 
identifying their aliases, both the tasks are relation extraction tasks at the ground level. The variability in the 
input again is the key here. These relationships are present both in the structured / unstructured manner in these 
documents. The task here can get quite complicated very easily. Just by adding an extra word towards the end of the sentence 
, the number of relations present in the examples below changes. </p> <br>

<p align="left"> 
1)   A , B acts as C , D to E and F     
2)   A , B acts as C , D to E and F respectively </p>><br>

<p align="justify">
We curated a ternary relation extraction dataset amongst organizations, person names and roles. We then used a BERT 
based backbone with a relation head on top of it to solve this problem.  An important part of this 
task was to decide which specific token embedding should we forward to the relation head. There are many 
techniques involved where people used max pooling or averaging all the token embeddings that represents the entities
and feed that to the relation layer. To make the network aware of the presence of specific tokens, we also used entity
markers around the Orgs and roles which helped us to achieve better results. </p> <br>

<p align="justify">
By implementing these entity and relation extraction models, we reduced review time of cases from a few hours to a 
couple of minutes when a new onboarding of a client takes place </p> <br>

<p align="center">
<img src="{{ site.url }}/images/relation-extraction-2.png" alt="Dp1" style="width:75%"></p>
