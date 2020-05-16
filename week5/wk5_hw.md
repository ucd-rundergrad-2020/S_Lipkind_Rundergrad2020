---
title: "Week 5 HW - Tibbles and Data Importing"
author: "Sofya Lipkind"
date: "5/16/2020"
output: 
  html_document: 
    keep_md: yes
    theme: yeti
---

```
## Warning: package 'tidyverse' was built under R version 3.5.3
```

```
## -- Attaching packages ------------------------------------------------------------------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.2.1     v purrr   0.3.3
## v tibble  2.1.3     v dplyr   0.8.4
## v tidyr   1.0.2     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.4.0
```

```
## Warning: package 'ggplot2' was built under R version 3.5.3
```

```
## Warning: package 'tibble' was built under R version 3.5.3
```

```
## Warning: package 'tidyr' was built under R version 3.5.3
```

```
## Warning: package 'readr' was built under R version 3.5.3
```

```
## Warning: package 'purrr' was built under R version 3.5.3
```

```
## Warning: package 'dplyr' was built under R version 3.5.3
```

```
## Warning: package 'stringr' was built under R version 3.5.3
```

```
## Warning: package 'forcats' was built under R version 3.5.3
```

```
## -- Conflicts ---------------------------------------------------------------------- tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

## Chapter 10 Problems

### 10.5

    #### 10.5.1: How can you tell if an object is a tibble? (Hint: try printing mtcars, which is a regular data frame).  
*Tibbles are distinguished from data frames in that, when printed, they display the first 10 rows, along with all column names and their associated class. They also do not allow partial matching as data frames do.*
    #### 10.5.2: Compare and contrast the following operations on a data.frame and equivalent tibble. What is different? Why might the default data frame behaviours cause you frustration?

```r
df <- data.frame(abc = 1, xyz = "a")
df$x
```

```
## [1] a
## Levels: a
```

```r
df[, "xyz"]
```

```
## [1] a
## Levels: a
```

```r
df[, c("abc", "xyz")]
```

```
##   abc xyz
## 1   1   a
```


    #### 10.5.4  

    #### 10.5.5  

---

## Chapter 11 Problems

### 11.2.2

#### 11.2.2.1  

#### 11.2.2.4  

#### 11.2.2.5  

### **11.3.5**  

#### 11.3.5.1  

#### 11.3.5.2  

#### 11.3.5.3  

#### 11.3.5.7
