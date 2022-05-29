# ANA-515-Assignment-1
Assignment 01: R Markdown Gun Deaths 


---
title: "ANA 515 Assignment 1"
author: "Saikiran Patel"
date: "30/05/2022"
output:
  word_document: default
  html_document:
    theme:
      bootswatch: minty
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
```{r}
#install.packages("tidyverse")
#install.packages("knitr")
#install.packages("bslib")
```
```{r}
library(tidyverse)
library(knitr)
library(bslib)
```
```{r}
mydata <- read_csv("https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv")
```
```{r}
youth<-filter(mydata, age <= 65) 
youth
summarise(youth)
```
#Gun deaths by age
```{r youth-dist, echo=FALSE}
youth %>%
  ggplot(aes(x=age, colour="cond"))+
  geom_freqpoly(binwidth=1)

```
#Gun deaths by race
```{r race-dist, echo=FALSE}
youth %>%
  ggplot(aes(x=fct_infreq(race)%>%fct_rev(), fill="cond"))+
  geom_bar() + coord_flip() +
  labs(x="Victim race")
```

