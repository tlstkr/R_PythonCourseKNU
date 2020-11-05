Task 1
------

#### Create atomic varaibles

``` r
char <- 'a'
num <- 0.5
int <- 1L
comp <- 1+4i 
bool <- TRUE
```

Task 2
------

#### Create vectors

``` r
v <- 5:75
v <- c(3.14, 2.71, 0, 13)
v <- rep(TRUE, 100)
```

Task 3
------

#### Create matrix

``` r
m <- matrix(c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1), nrow = 4, ncol = 3)
v <- cbind(c(0.5, 3.9, 0, 2), c(1.3, 131, 2.2, 7), c(3.5, 2.8, 4.6, 5.1))
```

Task 4
------

#### Create list

``` r
l <- list(char, num, int, comp, bool)
```

Task 5
------

#### Create three-leveled factor

``` r
f <- factor(c('baby', 'child', 'adult'), levels = c('baby', 'child', 'adult'))
```

Task 6
------

#### Find NA

``` r
v <- c(1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11)
min(which(is.na(v)))
```

    ## [1] 5

``` r
sum(is.na(v))
```

    ## [1] 3

Task 7
------

#### Create dataframe

``` r
survey <- data.frame("index" = c(1, 2, 3, 4, 5),
                     "sex" = c("m", "m", "m", "f", "f"),
                     "age" = c(99, 46, 23, 54, 23))
```

Task 8
------

#### Change dataframe names

``` r
names(survey) <- c('Index','Sex','Age')
```
