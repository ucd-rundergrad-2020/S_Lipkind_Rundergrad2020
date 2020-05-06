---
title: "Week 3 HW and Notes"
output:
  html_document: 
    keep_md: yes
editor_options:
  chunk_output_type: console
---
# SETUP


FXN: Save graphical outputs

```r
picsave <- function(graph, name) {
  ggsave(plot = graph, filename= name, device = "pdf", width = 12, height = 8, path = "~/GitHub/S_Lipkind_Rundergrad2020/week3/pics/")
}
```
---
# PROBLEMS

## CHAPTER 4 PROBLEMS

### 4.4

1. Why does this code not work?


```r
my_variable <- 10
my_varıable
```

```
## [1] 10
```

```r
#> Error in eval(expr, envir, enclos): object 'my_varıable' not found
```

*Was this written by someone who speaks Turkish or something? Not sure how else someone could use _ı_ instead of _i_.*

2. Tweak each of the following R commands so that they run correctly:


```r
a <- ggplot(data = mpg) + #dota -> data
  geom_point(mapping = aes(x = displ, y = hwy))
#picsave(a, "4.4.2 graph.pdf")

filter(mpg, cyl == 8) #= -> ==
```

```
## # A tibble: 70 x 11
##    manufacturer model     displ  year   cyl trans  drv     cty   hwy fl    class
##    <chr>        <chr>     <dbl> <int> <int> <chr>  <chr> <int> <int> <chr> <chr>
##  1 audi         a6 quatt~   4.2  2008     8 auto(~ 4        16    23 p     mids~
##  2 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        14    20 r     suv  
##  3 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        11    15 e     suv  
##  4 chevrolet    c1500 su~   5.3  2008     8 auto(~ r        14    20 r     suv  
##  5 chevrolet    c1500 su~   5.7  1999     8 auto(~ r        13    17 r     suv  
##  6 chevrolet    c1500 su~   6    2008     8 auto(~ r        12    17 r     suv  
##  7 chevrolet    corvette    5.7  1999     8 manua~ r        16    26 p     2sea~
##  8 chevrolet    corvette    5.7  1999     8 auto(~ r        15    23 p     2sea~
##  9 chevrolet    corvette    6.2  2008     8 manua~ r        16    26 p     2sea~
## 10 chevrolet    corvette    6.2  2008     8 auto(~ r        15    25 p     2sea~
## # ... with 60 more rows
```

```r
filter(diamonds, carat > 3) # diamond -> diamonds
```

```
## # A tibble: 32 x 10
##    carat cut     color clarity depth table price     x     y     z
##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
## # ... with 22 more rows
```

3. Press Alt + Shift + K. What happens? How can you get to the same place using the menus?

*Oh my goodness, that is amazing. An entire list of keyboard shortcuts. You could also reach that page by going to Help > Keyboard Shortcuts Help.*

## CHAPTER 5 PROBLEMS

### 5.2.4

Find all flights that...

  #### 1.1: had an arrival delay of two or more hours
  

```r
head(flights)
```

```
## # A tibble: 6 x 19
##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
## 1  2013     1     1      517            515         2      830            819
## 2  2013     1     1      533            529         4      850            830
## 3  2013     1     1      542            540         2      923            850
## 4  2013     1     1      544            545        -1     1004           1022
## 5  2013     1     1      554            600        -6      812            837
## 6  2013     1     1      554            558        -4      740            728
## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
## #   hour <dbl>, minute <dbl>, time_hour <dttm>
```

```r
filter(flights, arr_delay >= 2)
```

```
## # A tibble: 127,929 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1      517            515         2      830            819
##  2  2013     1     1      533            529         4      850            830
##  3  2013     1     1      542            540         2      923            850
##  4  2013     1     1      554            558        -4      740            728
##  5  2013     1     1      555            600        -5      913            854
##  6  2013     1     1      558            600        -2      753            745
##  7  2013     1     1      558            600        -2      924            917
##  8  2013     1     1      559            600        -1      941            910
##  9  2013     1     1      600            600         0      837            825
## 10  2013     1     1      602            605        -3      821            805
## # ... with 127,919 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```
  
  #### 1.4: Departed in summer (July, August, and September)
  

