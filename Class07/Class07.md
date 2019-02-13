Class 7 Functions and Packages
================
Joshua Chevez
January 30, 2019

Functions revisited
-------------------

Load(i.e.**source**) our rescale() function from last day.

``` r
source("http://tinyurl.com/rescale-R")
```

Test this function

``` r
rescale(1:5)
```

    ## [1] 0.00 0.25 0.50 0.75 1.00

``` r
rescale(c(1:5, "string"))
```

We want to make this function more robust to these types of errors

``` r
rescale2(c(1:5, "string"))
```

``` r
is.numeric(1:5)
```

    ## [1] TRUE

``` r
is.numeric("string")
```

    ## [1] FALSE

``` r
is.numeric(c(1:5, "string"))
```

    ## [1] FALSE

``` r
!is.numeric(c(1:5, "string"))
```

    ## [1] TRUE

``` r
!is.numeric(c(1:5))
```

    ## [1] FALSE

``` r
x <- c( 1, 2, NA, 3, NA)
y <- c(NA, 3, NA, 3, 4)
```

``` r
is.na(x)
```

    ## [1] FALSE FALSE  TRUE FALSE  TRUE

``` r
is.na(y)
```

    ## [1]  TRUE FALSE  TRUE FALSE FALSE

``` r
is.na(x) & is.na(y)
```

    ## [1] FALSE FALSE  TRUE FALSE FALSE

``` r
#How many NA elements in both vectors
sum(is.na(x) & is.na(y))
```

    ## [1] 1

``` r
#what position is the NAx2
which(is.na(x) & is.na(y))
```

    ## [1] 3

Now take our working snippet and make a first function

``` r
both_na <- function(x, y) {
sum(is.na(x) & is.na(y)) 
}
```

``` r
both_na(x, y)
```

    ## [1] 1

``` r
x1 <- c(NA, NA, NA)
y1 <- c( 1, NA, NA)
y2 <- c( 1, NA, NA, NA)
y3 <- c(1, NA, NA, NA, NA)
both_na(x1, y3)
```

    ## Warning in is.na(x) & is.na(y): longer object length is not a multiple of
    ## shorter object length

    ## [1] 4

``` r
#shorter vectors repeat
```

``` r
both_na2(x1, y2)
```

``` r
both_na3(x, y)
```

    ## Found 1 NA's at position(s):3

    ## $number
    ## [1] 1
    ## 
    ## $which
    ## [1] 3
