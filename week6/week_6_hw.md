---
title: "Week 6 HW"
author: "Sofya Lipkind"
date: "5/20/2020"
output: 
  html_document: 
    highlight: pygments
    keep_md: yes
    theme: yeti
---





## Chapter 12 Problems

### 12.2.1

 2. Compute the rate for table2, and table4a + table4b. You will need to perform four operations: 
 
    + Extract the number of TB cases per country per year.  
    + Extract the matching population per country per year.  
    + Divide cases by population, and multiply by 10000.  
    + Store back in the appropriate place.  

```r
#table2
data(table2)
table2_cases<- table2 %>%
  spread(type, count) %>%
  mutate(rate = cases / population * 10000) %>%
  print()
```

```
## # A tibble: 6 x 5
##   country      year  cases population  rate
##   <chr>       <int>  <int>      <int> <dbl>
## 1 Afghanistan  1999    745   19987071 0.373
## 2 Afghanistan  2000   2666   20595360 1.29 
## 3 Brazil       1999  37737  172006362 2.19 
## 4 Brazil       2000  80488  174504898 4.61 
## 5 China        1999 212258 1272915272 1.67 
## 6 China        2000 213766 1280428583 1.67
```

```r
#table4a + 4b = 4c

table4 <- inner_join(table4a, table4b, by = "country") %>%
  gather(year, cases, c(`1999.x`, `2000.x`)) %>%
  gather(year, population, c(`1999.y`, `2000.y`)) %>%
  mutate(rate = cases / population * 10000) %>%
#  gsub(".y","", table4$year) %>%      Why does including this line get rid of all other information?
  print()
```

```
## # A tibble: 12 x 5
##    country      cases year   population  rate
##    <chr>        <int> <chr>       <int> <dbl>
##  1 Afghanistan    745 1999.y   19987071 0.373
##  2 Brazil       37737 1999.y  172006362 2.19 
##  3 China       212258 1999.y 1272915272 1.67 
##  4 Afghanistan   2666 1999.y   19987071 1.33 
##  5 Brazil       80488 1999.y  172006362 4.68 
##  6 China       213766 1999.y 1272915272 1.68 
##  7 Afghanistan    745 2000.y   20595360 0.362
##  8 Brazil       37737 2000.y  174504898 2.16 
##  9 China       212258 2000.y 1280428583 1.66 
## 10 Afghanistan   2666 2000.y   20595360 1.29 
## 11 Brazil       80488 2000.y  174504898 4.61 
## 12 China       213766 2000.y 1280428583 1.67
```

```r
#gsub(".y","", table4$year)
```

Which representation is easiest to work with? Which is hardest? Why?  
*Both of them sucked. How are you supposed to do these without knowing gather() and spread()?*
*I suppose Table 4 was harder, since I had to join them before I could do anything else, and then separate . Then again, if I didn't have spread, I would have hated 2 a lot, as well.*

 3. Recreate the plot showing change in cases over time using table2 instead of table1. What do you need to do first?
 

### 12.3.3

 1. 

 2. 

 3. 

 4. 

### 12.4.3

 1. 

 2. 

 3. 

### 12.6.1

 3. 

 4. 

