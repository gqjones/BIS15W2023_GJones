---
title: "Lab 3 Homework"
author: "Gabriel Jones"
date: "2023-01-19"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the tidyverse

```r
library(tidyverse)
```

## Mammals Sleep
1. For this assignment, we are going to use built-in data on mammal sleep patterns. From which publication are these data taken from? Since the data are built-in you can use the help function in R.

```r
# This data is taken from a 1976 publication by Allison Ciccetti
```

2. Store these data into a new data frame `sleep`.

```r
sleep <- readr::read_csv("C:/Users/gqlos/OneDrive/Documents/GitHub/BIS15W2023_GJones/lab3/data/mammals_sleep_allison_cicchetti_1976.csv")
```

```
## Rows: 62 Columns: 11
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): species
## dbl (10): body weight in kg, brain weight in g, slow wave ("nondreaming") sl...
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

3. What are the dimensions of this data frame (variables and observations)? How do you know? Please show the *code* that you used to determine this below.  

```r
dim(sleep)
```

```
## [1] 62 11
```

```r
# The dimentions are 62x11
```

4. Are there any NAs in the data? How did you determine this? Please show your code.  

```r
is.na(sleep)
```

```
##       species body weight in kg brain weight in g
##  [1,]   FALSE             FALSE             FALSE
##  [2,]   FALSE             FALSE             FALSE
##  [3,]   FALSE             FALSE             FALSE
##  [4,]   FALSE             FALSE             FALSE
##  [5,]   FALSE             FALSE             FALSE
##  [6,]   FALSE             FALSE             FALSE
##  [7,]   FALSE             FALSE             FALSE
##  [8,]   FALSE             FALSE             FALSE
##  [9,]   FALSE             FALSE             FALSE
## [10,]   FALSE             FALSE             FALSE
## [11,]   FALSE             FALSE             FALSE
## [12,]   FALSE             FALSE             FALSE
## [13,]   FALSE             FALSE             FALSE
## [14,]   FALSE             FALSE             FALSE
## [15,]   FALSE             FALSE             FALSE
## [16,]   FALSE             FALSE             FALSE
## [17,]   FALSE             FALSE             FALSE
## [18,]   FALSE             FALSE             FALSE
## [19,]   FALSE             FALSE             FALSE
## [20,]   FALSE             FALSE             FALSE
## [21,]   FALSE             FALSE             FALSE
## [22,]   FALSE             FALSE             FALSE
## [23,]   FALSE             FALSE             FALSE
## [24,]   FALSE             FALSE             FALSE
## [25,]   FALSE             FALSE             FALSE
## [26,]   FALSE             FALSE             FALSE
## [27,]   FALSE             FALSE             FALSE
## [28,]   FALSE             FALSE             FALSE
## [29,]   FALSE             FALSE             FALSE
## [30,]   FALSE             FALSE             FALSE
## [31,]   FALSE             FALSE             FALSE
## [32,]   FALSE             FALSE             FALSE
## [33,]   FALSE             FALSE             FALSE
## [34,]   FALSE             FALSE             FALSE
## [35,]   FALSE             FALSE             FALSE
## [36,]   FALSE             FALSE             FALSE
## [37,]   FALSE             FALSE             FALSE
## [38,]   FALSE             FALSE             FALSE
## [39,]   FALSE             FALSE             FALSE
## [40,]   FALSE             FALSE             FALSE
## [41,]   FALSE             FALSE             FALSE
## [42,]   FALSE             FALSE             FALSE
## [43,]   FALSE             FALSE             FALSE
## [44,]   FALSE             FALSE             FALSE
## [45,]   FALSE             FALSE             FALSE
## [46,]   FALSE             FALSE             FALSE
## [47,]   FALSE             FALSE             FALSE
## [48,]   FALSE             FALSE             FALSE
## [49,]   FALSE             FALSE             FALSE
## [50,]   FALSE             FALSE             FALSE
## [51,]   FALSE             FALSE             FALSE
## [52,]   FALSE             FALSE             FALSE
## [53,]   FALSE             FALSE             FALSE
## [54,]   FALSE             FALSE             FALSE
## [55,]   FALSE             FALSE             FALSE
## [56,]   FALSE             FALSE             FALSE
## [57,]   FALSE             FALSE             FALSE
## [58,]   FALSE             FALSE             FALSE
## [59,]   FALSE             FALSE             FALSE
## [60,]   FALSE             FALSE             FALSE
## [61,]   FALSE             FALSE             FALSE
## [62,]   FALSE             FALSE             FALSE
##       slow wave ("nondreaming") sleep (hrs/day)
##  [1,]                                     FALSE
##  [2,]                                     FALSE
##  [3,]                                     FALSE
##  [4,]                                     FALSE
##  [5,]                                     FALSE
##  [6,]                                     FALSE
##  [7,]                                     FALSE
##  [8,]                                     FALSE
##  [9,]                                     FALSE
## [10,]                                     FALSE
## [11,]                                     FALSE
## [12,]                                     FALSE
## [13,]                                     FALSE
## [14,]                                     FALSE
## [15,]                                     FALSE
## [16,]                                     FALSE
## [17,]                                     FALSE
## [18,]                                     FALSE
## [19,]                                     FALSE
## [20,]                                     FALSE
## [21,]                                     FALSE
## [22,]                                     FALSE
## [23,]                                     FALSE
## [24,]                                     FALSE
## [25,]                                     FALSE
## [26,]                                     FALSE
## [27,]                                     FALSE
## [28,]                                     FALSE
## [29,]                                     FALSE
## [30,]                                     FALSE
## [31,]                                     FALSE
## [32,]                                     FALSE
## [33,]                                     FALSE
## [34,]                                     FALSE
## [35,]                                     FALSE
## [36,]                                     FALSE
## [37,]                                     FALSE
## [38,]                                     FALSE
## [39,]                                     FALSE
## [40,]                                     FALSE
## [41,]                                     FALSE
## [42,]                                     FALSE
## [43,]                                     FALSE
## [44,]                                     FALSE
## [45,]                                     FALSE
## [46,]                                     FALSE
## [47,]                                     FALSE
## [48,]                                     FALSE
## [49,]                                     FALSE
## [50,]                                     FALSE
## [51,]                                     FALSE
## [52,]                                     FALSE
## [53,]                                     FALSE
## [54,]                                     FALSE
## [55,]                                     FALSE
## [56,]                                     FALSE
## [57,]                                     FALSE
## [58,]                                     FALSE
## [59,]                                     FALSE
## [60,]                                     FALSE
## [61,]                                     FALSE
## [62,]                                     FALSE
##       paradoxical ("dreaming") sleep (hrs/day)
##  [1,]                                    FALSE
##  [2,]                                    FALSE
##  [3,]                                    FALSE
##  [4,]                                    FALSE
##  [5,]                                    FALSE
##  [6,]                                    FALSE
##  [7,]                                    FALSE
##  [8,]                                    FALSE
##  [9,]                                    FALSE
## [10,]                                    FALSE
## [11,]                                    FALSE
## [12,]                                    FALSE
## [13,]                                    FALSE
## [14,]                                    FALSE
## [15,]                                    FALSE
## [16,]                                    FALSE
## [17,]                                    FALSE
## [18,]                                    FALSE
## [19,]                                    FALSE
## [20,]                                    FALSE
## [21,]                                    FALSE
## [22,]                                    FALSE
## [23,]                                    FALSE
## [24,]                                    FALSE
## [25,]                                    FALSE
## [26,]                                    FALSE
## [27,]                                    FALSE
## [28,]                                    FALSE
## [29,]                                    FALSE
## [30,]                                    FALSE
## [31,]                                    FALSE
## [32,]                                    FALSE
## [33,]                                    FALSE
## [34,]                                    FALSE
## [35,]                                    FALSE
## [36,]                                    FALSE
## [37,]                                    FALSE
## [38,]                                    FALSE
## [39,]                                    FALSE
## [40,]                                    FALSE
## [41,]                                    FALSE
## [42,]                                    FALSE
## [43,]                                    FALSE
## [44,]                                    FALSE
## [45,]                                    FALSE
## [46,]                                    FALSE
## [47,]                                    FALSE
## [48,]                                    FALSE
## [49,]                                    FALSE
## [50,]                                    FALSE
## [51,]                                    FALSE
## [52,]                                    FALSE
## [53,]                                    FALSE
## [54,]                                    FALSE
## [55,]                                    FALSE
## [56,]                                    FALSE
## [57,]                                    FALSE
## [58,]                                    FALSE
## [59,]                                    FALSE
## [60,]                                    FALSE
## [61,]                                    FALSE
## [62,]                                    FALSE
##       total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)
##  [1,]                                                           FALSE
##  [2,]                                                           FALSE
##  [3,]                                                           FALSE
##  [4,]                                                           FALSE
##  [5,]                                                           FALSE
##  [6,]                                                           FALSE
##  [7,]                                                           FALSE
##  [8,]                                                           FALSE
##  [9,]                                                           FALSE
## [10,]                                                           FALSE
## [11,]                                                           FALSE
## [12,]                                                           FALSE
## [13,]                                                           FALSE
## [14,]                                                           FALSE
## [15,]                                                           FALSE
## [16,]                                                           FALSE
## [17,]                                                           FALSE
## [18,]                                                           FALSE
## [19,]                                                           FALSE
## [20,]                                                           FALSE
## [21,]                                                           FALSE
## [22,]                                                           FALSE
## [23,]                                                           FALSE
## [24,]                                                           FALSE
## [25,]                                                           FALSE
## [26,]                                                           FALSE
## [27,]                                                           FALSE
## [28,]                                                           FALSE
## [29,]                                                           FALSE
## [30,]                                                           FALSE
## [31,]                                                           FALSE
## [32,]                                                           FALSE
## [33,]                                                           FALSE
## [34,]                                                           FALSE
## [35,]                                                           FALSE
## [36,]                                                           FALSE
## [37,]                                                           FALSE
## [38,]                                                           FALSE
## [39,]                                                           FALSE
## [40,]                                                           FALSE
## [41,]                                                           FALSE
## [42,]                                                           FALSE
## [43,]                                                           FALSE
## [44,]                                                           FALSE
## [45,]                                                           FALSE
## [46,]                                                           FALSE
## [47,]                                                           FALSE
## [48,]                                                           FALSE
## [49,]                                                           FALSE
## [50,]                                                           FALSE
## [51,]                                                           FALSE
## [52,]                                                           FALSE
## [53,]                                                           FALSE
## [54,]                                                           FALSE
## [55,]                                                           FALSE
## [56,]                                                           FALSE
## [57,]                                                           FALSE
## [58,]                                                           FALSE
## [59,]                                                           FALSE
## [60,]                                                           FALSE
## [61,]                                                           FALSE
## [62,]                                                           FALSE
##       maximum life span (years) gestation time (days) predation index (1-5)
##  [1,]                     FALSE                 FALSE                 FALSE
##  [2,]                     FALSE                 FALSE                 FALSE
##  [3,]                     FALSE                 FALSE                 FALSE
##  [4,]                     FALSE                 FALSE                 FALSE
##  [5,]                     FALSE                 FALSE                 FALSE
##  [6,]                     FALSE                 FALSE                 FALSE
##  [7,]                     FALSE                 FALSE                 FALSE
##  [8,]                     FALSE                 FALSE                 FALSE
##  [9,]                     FALSE                 FALSE                 FALSE
## [10,]                     FALSE                 FALSE                 FALSE
## [11,]                     FALSE                 FALSE                 FALSE
## [12,]                     FALSE                 FALSE                 FALSE
## [13,]                     FALSE                 FALSE                 FALSE
## [14,]                     FALSE                 FALSE                 FALSE
## [15,]                     FALSE                 FALSE                 FALSE
## [16,]                     FALSE                 FALSE                 FALSE
## [17,]                     FALSE                 FALSE                 FALSE
## [18,]                     FALSE                 FALSE                 FALSE
## [19,]                     FALSE                 FALSE                 FALSE
## [20,]                     FALSE                 FALSE                 FALSE
## [21,]                     FALSE                 FALSE                 FALSE
## [22,]                     FALSE                 FALSE                 FALSE
## [23,]                     FALSE                 FALSE                 FALSE
## [24,]                     FALSE                 FALSE                 FALSE
## [25,]                     FALSE                 FALSE                 FALSE
## [26,]                     FALSE                 FALSE                 FALSE
## [27,]                     FALSE                 FALSE                 FALSE
## [28,]                     FALSE                 FALSE                 FALSE
## [29,]                     FALSE                 FALSE                 FALSE
## [30,]                     FALSE                 FALSE                 FALSE
## [31,]                     FALSE                 FALSE                 FALSE
## [32,]                     FALSE                 FALSE                 FALSE
## [33,]                     FALSE                 FALSE                 FALSE
## [34,]                     FALSE                 FALSE                 FALSE
## [35,]                     FALSE                 FALSE                 FALSE
## [36,]                     FALSE                 FALSE                 FALSE
## [37,]                     FALSE                 FALSE                 FALSE
## [38,]                     FALSE                 FALSE                 FALSE
## [39,]                     FALSE                 FALSE                 FALSE
## [40,]                     FALSE                 FALSE                 FALSE
## [41,]                     FALSE                 FALSE                 FALSE
## [42,]                     FALSE                 FALSE                 FALSE
## [43,]                     FALSE                 FALSE                 FALSE
## [44,]                     FALSE                 FALSE                 FALSE
## [45,]                     FALSE                 FALSE                 FALSE
## [46,]                     FALSE                 FALSE                 FALSE
## [47,]                     FALSE                 FALSE                 FALSE
## [48,]                     FALSE                 FALSE                 FALSE
## [49,]                     FALSE                 FALSE                 FALSE
## [50,]                     FALSE                 FALSE                 FALSE
## [51,]                     FALSE                 FALSE                 FALSE
## [52,]                     FALSE                 FALSE                 FALSE
## [53,]                     FALSE                 FALSE                 FALSE
## [54,]                     FALSE                 FALSE                 FALSE
## [55,]                     FALSE                 FALSE                 FALSE
## [56,]                     FALSE                 FALSE                 FALSE
## [57,]                     FALSE                 FALSE                 FALSE
## [58,]                     FALSE                 FALSE                 FALSE
## [59,]                     FALSE                 FALSE                 FALSE
## [60,]                     FALSE                 FALSE                 FALSE
## [61,]                     FALSE                 FALSE                 FALSE
## [62,]                     FALSE                 FALSE                 FALSE
##       sleep exposure index (1-5) overall danger index (1-5)
##  [1,]                      FALSE                      FALSE
##  [2,]                      FALSE                      FALSE
##  [3,]                      FALSE                      FALSE
##  [4,]                      FALSE                      FALSE
##  [5,]                      FALSE                      FALSE
##  [6,]                      FALSE                      FALSE
##  [7,]                      FALSE                      FALSE
##  [8,]                      FALSE                      FALSE
##  [9,]                      FALSE                      FALSE
## [10,]                      FALSE                      FALSE
## [11,]                      FALSE                      FALSE
## [12,]                      FALSE                      FALSE
## [13,]                      FALSE                      FALSE
## [14,]                      FALSE                      FALSE
## [15,]                      FALSE                      FALSE
## [16,]                      FALSE                      FALSE
## [17,]                      FALSE                      FALSE
## [18,]                      FALSE                      FALSE
## [19,]                      FALSE                      FALSE
## [20,]                      FALSE                      FALSE
## [21,]                      FALSE                      FALSE
## [22,]                      FALSE                      FALSE
## [23,]                      FALSE                      FALSE
## [24,]                      FALSE                      FALSE
## [25,]                      FALSE                      FALSE
## [26,]                      FALSE                      FALSE
## [27,]                      FALSE                      FALSE
## [28,]                      FALSE                      FALSE
## [29,]                      FALSE                      FALSE
## [30,]                      FALSE                      FALSE
## [31,]                      FALSE                      FALSE
## [32,]                      FALSE                      FALSE
## [33,]                      FALSE                      FALSE
## [34,]                      FALSE                      FALSE
## [35,]                      FALSE                      FALSE
## [36,]                      FALSE                      FALSE
## [37,]                      FALSE                      FALSE
## [38,]                      FALSE                      FALSE
## [39,]                      FALSE                      FALSE
## [40,]                      FALSE                      FALSE
## [41,]                      FALSE                      FALSE
## [42,]                      FALSE                      FALSE
## [43,]                      FALSE                      FALSE
## [44,]                      FALSE                      FALSE
## [45,]                      FALSE                      FALSE
## [46,]                      FALSE                      FALSE
## [47,]                      FALSE                      FALSE
## [48,]                      FALSE                      FALSE
## [49,]                      FALSE                      FALSE
## [50,]                      FALSE                      FALSE
## [51,]                      FALSE                      FALSE
## [52,]                      FALSE                      FALSE
## [53,]                      FALSE                      FALSE
## [54,]                      FALSE                      FALSE
## [55,]                      FALSE                      FALSE
## [56,]                      FALSE                      FALSE
## [57,]                      FALSE                      FALSE
## [58,]                      FALSE                      FALSE
## [59,]                      FALSE                      FALSE
## [60,]                      FALSE                      FALSE
## [61,]                      FALSE                      FALSE
## [62,]                      FALSE                      FALSE
```

```r
# There are no NAs in the data. However, there are values of -999 which may be substituted for NA and would have to be taken into account during calculations
```

5. Show a list of the column names is this data frame.

```r
colnames(sleep)
```

```
##  [1] "species"                                                        
##  [2] "body weight in kg"                                              
##  [3] "brain weight in g"                                              
##  [4] "slow wave (\"nondreaming\") sleep (hrs/day)"                    
##  [5] "paradoxical (\"dreaming\") sleep (hrs/day)"                     
##  [6] "total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)"
##  [7] "maximum life span (years)"                                      
##  [8] "gestation time (days)"                                          
##  [9] "predation index (1-5)"                                          
## [10] "sleep exposure index (1-5)"                                     
## [11] "overall danger index (1-5)"
```

6. How many herbivores are represented in the data?  

```r
length(c(sleep$species[sleep$`predation index (1-5)` == 1]))
```

```
## [1] 14
```

7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 1kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.

```r
small <- 1
large <- 200
small.mammals <- data.frame(c(sleep$species[sleep$`body weight in kg` <= small]),
                            c(sleep$`body weight in kg`[sleep$`body weight in kg` <= small]),
                            c(sleep$`brain weight in g`[sleep$`body weight in kg` <= small]),
                            c(sleep$`slow wave ("nondreaming") sleep (hrs/day)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`paradoxical ("dreaming") sleep (hrs/day)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`maximum life span (years)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`gestation time (days)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`predation index (1-5)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`sleep exposure index (1-5)`[sleep$`body weight in kg` <= small]),
                            c(sleep$`overall danger index (1-5)`[sleep$`body weight in kg` <= small]))

large.mammals <- data.frame(c(sleep$species[sleep$`body weight in kg` >= large]),
                            c(sleep$`body weight in kg`[sleep$`body weight in kg` >= large]),
                            c(sleep$`brain weight in g`[sleep$`body weight in kg` >= large]),
                            c(sleep$`slow wave ("nondreaming") sleep (hrs/day)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`paradoxical ("dreaming") sleep (hrs/day)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`maximum life span (years)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`gestation time (days)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`predation index (1-5)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`sleep exposure index (1-5)`[sleep$`body weight in kg` >= large]),
                            c(sleep$`overall danger index (1-5)`[sleep$`body weight in kg` >= large]))
