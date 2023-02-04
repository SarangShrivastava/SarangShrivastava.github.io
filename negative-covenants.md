---
layout: projects
permalink: /negative-covenants/
title: Extracting mathematical constraints from Credit Agreements
tags: [negative-covenants]
modified: 26-7-2019
comments: false
---

<p align="center">
<img src="{{ site.url }}/images/nc1.png" alt="N1" style="width:100%"></p> <br>

<p align="justify">
A Credit Agreement is a legally-binding contract, documenting the terms of a loan agreement; it is 
made between a person or party borrowing money and a lender. Lenders provide full disclosure of all of 
the loan’s terms in a credit agreement. Important lending terms included in the credit agreement 
include the annual interest rate, how the interest is applied to outstanding balances, any fees 
associated with the account, the duration of the loan, the payment terms, and any consequences for 
late payments. The english language used to define these terms is not simple, instead its quite convoluted. 
They are laid out in a way that is precise and unambiguous, which gives rise to the complex nature of the
clauses used to define these terms. </p> <br>

<p align="center">
<img src="{{ site.url }}/images/nc3.png" alt="N2" style="width:70%"></p> <br>

<p align="justify">
Lets have a look at one of these complex clauses in detail and see how we we can go about this process of
converting them into machine readable forms.</p> <br>

<p align="center">
<img src="{{ site.url }}/images/nc2.png" alt="N2" style="width:70%"></p> <br>

<p align="justify">
The first step is to recognize the individual elements that represent the structure of the constraint. 
The Relation - "not to exceed", the Operator, "the greater of" and "the lesser of" , 
the Governors - "Consolidated Total Assets" and "Consolidated Adjusted EBIDTA", the Objects - "$100,000,000", 
"11.5%", "45%" and "$200m". All these elements can be extracted by simple methods like dictionary spotting or by 
training much complex sequence taggers. We can train multiple individual sequence taggers, or jointly train a sequence 
tagger which models all the above elements. We can use language models which are pretrained on public 
legal or we can pre-train a language model specifically on Credit agreements from scratch to further improve the accuracy of
our sequence tagger. There are 
multiple ways to proceed further, which one should we chose? We are often faced with this dilemma and the solution for this
is to quickly build a baseline solution and iterate upon. This helps us to benchmark the improvements which the advanced 
techniques might provide.  </p> <br>

<p align="justify">
Preliminary data analysis can provide useful insights for modelling our solutions. Ex - when we see 
an Object, we actually know that there is a Governor, and if the object is a percentage, the 
recognition can benefit from joint inference by a sequence tagger. Adopting a simple method of 
dictionary spotting for the governors, and regular expressions for the Objects can be a good baseline
solution. For Temporality, dictionary spotting is not very straightforward and hence we would want 
to train a sequence tagger for it.</p> <br>

<p align="center">
<img src="{{ site.url }}/images/negative_covenants_4.png" alt="N4" style="width:70%"></p><br>

<p align="justify">
Once the individual elements are extracted, we need to establish the relation, or the 
interdependencies between them. Objects belong to the Operators, Operators need to be 
linked to a Relation. We can train a relation extraction model by constructing our own features and
feeding them to a random forest based classifier, or we can train a more complex relation extraction model
sitting on top of a BERT base backbone. An important thing that we need to understand is, Are these Objects nested, or are they at 
the same level. Sometimes there are markers in the text - "(x)", "(y)", "(z)" which can provide soft signals for our
algorithm. But not all the cases are explicitly marked, Ex - the content of node z is not marked, 
there are two elements in that node which 
are not segregated explicitly by the markers. We can train a classifier that does a binary decision for 
each of these questions. </p> <br>

<p align="justify">
Once we have this structure detected, we would want to normalize it and link to a knowledge base. 
We want to normalize the Provision and Type as well. The number of normalized provisions and types are limited 
in number - a key piece of information which the business desks can provide us. We can also use the 
title stack - the section hierarchy of the document where this text 
is being talked about for adding additional context for the Type and Provision classifier. </p> <br>

<p align="justify">
We can provide easy access of the extracted terms in a Web UI. We can show all the terms we are 
extracting in a nice tabular view and save analysts a lot of time and money. We can even 
do a powerful semantic search over multiple Credit Agreements. Some example queries could be - Show me all 
terms with capital lease over $50 million, Show me a tech company with a leverage maintenance covenant, 
Given these 50 companies, do they contain a cap on the cost savings ? </p> <br>

<p align="center">
<img src="{{ site.url }}/images/negative_covenants_6.png" alt="N6" style="width:70%"></p>
