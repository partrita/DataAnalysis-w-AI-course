# Week02: Code and data discovery and documentation with AI

# Objectives 

## Summary

Sometimes data is large and discovery is hard. Sometimes you need to write data documentation. LLMs can help. You will learn how to write a clear and professional README. We use a cleaned subset of the 7th Wave of the World Values Survey (WVS). We'll also talk some tech on documentation. 

## Learning Objectives:

* Understand how to document a new dataset using as an example th WVS 7th wave data.
* Create a README that describes data.
* Learn to refine documentation by incorporating iterative feedback from peers and AI tools.

## Preparation BEFORE class

### Reading and review

* Background reading: Békés-Kézdi (2021) Chapters 1-3, in particular [core background info](/week02/assets/da-background.md) 
* Some discussion of data types [Data Management in Large-Scale Education Research](https://datamgmtinedresearch.com/structure) by Crystal Lewis
  
### Get data and info: 

Access the [VWS dataset](/data/VWS)
1. Data [WVS_subset.csv](/data/VWS/WVS_subset.csv)   --  subset of the 7th Wave of WVS dataset
2. Data: [WVS_random_subset.csv](/data/VWS/WVS_random_subset500.csv) - random subset from each country, small version
3. Download its official [codebook documentation](/data/VWS/codebook.pdf) 

If you prefer datasets are also at [OSF, Gabors Data Analysis / World Values Survey](https://osf.io/mfd6s/)

# Class plan 

## I. Background

### About Markdown

* Editor in R, Python [Quarto](https://quarto.org/)
* Online [Markdown editor](https://jbt.github.io/markdown-editor/)
* Also: [Pandoc](https://pandoc.org/) 

### What is a good readme?

**Some examples for reproduction package**

* Békés-Kézdi (2021) [Hotels dataset](https://gabors-data-analysis.com/datasets/hotels-europe/) -- show basics
* Koren-Pető (2021) [Business disruptions from social distancing](https://zenodo.org/records/4016325/preview/README.md?include_deleted=0) as [PDF](https://zenodo.org/records/4016325/files/README.pdf?download=1)

* Some ideas on readme:  [Makereadme](https://www.makeareadme.com/), [Social Science Editors](https://social-science-data-editors.github.io/template_README/)


**Key ingredients**

* Overview of project
* license 
* All datasets (data tables) separately discussed
* All key variables described (name, content, type, coverage (% share missing)
  * maybe also: source, extension (csv / xlsx/ parquet)

### What is a variable dictionary

* more details of a dataset, often as xlsx
* metric (euro, %), meaning of values if categorical
* maybe even mean, min, max

** Example**

* Békés-Kézdi (2021) [Bisnode dataset variables](https://osf.io/9a3t4)

## II. Work on data

### No AI

* Download and look at the Random Subset data
* Start collecting some info on the data

### AI: Learning and idea generation

* Start asking for skeleton readme, like [Good Readme](https://chatgpt.com/share/67bc35fc-080c-8000-8e06-30b997c6781e)
* Take a picture of a repo and ask to add
* Write a full prompt following iterations

### Cyborg mode: create a readme with AI
* Get AI to design a README TEMPLATE for this task.
* Get a draft
* Understand and edit draft

# Assignment

See suggested [assignment for week 02](assignment/assignment_02.md)

