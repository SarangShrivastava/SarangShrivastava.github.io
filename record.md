---
layout: projects
permalink: /record/
title: Record Linking between Databases
tags: [record]
modified: 26-7-2019
comments: false
---

  <img src="{{ site.url }}/images/record.png" alt="Dp1" style="width:100%">

   <p align="justify">
   Financial firms deal with situations where multiple data vendors are onboarded to provide structured
knowledge about Legal Entities and Financial Products. While these independent views of the vendor data 
are useful, it is even better if we can have a unified view of the data across vendors. But vendor data is not clean. 
It is often accompanied with missing values, different naming conventions and misspelled entities. 
The problem gets worse because of the absence of unique identifiers across vendor data which
could be used as foreign keys to unify them. Having a unified view helps analysts and traders across multiple functions
such as making deals, initiating trades, onboarding of new clients etc. Lets looks at some of the ways by which 
we can solve this problem.</p> <br>

   <p align="justify">The first thing that we need to start with is to serialize the records - convert the tabular records into a form 
   that a machine learning algorithm can understand. While dong this, we need to do preserve the semantics around the
   notion of column headers and rows.</p> <br>

   <p align="left">S1(Row11) = | Col | Title | Val | State of Fire | Col | Category | Val | Science | Col | Price | Val | 500Rs |</p> <br>

   <p align="left">S2(Row11) = The title of the book is State of Fire. It belongs to the category fo Science. Its priced at 500Rs.</p> <br>

   <p align="justify">There could be other ways as well to serialize the tabular entries apart from the ones described above, 
   but we can stick with one of them for now. </p> <br>

   <p align="center"><img src="{{ site.url }}/images/record_2.png" alt="Dp1" style="width:90%"></p><br>

   <p align="justify">
   Once we have serialized the records, we need to generate the candidate pairs. These pairs would eventually 
   be fed into a binary classifier to make an assertion (should they be linked or not?) of the records pairs.
   Can we generate all the possible pairs and work with them? No, the solution won't scale if the number
   of records (Ex - When dealing with millions of records) is large. How do we solve this problem at scale and generate the candidate pairs in 
   less than quadratic time. Essentially, for every record in database1, we need to 
   choose a subset of the records from database2 which we will work with. Formally, this process is 
   called Blocking. We can perform an approximate nearest neighbour search in an embedding space to 
   achieve this. We can convert the serialized forms of records into embeddings using a sentence embedder model.
   We can train our own sentence embedder or use an out-of-the-box model. Once we have the embeddings, we
   can perform our nearest neighbour search using standard libraries like 'scann' or 'faiss'. A comprehensive
   comparision of these libraries is available on 'http://ann-benchmarks.com/'. </p><br>

   <p align="justify">
   Once we have the candidate pairs for each record, we can use a binary classifier to link them. Can we 
   achieve this in a zero shot setting? Can we build a baseline solution without annotating any data for
   the classification task? Can we use a Large Language Model (LLMs) for this? Yes, we can. 
   LLMs are trained on billions of tokens in a multi task setting. Recent advances with GPT3, T0pp, Flan etc have
   changed the way we interact with LLMs. We are able to interact with these LLMs as our AI assistants. 
   With the correct set of prompts (an example is shown below), we can achieve reasonable baseline 
   numbers.</p><br>

   <p align="justify">
   Prompt1 = "Given below are description of two books. Do they describe the same book? Description1:
   S2(Row11) Description2: S2(Row11) Ans: " </p><br>

   <p align="justify">
   Can we deploy this baseline solution to a production environment? The answer to this question depends
   on the constraints around the SLAs for our solution. If we need an offline process that can ran on a
   weekly or a monthly basis and perform this linking, we can think about productionizing this. 
   We won't get into the details around running these models on a CPU v/s a GPU, having a hosted solution or
   acquiring our own machines to host them in this post, probably a topic in itself for some other day.
   But if our SLAs are strict, we can use a smaller language model to perform this binary classification.
   We would need to train dataset for fine-tuning this smaller language model. Well, with proper due diligence, we 
   can cautiously roll out a beta version with our current solution to the business and take their feedback. 
   We can take us this opportunity to carefully craft annotation guidelines, refine them and leverage the
   initial feedback to bootstrap us with the initial set of training data. </p><br>

   <p align="center"><img src="{{ site.url }}/images/record_6.png" alt="Dp1" style="width:90%"></p><br>

   <p align="justify">
   When do we stop annotating and how much data is enough? We should with algorithms and models that are less
   data intensive. Can we train a small few-shot model which gives us results comparable with GPT3? Yes, Setfit
   to the rescue. This was released in late 2022 and the authors demonstrate that it has better performance
   than GPT3 on some benchmark tasks. It can be trained very easily on a classification task in a few shot 
   setting. Can we improve our results even further? We can train an ensemble of multiple orthogonal techniques
   to get to the final verdict around linking of records.</p><br>

   <p align="center"><img src="{{ site.url }}/images/record_5.png" alt="Dp1" style="width:100%"></p><br>