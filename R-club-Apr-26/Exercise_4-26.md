# Homework



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Including Plots

You can also embed plots, for example:

![](Exercise_4-26_files/figure-html/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.


```r
library("tidyverse")
```

```
## Warning: package 'tidyverse' was built under R version 3.3.3
```

```
## Loading tidyverse: ggplot2
## Loading tidyverse: tibble
## Loading tidyverse: tidyr
## Loading tidyverse: readr
## Loading tidyverse: purrr
## Loading tidyverse: dplyr
```

```
## Warning: package 'ggplot2' was built under R version 3.3.3
```

```
## Warning: package 'tibble' was built under R version 3.3.3
```

```
## Warning: package 'tidyr' was built under R version 3.3.3
```

```
## Warning: package 'readr' was built under R version 3.3.3
```

```
## Warning: package 'purrr' was built under R version 3.3.3
```

```
## Warning: package 'dplyr' was built under R version 3.3.3
```

```
## Conflicts with tidy packages ----------------------------------------------
```

```
## filter(): dplyr, stats
## lag():    dplyr, stats
```

```r
## Exercise 1
ggplot(data = mpg)
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

```r
# An empty layer with no dots

mpg
```

```
## # A tibble: 234 ¡Á 11
##    manufacturer      model displ  year   cyl      trans   drv   cty   hwy
##           <chr>      <chr> <dbl> <int> <int>      <chr> <chr> <int> <int>
## 1          audi         a4   1.8  1999     4   auto(l5)     f    18    29
## 2          audi         a4   1.8  1999     4 manual(m5)     f    21    29
## 3          audi         a4   2.0  2008     4 manual(m6)     f    20    31
## 4          audi         a4   2.0  2008     4   auto(av)     f    21    30
## 5          audi         a4   2.8  1999     6   auto(l5)     f    16    26
## 6          audi         a4   2.8  1999     6 manual(m5)     f    18    26
## 7          audi         a4   3.1  2008     6   auto(av)     f    18    27
## 8          audi a4 quattro   1.8  1999     4 manual(m5)     4    18    26
## 9          audi a4 quattro   1.8  1999     4   auto(l5)     4    16    25
## 10         audi a4 quattro   2.0  2008     4 manual(m6)     4    20    28
## # ... with 224 more rows, and 2 more variables: fl <chr>, class <chr>
```

```r
#234 rows, 11 columns

?mpg
```

```
## starting httpd help server ...
```

```
##  done
```

```r
#drv f = front-wheel drive, r = rear wheel drive, 4 = 4wd (for types of wheel drive?)

ggplot(data = mpg)+
  geom_point(mapping = aes(x = cyl, y = hwy))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-2.png)<!-- -->

```r
ggplot(data = mpg)+
  geom_point(mapping = aes(x = drv, y = class))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-3.png)<!-- -->

```r
#random dots, not useful because they are not consecutive variables and are not closely related

##Exercise 2
ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, color = "blue"))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-4.png)<!-- -->

```r
#If color is in the  bracket, it is referred to the variable in the dataset, not the property of the graph

?mpg
# categorical: trans, drv, fl, class, year 
#continuous: displ, cyl, cty, hwy

ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, color = cty))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-5.png)<!-- -->

```r
#continuous color changes
ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, size = cty))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-6.png)<!-- -->

```r
#continuous size changes
#ggplot(data = mpg)+
  #geom_point(mapping = aes(x = displ, y = hwy, shape = cty))
#Error: A continuous variable can not be mapped to shape

ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, size = cty, color = cty))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-7.png)<!-- -->

```r
#combination of multiple aesthetics

?geom_point
ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, shape = class), stroke = 3)
```

```
## Warning: The shape palette can deal with a maximum of 6 discrete values
## because more than 6 becomes difficult to discriminate; you have 7.
## Consider specifying shapes manually if you must have them.
```

```
## Warning: Removed 62 rows containing missing values (geom_point).
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-8.png)<!-- -->

```r
#modify the width of the border, only for circles?

ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ, y = hwy, color = displ < 5))
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-9.png)<!-- -->

```r
#seperate colors of the dots by value of displ

#Exercise 3
 ggplot(data = mpg)+
 geom_point(mapping = aes(x = displ, y = hwy))+
 facet_wrap(~ cty, nrow = 2)
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-10.png)<!-- -->

```r
# A bunch of splitted graphs, not useful
#It means that there is no specific data in that cell where drv is r and cyls are 4&5
ggplot(data = mpg)+
 geom_point(mapping = aes(x = displ, y = hwy))+
 facet_grid(drv ~ .)
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-11.png)<!-- -->

```r
ggplot(data = mpg)+
 geom_point(mapping = aes(x = displ, y = hwy))+
 facet_grid(. ~ cyl)
```

![](Exercise_4-26_files/figure-html/unnamed-chunk-1-12.png)<!-- -->

```r
#The . means that we only split the graph by one variable but we keep that in one row/column, depending on the dot's position in the backet

#Advantage: we can take every type of class individually, with a bigger dataset it is more efficient
#disadvantage: it loses an overall view of the whole dataset

#nrow and ncolumn mean the max number of rows/columns
#Because the 2 variable themselves have a specific number of rows/columns

#because it is easier to read when have more columns than more rows(?)
```