```r
filter(flights, month %in% c(7,8,9))
```

```
## # A tibble: 86,326 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     7     1        1           2029       212      236           2359
##  2  2013     7     1        2           2359         3      344            344
##  3  2013     7     1       29           2245       104      151              1
##  4  2013     7     1       43           2130       193      322             14
##  5  2013     7     1       44           2150       174      300            100
##  6  2013     7     1       46           2051       235      304           2358
##  7  2013     7     1       48           2001       287      308           2305
##  8  2013     7     1       58           2155       183      335             43
##  9  2013     7     1      100           2146       194      327             30
## 10  2013     7     1      100           2245       135      337            135
## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

  #### 1.5: Arrived more than two hours late, but didn’t leave late


```r
filter(flights, arr_delay > 2 & dep_delay == 0)
```

```
## # A tibble: 4,368 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1      600            600         0      837            825
##  2  2013     1     1      635            635         0     1028            940
##  3  2013     1     1      739            739         0     1104           1038
##  4  2013     1     1      745            745         0     1135           1125
##  5  2013     1     1      800            800         0     1022           1014
##  6  2013     1     1      805            805         0     1015           1005
##  7  2013     1     1      810            810         0     1048           1037
##  8  2013     1     1      823            823         0     1151           1135
##  9  2013     1     1      830            830         0     1018           1015
## 10  2013     1     1      835            835         0     1210           1150
## # ... with 4,358 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

  #### 1.7: Departed between midnight and 6am (inclusive)
  

```r
(d <- filter(flights, dep_time >= 0, dep_time <= 600))
```

```
## # A tibble: 9,344 x 19
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
## # ... with 9,334 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```
  
  #### 2: Another useful dplyr filtering helper is between(). What does it do? Can you use it to simplify the code needed to answer the previous challenges?

?between
*It's an inclusive shortcut to find values within a certain range.*

```r
e <- filter(flights, dep_time %in% between(dep_time,0, 600))
# d == e
```

  #### 3: How many flights have a missing dep_time? What other variables are missing? What might these rows represent?


```r
filter(flights, dep_time %in% NA) # 8255 rows/flights
```

```
## # A tibble: 8,255 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1       NA           1630        NA       NA           1815
##  2  2013     1     1       NA           1935        NA       NA           2240
##  3  2013     1     1       NA           1500        NA       NA           1825
##  4  2013     1     1       NA            600        NA       NA            901
##  5  2013     1     2       NA           1540        NA       NA           1747
##  6  2013     1     2       NA           1620        NA       NA           1746
##  7  2013     1     2       NA           1355        NA       NA           1459
##  8  2013     1     2       NA           1420        NA       NA           1644
##  9  2013     1     2       NA           1321        NA       NA           1536
## 10  2013     1     2       NA           1545        NA       NA           1910
## # ... with 8,245 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

```r
#these observations also all have NA dep_delay, arr_time, arr_delay.
#Hypothesis: cancelled flights
```

  
### 5.3.1

#### How could you use arrange() to sort all missing values to the start? (Hint: use is.na()).

```r
arrange(flights, desc(is.na(dep_delay))) #this works, but is it the intended solution?
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1       NA           1630        NA       NA           1815
##  2  2013     1     1       NA           1935        NA       NA           2240
##  3  2013     1     1       NA           1500        NA       NA           1825
##  4  2013     1     1       NA            600        NA       NA            901
##  5  2013     1     2       NA           1540        NA       NA           1747
##  6  2013     1     2       NA           1620        NA       NA           1746
##  7  2013     1     2       NA           1355        NA       NA           1459
##  8  2013     1     2       NA           1420        NA       NA           1644
##  9  2013     1     2       NA           1321        NA       NA           1536
## 10  2013     1     2       NA           1545        NA       NA           1910
## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

