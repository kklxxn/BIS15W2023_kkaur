---
title: "cheat-sheet"
output: 
  html_document: 
    keep_md: yes
date: "2023-01-24"
---



## Lab 1

*gets current working directory*

```r
getwd()
```

```
## [1] "C:/Users/khush/Desktop/BIS15W2023_kkaur"
```
*arithmetic order of operations applies*
*help on method*

```r
?mean
```

```
## starting httpd help server ... done
```

*vectors*

```r
example_1 <- c(1,2,3,4,5,6) # c is concatenate
```
- operations on vectors

```r
mean(example_1)
```

```
## [1] 3.5
```

```r
median(example_1)
```

```
## [1] 3.5
```

```r
sd(example_1)
```

```
## [1] 1.870829
```


## Lab 2: objects and data classes
*operations to work with objects*

```r
#making the objects
red <- 34
yellow <- 45
purple <- 29
```

```r
sum(red,yellow)
```

```
## [1] 79
```

*classes*

```r
my_numeric <- 42 
my_integer <- 2L #adding an L automatically denotes an integer
my_character <- "universe"
my_logical <- FALSE
my_complex <- 2+4i
```


```r
#important functions
class(my_character) #class of x
```

```
## [1] "character"
```

```r
is.integer(my_character) # checks is x is of specified type, Boolean return
```

```
## [1] FALSE
```

```r
new_integer <- as.character(my_integer) # changes class of x to specified class
class(new_integer)
```

```
## [1] "character"
```
*NA values*

```r
bleh <- NA
is.na(bleh) # checks if bleh is NA type
```

```
## [1] TRUE
```

```r
anyNA(bleh) #same as above but more useful for vectors, data matrices and data frame
```

```
## [1] TRUE
```

```r
blehbleh <- c(1,5,2,NA,4,6)
mean(blehbleh, na.rm = T ) #na. tells function whether to include the NA value or not
```

```
## [1] 3.6
```

```r
mean(blehbleh) # will give a null value without it
```

```
## [1] NA
```
# Data Structures
In addition to classes of data, R also organizes data in different ways. These are called data structures and include vectors, lists, matrices, data frames, and factors. For now, we will focus on `vectors`.  

# Vectors
Vectors are a common way of organizing data in R.  We create vectors using the `c` command. The `c` stands for concatenate. 


```r
#creating a seqeuence
v <- c(1:50)
v
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
## [26] 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50
```

```r
#evaluating
v <= 25
```

```
##  [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
## [13]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
## [25]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
## [37] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
## [49] FALSE FALSE
```

```r
# to get only elements
v[v<= 25]
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
```
*accesing elements*

```r
days_of_the_week <- c("Monday", "Tuesday", "Wednesday", "Thrusday", "Friday", "Saturday", "Sunday")
days_of_the_week[3]
```

```
## [1] "Wednesday"
```

# Data Matrices
Data matrices are a series of stacked vectors, similar to a data table. In the example below, we build a new data matrix using the matrix command.

