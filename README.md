<h1 align ='center'> <u>Document-Similarity</u> </h1>
Natural Language Processing based technique to identify the similarity among the provided documents.

In this, two methods implemented using Python in Jupyter notebook.

Method-1: Cosine Similarity: Convert the documents from text to vectors manually based on the count of a word in a particular document occured, then we will calculate the cosine value through inner product of vectors.

Method-2: TF-IDF Based Cosine Similarity: TF-IDF( Term Frequency - Inverse Document Frequency) will be used for vectorization of documents. It can be partitioned into two.

1. TF (Term Frequency): TF is the number of times a term appears in a particular document. So it’s specific to a document. A few of the ways to calculate tf is given below:-

   tf(t) = No. of times term ‘t’ occurs in a document
   
   or
   
   tf(t) = (No. of times term ‘t’ occurs in a document) / (No. Of terms in a document)
   
   or
   
   tf(t) = (No. of times term ‘t’ occurs in a document) / (Frequency of most common term in a document)
   
   sklearn uses the first one i:e No. Of times a term ‘t’ appears in a document
   
2. IDF (Inverse Document Frequency): IDF is a measure of how common or rare a term is across the entire corpus of documents. So the point to note is that it’s common to all the documents. If the word is common and appears in many documents, the idf value (normalized) will approach 0 or else approach 1 if it’s rare. A few of the ways we can calculate idf value for a term is given below.

   
This article was published as a part of the Data Science Blogathon.

Overview
In NLP, tf-idf is an important measure and is used by algorithms like cosine similarity to find documents that are similar to a given search query.

Here in this blog, we will try to break tf-idf and see how sklearn’s TfidfVectorizer calculates tf-idf values. I had a hard time matching the tf-idf values generated by TfidfVectorizer and with the ones I calculated. The reason is that there are many ways in which tf-idf values are calculated, and we need to be aware of the method that TfidfVectorizer uses to calculate tf-idf. This will save a lot of time and effort for you. I spent a couple of days troubleshooting before I could realize the issue.

We will write a simple Python program that uses TfidfVectorizer to calculate tf-idf and manually validate this. Before we get into the coding part, let’s go through a few terms that make up tf-idf.

What is Term Frequency (tf)
tf is the number of times a term appears in a particular document. So it’s specific to a document. A few of the ways to calculate tf is given below:-

tf(t) = No. of times term ‘t’ occurs in a document


ML Hackathon: The Sledge Hack is live now!
Predict no. of runs Virat and Rohit will score in Ind vs Aus Upcoming World Cup Clash

OR

tf(t) = (No. of times term ‘t’ occurs in a document) / (No. Of terms in a document)

OR

tf(t) = (No. of times term ‘t’ occurs in a document) / (Frequency of most common term in a document)

sklearn uses the first one i:e No. Of times a term ‘t’ appears in a document

Inverse Document Frequency (idf)
idf is a measure of how common or rare a term is across the entire corpus of documents. So the point to note is that it’s common to all the documents. If the word is common and appears in many documents, the idf value (normalized) will approach 0 or else approach 1 if it’s rare. A few of the ways we can calculate idf value for a term is given below

idf (t) =1 + log e [ n / df(t) ]

OR

idf(t) = log e [ n / df(t) ]

where

n = Total number of documents available

t = term for which idf value has to be calculated

df(t) = Number of documents in which the term t appears

 

But as per sklearn’s online documentation, it uses the below method to calculate idf of a term in a document.

idf(t) = log e [ (1+n) / ( 1 + df(t) ) ] + 1 (default i:e smooth_idf = True)

and

idf(t) = log e [ n / df(t) ] + 1 (when smooth_idf = False)



This article was published as a part of the Data Science Blogathon.

Overview
In NLP, tf-idf is an important measure and is used by algorithms like cosine similarity to find documents that are similar to a given search query.

Here in this blog, we will try to break tf-idf and see how sklearn’s TfidfVectorizer calculates tf-idf values. I had a hard time matching the tf-idf values generated by TfidfVectorizer and with the ones I calculated. The reason is that there are many ways in which tf-idf values are calculated, and we need to be aware of the method that TfidfVectorizer uses to calculate tf-idf. This will save a lot of time and effort for you. I spent a couple of days troubleshooting before I could realize the issue.

We will write a simple Python program that uses TfidfVectorizer to calculate tf-idf and manually validate this. Before we get into the coding part, let’s go through a few terms that make up tf-idf.

What is Term Frequency (tf)
tf is the number of times a term appears in a particular document. So it’s specific to a document. A few of the ways to calculate tf is given below:-

tf(t) = No. of times term ‘t’ occurs in a document


ML Hackathon: The Sledge Hack is live now!
Predict no. of runs Virat and Rohit will score in Ind vs Aus Upcoming World Cup Clash

OR

tf(t) = (No. of times term ‘t’ occurs in a document) / (No. Of terms in a document)

OR

tf(t) = (No. of times term ‘t’ occurs in a document) / (Frequency of most common term in a document)

sklearn uses the first one i:e No. Of times a term ‘t’ appears in a document

Inverse Document Frequency (idf)
idf is a measure of how common or rare a term is across the entire corpus of documents. So the point to note is that it’s common to all the documents. If the word is common and appears in many documents, the idf value (normalized) will approach 0 or else approach 1 if it’s rare. A few of the ways we can calculate idf value for a term is given below

idf (t) =1 + log e [ n / df(t) ]

OR

idf(t) = log e [ n / df(t) ]

where

n = Total number of documents available

t = term for which idf value has to be calculated

df(t) = Number of documents in which the term t appears

 

But as per sklearn’s online documentation, it uses the below method to calculate idf of a term in a document.

idf(t) = log e [ (1+n) / ( 1 + df(t) ) ] + 1 (default i:e smooth_idf = True)

and

idf(t) = log e [ n / df(t) ] + 1 (when smooth_idf = False)

 

Term Frequency-Inverse Document Frequency (tf-idf): tf-idf value of a term in a document is the product of its tf and idf. The higher is the value, the more relevant the term is in that document.

 