#### Sort flights to find the most delayed flights. Find the flights that left earliest.

```r
arrange(flights, dep_time, desc(dep_delay))
```

```
## # A tibble: 336,776 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     4    10        1           1930       271      106           2101
##  2  2013     5    22        1           1935       266      154           2140
##  3  2013     6    24        1           1950       251      105           2130
##  4  2013     7     1        1           2029       212      236           2359
##  5  2013     1    31        1           2100       181      124           2225
##  6  2013     2    11        1           2100       181      111           2225
##  7  2013     3    18        1           2128       153      247           2355
##  8  2013     6    25        1           2130       151      249             14
##  9  2013     2    24        1           2245        76      121           2354
## 10  2013     1    13        1           2249        72      108           2357
## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

#### Sort flights to find the fastest (highest speed) flights.

```r
y <- arrange(flights, desc(distance), air_time)
#(select(y, distance, air_time)) -> double-checking
```

#### Which flights travelled the farthest? Which travelled the shortest?

```r
(longest_distance <- top_n(flights, 10, distance))
```

```
## # A tibble: 342 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     1      857            900        -3     1516           1530
##  2  2013     1     2      909            900         9     1525           1530
##  3  2013     1     3      914            900        14     1504           1530
##  4  2013     1     4      900            900         0     1516           1530
##  5  2013     1     5      858            900        -2     1519           1530
##  6  2013     1     6     1019            900        79     1558           1530
##  7  2013     1     7     1042            900       102     1620           1530
##  8  2013     1     8      901            900         1     1504           1530
##  9  2013     1     9      641            900      1301     1242           1530
## 10  2013     1    10      859            900        -1     1449           1530
## # ... with 332 more rows, and 11 more variables: arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```

```r
(shortest_distance <- top_n(flights, -10, distance))
```

```
## # A tibble: 50 x 19
##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
##  1  2013     1     3     2127           2129        -2     2222           2224
##  2  2013     1     4     1240           1200        40     1333           1306
##  3  2013     1     4     1829           1615       134     1937           1721
##  4  2013     1     4     2128           2129        -1     2218           2224
##  5  2013     1     5     1155           1200        -5     1241           1306
##  6  2013     1     6     2125           2129        -4     2224           2224
##  7  2013     1     7     2124           2129        -5     2212           2224
##  8  2013     1     8     2127           2130        -3     2304           2225
##  9  2013     1     9     2126           2129        -3     2217           2224
## 10  2013     1    10     2133           2129         4     2223           2224
## # ... with 40 more rows, and 11 more variables: arr_delay <dbl>, carrier <chr>,
## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>
```
 
 
### 5.4.1

#### Brainstorm as many ways as possible to select dep_time, dep_delay, arr_time, and arr_delay from flights.

```r
#one option: select()
```

#### What happens if you include the name of a variable multiple times in a select() call?

```r
select(flights, day, month, day, month, dep_delay, dep_delay)
```

```
## # A tibble: 336,776 x 3
##      day month dep_delay
##    <int> <int>     <dbl>
##  1     1     1         2
##  2     1     1         4
##  3     1     1         2
##  4     1     1        -1
##  5     1     1        -6
##  6     1     1        -4
##  7     1     1        -5
##  8     1     1        -3
##  9     1     1        -3
## 10     1     1        -2
## # ... with 336,766 more rows
```
*Repeating variable names does not appear to make a difference. Only the sorting of the initial appearance of each name within the list matters.*

#### What does the one_of() function do? Why might it be helpful in conjunction with this vector?

```r
vars <- c("year", "month", "day", "dep_delay", "arr_delay") 
select(flights, one_of(vars))
```

