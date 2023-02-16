---
title: "Lab 9 Homework"
author: "Gabriel Jones"
date: "`r Sys.Date()`"
output:
  html_document:
    theme: spacelab
    keepmd: yes
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the libraries
```{r message=FALSE, warning=FALSE}
library(tidyverse)
library(janitor)
library(here)
library(naniar)
``` 

For this homework, we will take a departure from biological data and use data about California colleges. These data are a subset of the national college scorecard (https://collegescorecard.ed.gov/data/). Load the `ca_college_data.csv` as a new object called `colleges`.
```{r}
colleges <- read.csv("data/ca_college_data.csv")
```

The variables are a bit hard to decipher, here is a key:  

INSTNM: Institution name  
CITY: California city  
STABBR: Location state  
ZIP: Zip code  
ADM_RATE: Admission rate  
SAT_AVG: SAT average score  
PCIP26: Percentage of degrees awarded in Biological And Biomedical Sciences  
COSTT4_A: Annual cost of attendance  
C150_4_POOLED: 4-year completion rate  
PFTFTUG1_EF: Percentage of undergraduate students who are first-time, full-time degree/certificate-seeking undergraduate students  

1. Use your preferred function(s) to have a look at the data and get an idea of its structure. Make sure you summarize NA's and determine whether or not the data are tidy. You may also consider dealing with any naming issues.
```{r}
view(colleges)
```

```{r}
colleges%>%
  summarise_all("anyNA")
```

```{r}
colleges <- colleges%>%
  rename_with("tolower")
colleges
```

2. Which cities in California have the highest number of colleges?
```{r}
colleges%>%
  summarise(city)%>%
  count(city)%>%
  slice_max(order_by = n, n=1)
```

3. Based on your answer to #2, make a plot that shows the number of colleges in the top 10 cities.
```{r}
colleges%>%
  summarise(city)%>%
  count(city)%>%
  slice_max(order_by = n, n=10)%>%
  ggplot(aes(city, n))+
  geom_col()
```

4. The column `COSTT4_A` is the annual cost of each institution. Which city has the highest average cost? Where is it located?
```{r}
colleges%>%
  group_by(city)%>%
  summarise(costt4_a_mean=mean(costt4_a, na.rm=T))%>%
  slice_max(order_by = costt4_a_mean)
```

5. Based on your answer to #4, make a plot that compares the cost of the individual colleges in the most expensive city. Bonus! Add UC Davis here to see how it compares :>).
```{r}
colleges%>%
  filter(city=="Claremont")%>%
  summarise(instnm, costt4_a)%>%
  arrange()
```

6. The column `ADM_RATE` is the admissions rate by college and `C150_4_POOLED` is the four-year completion rate. Use a scatterplot to show the relationship between these two variables. What do you think this means?
```{r}
colleges%>%
  ggplot(aes(adm_rate, c150_4_pooled))+
  geom_point()
# The more admissions a college has, the lower it's four year completion rate is. This means less people graduate in 4 years the larger the university is.
```

7. Is there a relationship between cost and four-year completion rate? (You don't need to do the stats, just produce a plot). What do you think this means?
```{r}
colleges%>%
  ggplot(aes(costt4_a, c150_4_pooled))+
  geom_point()+
  geom_smooth(method=lm)
# There is some relationship between cost and four-year completion rate, but nothing statistically significant. 
```

8. The column titled `INSTNM` is the institution name. We are only interested in the University of California colleges. Make a new data frame that is restricted to UC institutions. You can remove `Hastings College of Law` and `UC San Francisco` as we are only interested in undergraduate institutions.
```{r}
univ_calif_final <- filter(colleges, instnm=="University of California-Davis" | 
         instnm=="University of California-San Diego" |
         instnm=="University of California-Irvine" |
         instnm=="University of California-Riverside" |
         instnm=="University of California-Los Angeles" |
         instnm=="University of California-Santa Cruz" |
         instnm=="University of California-Berkeley" |
         instnm=="University of California-Santa Barbara")
```

Use `separate()` to separate institution name into two new columns "UNIV" and "CAMPUS".
```{r}
univ_calif_final %>%
  separate(instnm, into = c("univ", "campus"), sep="-")
```

9. The column `ADM_RATE` is the admissions rate by campus. Which UC has the lowest and highest admissions rates? Produce a numerical summary and an appropriate plot.
```{r}
univ_calif_final %>%
  separate(instnm, into = c("univ", "campus"), sep="-")%>%
  summarise(campus, adm_rate)%>%
  arrange(adm_rate)
```
```{r}
univ_calif_final %>%
  separate(instnm, into = c("univ", "campus"), sep="-")%>%
  summarise(campus, adm_rate)%>%
  arrange(adm_rate)%>%
  ggplot(aes(campus, adm_rate))+
  geom_col()
```

10. If you wanted to get a degree in biological or biomedical sciences, which campus confers the majority of these degrees? Produce a numerical summary and an appropriate plot.
```{r}
univ_calif_final%>%
  separate(instnm, into = c("univ", "campus"), sep="-")%>%
  summarise(campus, pcip26)%>%
  arrange()
```

```{r}
univ_calif_final%>%
  separate(instnm, into = c("univ", "campus"), sep="-")%>%
  summarise(campus, pcip26)%>%
  ggplot(aes(campus, pcip26))+
  geom_col()
```

## Knit Your Output and Post to [GitHub](https://github.com/FRS417-DataScienceBiologists)