# Data Science Specialization Capstone Project - Johns Hopkins University on Courera

## Introduction to Natural Language Processing

Around the world, people are spending an increasing amount of time on their mobile devices for email, social networking, banking and a whole range of other activities. But typing on mobile devices can be a serious pain. SwiftKey, our corporate partner in this capstone, builds a smart keyboard that makes it easier for people to type on their mobile devices. One cornerstone of their smart keyboard is predictive text models. When someone types:

*I went to the*

the keyboard presents three options for what the next word might be. For example, the three words might be gym, store, restaurant. In this capstone you will work on understanding and building predictive text models like those used by SwiftKey.

This course will start with the basics, analyzing a large corpus of text documents to discover the structure in the data and how words are put together. It will cover cleaning and analyzing text data, then building and sampling from a predictive text model. Finally, you will use the knowledge you gained in data products to build a predictive text product you can show off to your family, friends, and potential employers.

You will use all of the skills you have learned during the Data Science Specialization in this course, but you'll notice that we are tackling a brand new application: analysis of text data and natural language processing. This choice is on purpose. As a practicing data scientist you will be frequently confronted with new data types and problems. A big part of the fun and challenge of being a data scientist is figuring out how to work with these new data types to build data products people love. The capstone will be evaluated based on the following assessments:

1. An introductory quiz to test whether you have downloaded and can manipulate the data.
2. An intermediate R markdown report that describes in plain language, plots, and code your exploratory analysis of the course data set.
3. Two natural language processing quizzes, where you apply your predictive model to real data to check how it is working.
4. A Shiny app that takes as input a phrase (multiple words), one clicks submit, and it predicts the next word.
5. A 5 slide deck created with R presentations pitching your algorithm and app to your boss or investor.

During the capstone you can get support from your fellow students, from us, and from the engineers at SwiftKey. But we really want you to show your independence, creativity, and initiative. We have been incredibly impressed by your performance in the classes up until now and know you can do great things.

We have compiled some basic natural language processing resources below. You are welcome to use these resources or any others you can find while performing this analysis. One thing to keep in mind is that we do not expect you to become a world's expert in natural language processing. The point of this capstone is for you to show you can explore a new data type, quickly get up to speed on a new application, and implement a useful model in a reasonable period of time. We think NLP is very cool and depending on your future goals may be worth studying more in-depth, but you can complete this project by using your general knowledge of data science and basic knowledge of NLP.

## Course Dataset - from Johns Hopkins University

This is the training data to get you started that will be the basis for most of the capstone. You must download the data from the link below and not from external websites to start.

* [https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip](https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip)

The first step in analyzing any new data set is figuring out: (a) what data you have and (b) what are the standard tools and models used for that type of data. Make sure you have downloaded the data from Coursera before heading for the exercises. This exercise uses the files named LOCALE.blogs.txt where LOCALE is the each of the four locales en_US, de_DE, ru_RU and fi_FI. The data is from a corpus called HC Corpora. See the About the Corpora reading for more details. The files have been language filtered but may still contain some foreign text.

In this capstone we will be applying data science in the area of natural language processing. As a first step toward working on this project, you should familiarize yourself with Natural Language Processing, Text Mining, and the associated tools in R. Here are some resources that may be helpful to you.

* [Natural language processing Wikipedia page](https://en.wikipedia.org/wiki/Natural_language_processing)
* [Text mining infrastructure in R](https://www.jstatsoft.org/article/view/v025i05)
* [CRAN Task View: Natural Language Processing](https://cran.r-project.org/web/views/NaturalLanguageProcessing.html)

## Data Mining

I have completed an initial data mining exercise that gives insight to the scope of the given datasets.  This data mining exercise is documented in an R markdown document, available here within this repository, and the document is identified as **data-mining.md**.

One of the first things that I did was to identify that I will want to run R Studio on my machine with cache, so I configured my R markdown document accordingly.  I then used the readLines() function, as instructed within this course, to read the given text files into character vectors of length equal to the number of lines.  For human visualization, I used the head() function to output the first 6 lines of each character vector.  I then used the length() and the max() functions to learn the following:

1. The Twitter data contains 2,360,148 lines and the largest entry is 140 characters (300 Mb).
2. The Blog data contains 899,288 lines and the largest entry is 40,833 characters (250 Mb).
3. The News data contains 77,259 lines and the largest entry is 5,760 characters (20 Mb).

With some other general data exploration techniques, I got familiar with the datasets.  For the purposes of this initial exercise, I believed it was adequate to draw a random sample from each of these large files so that I could simply infer some general characteristics about the datasets as a whole.

As instructed per this exercise, I used the **tm package** (Text Mining) to create a Corpus, and I then used some **tm_map** methods to conduct some cleaning exercises on this data.  I took some steps to remove non-graphical characters, profanity, punctuation, numbers, and whitespace.  I then drew on some work from Chiara Mondino for the preparation of my data exploration techniques.  I found that the sorted visualization of the most popular words and word combinations to be very intuitive even to a non-technical reviewer of this work.

In my conclusions, I observed that the general removal of all punctuation did not produce acceptable results.  There are many common words within the english language which are presented in the form of a conjunction with the apostrophe.  I will find it very important with future stages of this project that this anomoly is corrected.

## Prediction Model






