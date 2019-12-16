---
categories:
- RStudio
description: this is meta description
draft: false
image: images/data.jpg
tags:
- RSudio
- New
title: Data Wranglin' 
type: "post"
---

In my computational biology class, our first project using RStudio focused on data wrangling and data exploration. The following post captures some of the highlights from my project, but excludes the more caveman-like tidying performed. I'm sure there was a more delicate way to forge a cohesive dataset, but big hammer do trick.

![image](/images/caveman.png)

__The code in its entirety can be found [here](/Project1)__

Both data sets were found on the Center for Disease Control website for the 2015 year. The Cause of Death (COD) data set has information on the five leading causes of death for each state in the U.S.. Interesting variables include projected number of deaths for each state due to a specific cause of death and whether that state exceeding that projection, quantified using a percentage. The diabetes data set information was a subset of data from chronic disease indicators. My interest in healthcare and nutrition prompted me to choose these data sets. I ultimately wanted to determine whether there was a relationship between states that had poor nutrition (high incidence of diabetes) and higher than expected rates of mortality. Overall, there was low correlation between selected variables. This could be due to high prevalance of NAs in the diabetes data set. In the future, I'd like to investigate how the prevalence of NAs for a particular state corresponds to that state's health outcomes - how a lack of complete data could be indicative of real ______. 


```{r include=F}
library(ggplot2)
library(tidyr)
library(tidyverse)
diabetes <- read.csv("~/Desktop/website/content/blog/Diabetes.csv")
COD <- read.csv("~/Desktop/website/content/blog/ExcessDeaths.csv")
COD_Canc <- COD %>% select(-HHS.Region) %>% filter(Age.Range == "0-49", Locality == "All", Benchmark == "Floating", Cause.of.Death == "Cancer")
COD_HD <- COD %>% select(-HHS.Region) %>% filter(Age.Range == "0-49", Locality == "All", Benchmark == "Floating", Cause.of.Death == "Heart Disease")
COD_St <- COD %>% select(-HHS.Region) %>% filter(Age.Range == "0-49", Locality == "All", Benchmark == "Floating", Cause.of.Death == "Stroke")
```