# Week 04 Join tables

Data wrangling is when you prepare the data for the analysis. A key aspect is joining data tables. AI can help design the process, and give you code to do that. 

### Objectives summary: 
Learn how to organize data in a tidy way, join multiple datasets,  choose variables to answer a research question and create a reproducible workflow to analyze data.

### Learning Objectives

* Learn how to store information in a tidy way.
* Work with relational data.
* Join tables

### before class
* Background reading: Békés-Kézdi (2021) Chapter 2
* Download data from [Here](/week04/data/modified) or Moodle. It is a set of csv files such as 'cities_modified'
* The data [description is available here](/week04/data/hotel-data-readme.md) 

## Class Plan


### Task 1: Use AI to understand these terms. Ask examples. (Individual)
* tidy data table
* relational datasets,
  * schema,
  * primary and foreign key
  * composite key
* joining tables
  * different types of join
  * 1:1, 1:m
* joining tables in your language (python, R, Stata)

This is followed by a discussion.

## Task 2: Form 2-3 groups of people using same coding language

Use the data you downloaded to carry out joins and inspect results. Use AI but inspect. 

## 1:1

1. Compare left, right, inner, outer joins. 
  *  what happens to N?

## 1:m

2. Start: Tabulate the frequency of hotels by city_hotel_counts

3. Cities to Hotels
  * one city joins to multiple hotels
  * filter on 2 cities for easier visibility

4. Join hotel and occupancy 1
  * m:1

5. Join hotel and occupancy  2
  * get hotel level
  * trick: aggregate 

6. Join on composite key

* create a data table at city-year-match level showing average occupancy and tourist arrivals

## home assignment

* Create groups of 2-3 people who use the same coding language. 

* Ask AI to give you a list of research questions that can be answered using many (at least 4) of the hotel data sets provided. Iterate with AI to find an interesting question using a persona. 

* Write code that joins the required data
* Write code to do the analysis (conditional comparison / some simple regression)

* Produce a figure that shows the answer (or a simple version of the answer) to the research question (e.g. scatterplot and regression line, or boxplot, etc)

* Create a min. 6 - max. 10 pages slide show to illustrate the research question, the merging process, the figure and the conclusion.

For example, you can use the following slide show structure, each bit is 1-2 slides:
* Research question and why/for whom you picked it
* Data and variables
* Detailed steps of joining tables to get to the work data (here be specific, 2-4 slides)
* Steps of creating my variables for analysis
* Result and interpretation

Submit: 
1. Slideshow in pdf format: “lastname1_lastname2_lastname3_slides.pdf”
2. Reproducible code “lastname1_lastname2_lastname3_code.pdf”