```
## # A tibble: 336,776 x 5
##     year month   day dep_delay arr_delay
##    <int> <int> <int>     <dbl>     <dbl>
##  1  2013     1     1         2        11
##  2  2013     1     1         4        20
##  3  2013     1     1         2        33
##  4  2013     1     1        -1       -18
##  5  2013     1     1        -6       -25
##  6  2013     1     1        -4        12
##  7  2013     1     1        -5        19
##  8  2013     1     1        -3       -14
##  9  2013     1     1        -3        -8
## 10  2013     1     1        -2         8
## # ... with 336,766 more rows
```

*one_of() allows one to make a character vector with specific column names that you can then select for.*

#### Does the result of running the following code surprise you? How do the select helpers deal with case by default? How can you change that default?

```r
select(flights, contains("TIME"))
```

```
## # A tibble: 336,776 x 6
##    dep_time sched_dep_time arr_time sched_arr_time air_time time_hour          
##       <int>          <int>    <int>          <int>    <dbl> <dttm>             
##  1      517            515      830            819      227 2013-01-01 05:00:00
##  2      533            529      850            830      227 2013-01-01 05:00:00
##  3      542            540      923            850      160 2013-01-01 05:00:00
##  4      544            545     1004           1022      183 2013-01-01 05:00:00
##  5      554            600      812            837      116 2013-01-01 06:00:00
##  6      554            558      740            728      150 2013-01-01 05:00:00
##  7      555            600      913            854      158 2013-01-01 06:00:00
##  8      557            600      709            723       53 2013-01-01 06:00:00
##  9      557            600      838            846      140 2013-01-01 06:00:00
## 10      558            600      753            745      138 2013-01-01 06:00:00
## # ... with 336,766 more rows
```

*The results aren't too surprising, though I didn't realize select was not case-sensitive.*
*If I wanted to specify case, I could add the specifier below:*

```r
select(flights, contains("time", ignore.case = FALSE))
```

```
## # A tibble: 336,776 x 6
##    dep_time sched_dep_time arr_time sched_arr_time air_time time_hour          
##       <int>          <int>    <int>          <int>    <dbl> <dttm>             
##  1      517            515      830            819      227 2013-01-01 05:00:00
##  2      533            529      850            830      227 2013-01-01 05:00:00
##  3      542            540      923            850      160 2013-01-01 05:00:00
##  4      544            545     1004           1022      183 2013-01-01 05:00:00
##  5      554            600      812            837      116 2013-01-01 06:00:00
##  6      554            558      740            728      150 2013-01-01 05:00:00
##  7      555            600      913            854      158 2013-01-01 06:00:00
##  8      557            600      709            723       53 2013-01-01 06:00:00
##  9      557            600      838            846      140 2013-01-01 06:00:00
## 10      558            600      753            745      138 2013-01-01 06:00:00
## # ... with 336,766 more rows
```


### 5.5.2

#### 1.Currently dep_time and sched_dep_time are convenient to look at, but hard to compute with because they’re not really continuous numbers. Convert them to a more convenient representation of number of minutes since midnight.

```r
head(flights)
```

```
## # A tibble: 6 x 19
##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
## 1  2013     1     1      517            515         2      830            819
## 2  2013     1     1      533            529         4      850            830
## 3  2013     1     1      542            540         2      923            850
## 4  2013     1     1      544            545        -1     1004           1022
## 5  2013     1     1      554            600        -6      812            837
## 6  2013     1     1      554            558        -4      740            728
## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
## #   hour <dbl>, minute <dbl>, time_hour <dttm>
```

```r
minutes <- function(miltime) {
  miltime %/% 100 * 60 + miltime %% 100
}

mod <- flights %>%
  select(dep_time,sched_dep_time) %>%
  lapply(.,minutes) %>%
  as_tibble() %>%
  rename(
    mod_dep_time = dep_time,
    mod_sched_dep_time = sched_dep_time)

modflights <- flights %>% #I initially tried to join flights and mod together, but I couldn't figure out the 'by' part.
  mutate(
    mod_dep_time = mod$mod_dep_time,
    mod_sched_dep_time = mod$mod_sched_dep_time)
```