```

8. What is the mean weight for both the small and large mammals?

```r
mean(small.mammals$c.sleep..body.weight.in.kg..sleep..body.weight.in.kg.....small..)
```

```
## [1] 0.3324286
```


```r
mean(large.mammals$c.sleep..body.weight.in.kg..sleep..body.weight.in.kg.....large..)
```

```
## [1] 1596.143
```

9. Using a similar approach as above, do large or small animals sleep longer on average?  

```r
mean(small.mammals$c.sleep..total.sleep..hrs.day....sum.of.slow.wave.and.paradoxical.sleep...sleep..body.weight.in.kg.....)
```

```
## [1] 12.71905
```


```r
mean(c(large.mammals$c.sleep..total.sleep..hrs.day....sum.of.slow.wave.and.paradoxical.sleep...sleep..body.weight.in.kg.....[
  large.mammals$c.sleep..total.sleep..hrs.day....sum.of.slow.wave.and.paradoxical.sleep...sleep..body.weight.in.kg..... > 0
]))
```

```
## [1] 5.2
```

```r
# Small mammals sleep longer on average
```
10. Which animal is the sleepiest among the entire dataframe?

```r
sleep$species[which(sleep$`total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)` == max(sleep$`total sleep (hrs/day)  (sum of slow wave and paradoxical sleep)`))]
```

```
## [1] "Little brown bat"
```

``
## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
