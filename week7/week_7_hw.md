---
title: "week_7_hw"
author: "Sofya Lipkind"
date: "6/2/2020"
output: 
  html_document: 
    highlight: pygments
    keep_md: yes
    theme: yeti
---



## Chapter 13 Problems  

### 13.2.1

#### 1. Imagine you wanted to draw (approximately) the route each plane flies from its origin to its destination. What variables would you need? What tables would you need to combine?

*airport contains the variables Lat and Lon, which describe the location of each airport.Using Lat an Lon in conjunction with origin and dest (from flight) should give us a vague idea of the path between the origin and the destination.*

#### 2. I forgot to draw the relationship between weather and airports. What is the relationship and how should it appear in the diagram?

*weather(origin) -> airports(faa) -> airports(names)*

#### 3. weather only contains information for the origin (NYC) airports. If it contained weather records for all airports in the USA, what additional relation would it define with flights?

*dest, correct?*

#### 4. We know that some days of the year are “special”, and fewer people than usual fly on them. How might you represent that data as a data frame? What would be the primary keys of that table? How would it connect to the existing tables?


```r
flights %>%
  group_by(year) %>%
  count(month, day) %>%
  arrange(n)
```

```
## # A tibble: 365 x 4
## # Groups:   year [1]
##     year month   day     n
##    <int> <int> <int> <int>
##  1  2013    11    28   634
##  2  2013    11    29   661
##  3  2013     1    19   674
##  4  2013    10    12   676
##  5  2013     1    26   680
##  6  2013     8    31   680
##  7  2013     2     2   682
##  8  2013     9    28   682
##  9  2013     2     9   684
## 10  2013    10    19   684
## # ... with 355 more rows
```

```r
#connect via year/month/day to flights, whereby it could connect to other tables
```

### 13.3.1

#### 1. Add a surrogate key to flights.

```r
flights %>%
  mutate(id=row_number())
```

```
## # A tibble: 336,776 x 20
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1      517            515         2      830            819
##  2  2013     1     1      533            529         4      850            830
##  3  2013     1     1      542            540         2      923            850
##  4  2013     1     1      544            545        -1     1004           1022
##  5  2013     1     1      554            600        -6      812            837
##  6  2013     1     1      554            558        -4      740            728
##  7  2013     1     1      555            600        -5      913            854
##  8  2013     1     1      557            600        -3      709            723
##  9  2013     1     1      557            600        -3      838            846
## 10  2013     1     1      558            600        -2      753            745
## # ... with 336,766 more rows, and 12 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>,
## #   id <int>
```
#### 2. Identify the keys in the following datasets
  1. Lahman::Batting  

```r
head(Lahman::Batting)
```

```
##    playerID yearID stint teamID lgID  G  AB  R  H X2B X3B HR RBI SB CS BB SO
## 1 abercda01   1871     1    TRO   NA  1   4  0  0   0   0  0   0  0  0  0  0
## 2  addybo01   1871     1    RC1   NA 25 118 30 32   6   0  0  13  8  1  4  0
## 3 allisar01   1871     1    CL1   NA 29 137 28 40   4   5  0  19  3  1  2  5
## 4 allisdo01   1871     1    WS3   NA 27 133 28 44  10   2  2  27  1  1  0  2
## 5 ansonca01   1871     1    RC1   NA 25 120 29 39  11   3  0  16  6  2  2  1
## 6 armstbo01   1871     1    FW1   NA 12  49  9 11   2   1  0   5  0  1  0  1
##   IBB HBP SH SF GIDP
## 1  NA  NA NA NA    0
## 2  NA  NA NA NA    0
## 3  NA  NA NA NA    1
## 4  NA  NA NA NA    0
## 5  NA  NA NA NA    0
## 6  NA  NA NA NA    0
```

```r
#primary: playerID
```

  2. babynames::babynames  

```r
glimpse(babynames::babynames)
```

```
## Observations: 1,924,665
## Variables: 5
## $ year <dbl> 1880, 1880, 1880, 1880, 1880, 1880, 1880, 1880, 1880, 1880, 18...
## $ sex  <chr> "F", "F", "F", "F", "F", "F", "F", "F", "F", "F", "F", "F", "F...
## $ name <chr> "Mary", "Anna", "Emma", "Elizabeth", "Minnie", "Margaret", "Id...
## $ n    <int> 7065, 2604, 2003, 1939, 1746, 1578, 1472, 1414, 1320, 1288, 12...
## $ prop <dbl> 0.07238359, 0.02667896, 0.02052149, 0.01986579, 0.01788843, 0....
```

```r
unique(babynames::babynames$year)
```

```
##   [1] 1880 1881 1882 1883 1884 1885 1886 1887 1888 1889 1890 1891 1892 1893 1894
##  [16] 1895 1896 1897 1898 1899 1900 1901 1902 1903 1904 1905 1906 1907 1908 1909
##  [31] 1910 1911 1912 1913 1914 1915 1916 1917 1918 1919 1920 1921 1922 1923 1924
##  [46] 1925 1926 1927 1928 1929 1930 1931 1932 1933 1934 1935 1936 1937 1938 1939
##  [61] 1940 1941 1942 1943 1944 1945 1946 1947 1948 1949 1950 1951 1952 1953 1954
##  [76] 1955 1956 1957 1958 1959 1960 1961 1962 1963 1964 1965 1966 1967 1968 1969
##  [91] 1970 1971 1972 1973 1974 1975 1976 1977 1978 1979 1980 1981 1982 1983 1984
## [106] 1985 1986 1987 1988 1989 1990 1991 1992 1993 1994 1995 1996 1997 1998 1999
## [121] 2000 2001 2002 2003 2004 2005 2006 2007 2008 2009 2010 2011 2012 2013 2014
## [136] 2015 2016 2017
```

```r
#primary: name + year
```

### 13.4.6

#### 1. Compute the average delay by destination, then join on the airports data frame so you can show the spatial distribution of delays. Here’s an easy way to draw a map of the United States:

```r
#could not install maps
#install.packages("maps")
#airports %>%
#  semi_join(flights, c("faa" = "dest")) %>%
#  ggplot(aes(lon, lat)) +
#    borders("state") +
#    geom_point() +
#    coord_quickmap()
```

#### 2. Add the location of the origin and destination (i.e. the lat and lon) to flights.



## Chapter 18 Problems