#### 2.Compare air_time with arr_time - dep_time. What do you expect to see? What do you see? What do you need to do to fix it?

```r
discrepancy <- flights %>%
  mutate(
    arr_dep = arr_time - dep_time) %>%
  select(arr_dep, air_time) %>%
  lapply(.,minutes) %>%
  glimpse(.)
```

```
## List of 2
##  $ arr_dep : num [1:336776] 193 197 261 300 178 146 238 112 201 155 ...
##  $ air_time: num [1:336776] 147 147 120 143 76 110 118 53 100 98 ...
```

```r
#Theoretically, you would expect the values to be the same, but they are not.
#Perhaps there's an issue as a result of military time? When I converted to minutes, though, the difference remained. Air time is shorter than arr_dep.
#Hypothesis: The difference in time is explained by the time the planes take to embark and disembark.
#How to test: add dep_delay and arr_delay to ait_time, see if air_time == arr_dep.

head(flights)
```

```
## # A tibble: 6 x 19
##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
## 1  2013     1     1      517            515         2      830            819
## 2  2013     1     1      533            529         4      850            830
## 3  2013     1     1      542            540         2      923            850
## 4  2013     1     1      544            545        -1     1004           1022
## 5  2013     1     1      554            600        -6      812            837
## 6  2013     1     1      554            558        -4      740            728
## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
## #   hour <dbl>, minute <dbl>, time_hour <dttm>
```

```r
flights %>% 
    mutate(
      air_time_delay = air_time + arr_delay + dep_delay,
      arr_dep = discrepancy$arr_dep) %>%
    select(air_time,air_time_delay,arr_dep, dep_delay, arr_delay) %>%
    lapply(., minutes) %>%
    glimpse(.)
```

```
## List of 5
##  $ air_time      : num [1:336776] 147 147 120 143 76 110 118 53 100 98 ...
##  $ air_time_delay: num [1:336776] 160 171 155 124 85 118 132 36 89 104 ...
##  $ arr_dep       : num [1:336776] 153 157 181 180 138 106 158 72 121 115 ...
##  $ dep_delay     : num [1:336776] 2 4 2 39 34 36 35 37 37 38 ...
##  $ arr_delay     : num [1:336776] 11 20 33 22 15 12 19 26 32 8 ...
```

```r
#However, that doesn't seem to work, either, and the difference between arr_dep and air_time is not explained neatly by either dep_delay or arr_delay.
```

#### 3.Compare dep_time, sched_dep_time, and dep_delay. How would you expect those three numbers to be related?

```r
#Expected: dep_time == sched_dep_time + dep_delay
#
flights %>%
  select(dep_time, sched_dep_time, dep_delay) %>%
  mutate(hypothesis = sched_dep_time + dep_delay) %>%
  lapply(., minutes) %>%
  glimpse(.)
```

```
## List of 4
##  $ dep_time      : num [1:336776] 317 333 342 344 354 354 355 357 357 358 ...
##  $ sched_dep_time: num [1:336776] 315 329 340 345 360 358 360 360 360 360 ...
##  $ dep_delay     : num [1:336776] 2 4 2 39 34 36 35 37 37 38 ...
##  $ hypothesis    : num [1:336776] 317 333 342 344 394 354 395 397 397 398 ...
```

```r
#Hypothesis is correct!
```

#### 4.Find the 10 most delayed flights using a ranking function. How do you want to handle ties? Carefully read the documentation for min_rank().

```r
#solution 1: top_n()

flights %>%
  mutate(
    delays4dayz = dep_delay + arr_delay) %>%
  top_n(.,10, delays4dayz) %>%
  glimpse(.)
```

