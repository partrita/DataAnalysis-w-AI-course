# Week 04 Join tables

## About the class
Data wrangling is when you prepare the data for the analysis. A key aspect is joining data tables. AI can help design the process, and give you code to do that. 

### Objectives summary: 
Learn how to organize data in a tidy way, join multiple datasets,  choose variables to answer a research question and create a reproducible workflow to analyze data.

### Learning Objectives

* Learn how to store information in a tidy way.
* Work with relational data.
* Join tables
* Use AI to explain complex concepts

### Before class
* Background reading: Békés-Kézdi (2021) Chapter 2
* Download data from [Here](/week04/data/modified) or Moodle. It is a set of csv files such as 'cities_modified'
* The data [description is available here](/week04/data/hotel-data-readme.md) 

## Class Plan

### Recap

* Discuss assignment 03


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

1. Join hotels and cities. Compare left, right, inner, outer joins. 
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

## Advice, ideas

* discuss and collect ideas from  AI
* learn to focus on key suggestions (AI can go nuanced and not important points easily)

## Home Assignment

Suggested assignment [[/assignments/assignment_04.md](/assignments/assignment_04.md)]
