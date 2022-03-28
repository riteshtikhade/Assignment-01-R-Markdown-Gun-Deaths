# Assignment-01-R-Markdown-Gun-Deaths
ANA 515 Assignment 1

---
title: "ANA 515 Assignment 1"
author: Ritesh Tikhade
date: 3/26/2022
output: 
  html_document:
  theme: cerulean
---
```{r setup, include = FALSE}
library(dplyr)
library(knitr)
library(bslib)
library(tidyverse)
url <- "https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv"
gun_deaths <- read.csv(url)
youth <- gun_deaths %>% 
  filter(age <= 65)
summary(youth)
```
We have data about `r nrow(gun_deaths)` individuals killed by guns. Only `r nrow(gun_deaths)-nrow(youth)` are older than 65. The distribution of the 

# Gun deaths by age 
```{r youth-dist, echo = FALSE} 
youth %>% 
ggplot(aes(age)) + 
geom_freqpoly(binwidth = 1)
```
# Gun deaths by race 
```{r race-dist, echo = FALSE} 
youth %>% 
ggplot(aes(fct_infreq(race) %>% fct_rev())) + 
geom_bar() + coord_flip() + 
labs(x = "Victim race") 
```