```
## Observations: 10
## Variables: 20
## $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013...
## $ month          <int> 1, 1, 12, 3, 4, 5, 6, 7, 7, 9
## $ day            <int> 9, 10, 5, 17, 10, 3, 15, 22, 22, 20
## $ dep_time       <int> 641, 1121, 756, 2321, 1100, 1133, 1432, 845, 2257, 1139
## $ sched_dep_time <int> 900, 1635, 1700, 810, 1900, 2055, 1935, 1600, 759, 1845
## $ dep_delay      <dbl> 1301, 1126, 896, 911, 960, 878, 1137, 1005, 898, 1014
## $ arr_time       <int> 1242, 1239, 1058, 135, 1342, 1250, 1607, 1044, 121, ...
## $ sched_arr_time <int> 1530, 1810, 2020, 1020, 2211, 2215, 2120, 1815, 1026...
## $ arr_delay      <dbl> 1272, 1109, 878, 915, 931, 875, 1127, 989, 895, 1007
## $ carrier        <chr> "HA", "MQ", "AA", "DL", "DL", "MQ", "MQ", "MQ", "DL"...
## $ flight         <int> 51, 3695, 172, 2119, 2391, 3744, 3535, 3075, 2047, 177
## $ tailnum        <chr> "N384HA", "N517MQ", "N5DMAA", "N927DA", "N959DL", "N...
## $ origin         <chr> "JFK", "EWR", "EWR", "LGA", "JFK", "EWR", "JFK", "JF...
## $ dest           <chr> "HNL", "ORD", "MIA", "MSP", "TPA", "ORD", "CMH", "CV...
## $ air_time       <dbl> 640, 111, 149, 167, 139, 112, 74, 96, 109, 354
## $ distance       <dbl> 4983, 719, 1085, 1020, 1005, 719, 483, 589, 762, 2586
## $ hour           <dbl> 9, 16, 17, 8, 19, 20, 19, 16, 7, 18
## $ minute         <dbl> 0, 35, 0, 10, 0, 55, 35, 0, 59, 45
## $ time_hour      <dttm> 2013-01-09 09:00:00, 2013-01-10 16:00:00, 2013-12-0...
## $ delays4dayz    <dbl> 2573, 2235, 1774, 1826, 1891, 1753, 2264, 1994, 1793...
```

```r
#If one were to instead use min_rank(), ties would be settled by choosing the minimum of the "corresponding indices," whatever that means.
```

#### 5.What does 1:3 + 1:10 return? Why?

```r
1:3 + 1:10
```

```
## Warning in 1:3 + 1:10: longer object length is not a multiple of shorter object
## length
```

```
##  [1]  2  4  6  5  7  9  8 10 12 11
```

```r
#Returns:   2  4  6  5  7  9  8 10 12 11
```
*Because 1:3 is shorter than 1:10, 1:3 "loops" as it adds along 1:10.*  
*(1 2 3 1 2 3 1 2 3 1) + (1 2 3 4 5 6 7 8 9 10)*

#### 6.What trigonometric functions does R provide?

```r
sin(pi)
```

```
## [1] 1.224606e-16
```

```r
cos(pi)
```

```
## [1] -1
```

```r
tan(pi)
```

```
## [1] -1.224647e-16
```

```r
#sec(pi) Not included
#csc(pi) Not included
#cot(pi) Not included
```

### 5.6.7

#### 5. Which carrier has the worst delays? Challenge: can you disentangle the effects of bad airports vs. bad carriers? Why/why not? (Hint: think about flights %>% group_by(carrier, dest) %>% summarise(n()))

```r
#Carrier that has longest delays, on average
glimpse(flights)
```

```
## Observations: 336,776
## Variables: 19
## $ year           <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013...
## $ month          <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1...
## $ day            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1...
## $ dep_time       <int> 517, 533, 542, 544, 554, 554, 555, 557, 557, 558, 55...
## $ sched_dep_time <int> 515, 529, 540, 545, 600, 558, 600, 600, 600, 600, 60...
## $ dep_delay      <dbl> 2, 4, 2, -1, -6, -4, -5, -3, -3, -2, -2, -2, -2, -2,...
## $ arr_time       <int> 830, 850, 923, 1004, 812, 740, 913, 709, 838, 753, 8...
## $ sched_arr_time <int> 819, 830, 850, 1022, 837, 728, 854, 723, 846, 745, 8...
## $ arr_delay      <dbl> 11, 20, 33, -18, -25, 12, 19, -14, -8, 8, -2, -3, 7,...
## $ carrier        <chr> "UA", "UA", "AA", "B6", "DL", "UA", "B6", "EV", "B6"...
## $ flight         <int> 1545, 1714, 1141, 725, 461, 1696, 507, 5708, 79, 301...
## $ tailnum        <chr> "N14228", "N24211", "N619AA", "N804JB", "N668DN", "N...
## $ origin         <chr> "EWR", "LGA", "JFK", "JFK", "LGA", "EWR", "EWR", "LG...
## $ dest           <chr> "IAH", "IAH", "MIA", "BQN", "ATL", "ORD", "FLL", "IA...
## $ air_time       <dbl> 227, 227, 160, 183, 116, 150, 158, 53, 140, 138, 149...
## $ distance       <dbl> 1400, 1416, 1089, 1576, 762, 719, 1065, 229, 944, 73...
## $ hour           <dbl> 5, 5, 5, 5, 6, 5, 6, 6, 6, 6, 6, 6, 6, 6, 6, 5, 6, 6...
## $ minute         <dbl> 15, 29, 40, 45, 0, 58, 0, 0, 0, 0, 0, 0, 0, 0, 0, 59...
## $ time_hour      <dttm> 2013-01-01 05:00:00, 2013-01-01 05:00:00, 2013-01-0...
```

```r
flights %>%
  group_by(carrier, dest) %>%
  summarize(
    ad = mean(arr_delay, na.rm = TRUE), 
    dd = mean(dep_delay, na.rm = TRUE),
    n()) %>%
  arrange(desc(ad +dd))
```

```
## # A tibble: 314 x 5
## # Groups:   carrier [16]
##    carrier dest     ad    dd `n()`
##    <chr>   <chr> <dbl> <dbl> <int>
##  1 UA      STL   110    77.5     2
##  2 OO      ORD   107    67       1
##  3 OO      DTW    68.5  61       2
##  4 UA      RDU    56    60       1
##  5 EV      PBI    40.7  48.7     6
##  6 EV      TYS    41.2  41.8   323
##  7 EV      CAE    42.8  36.7   113
##  8 EV      TUL    33.7  34.9   315
##  9 EV      OKC    30.6  30.6   346
## 10 UA      JAC    29.9  28.7    23
## # ... with 304 more rows
```

```r
#   carrier dest     ad    dd `n()`
#   <chr>   <chr> <dbl> <dbl> <int>
# 1 UA      STL   110    77.5     2
# 2 OO      ORD   107    67       1
# 3 OO      DTW    68.5  61       2
# 4 UA      RDU    56    60       1
# 5 EV      PBI    40.7  48.7     6
# 6 EV      TYS    41.2  41.8   323
# 7 EV      CAE    42.8  36.7   113
# 8 EV      TUL    33.7  34.9   315
# 9 EV      OKC    30.6  30.6   346
#10 UA      JAC    29.9  28.7    23
```

```r
#Now, how would I handle distinguishing bad airports vs bad carriers? 
#Bad airports will affect any airplanes that (dis)embark there, and bad airlines will affect all of their associated airplanes.
#flights %>%
#  group_by(carrier, dest) %>%
#  summarize(
#    ad = mean(arr_delay, na.rm = TRUE), 
#    dd = mean(dep_delay, na.rm = TRUE),
#    n()) %>%
#  arrange(desc(n()))
```

