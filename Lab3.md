Task 1
------

#### Create add function

``` r
add2 <- function(x,y) { 
return(as.numeric(x) + as.numeric(y))  
}

print(add2(5,9))
```

    ## [1] 14

Task 2
------

#### Create above function

``` r
above <- function(x,n = 10) { 
return(x[x>n])  
}

print(above(c(32,3,52,6,84,2,6,15)))
```

    ## [1] 32 52 84 15

Task 3
------

#### Create my\_ifelse function

``` r
my_ifelse <- function(x,exp,n) { 
if(exp == '<') {return(x[x<n])}
if(exp == '>') {return(x[x>n])}
if(exp == '<=') {return(x[x<=n])}
if(exp == '>=') {return(x[x>=n])}
if(exp == '==') {return(x[x==n])}
else {return(x)}
}

print(my_ifelse(c(4,2,6,4,7,3),'>=',4))
```

    ## [1] 4 6 4 7

Task 4
------

#### Create columnmean function

``` r
columnmean <- function(x,removeNA = TRUE) { 
  result <- c()
  if(removeNA == TRUE) {
    for(i in 1:length(x[1,])) {result[i] <- (mean(x[,i], na.rm = TRUE))}
  }
  else {
    for(i in 1:length(x[1,])) {result[i] <- (mean(x[,i], na.rm = FALSE))}
  }
return(result)
}

y = matrix(1:20,5,4)
y[1,2] = NA
y[4,3] = NA

print(columnmean(y))
```

    ## [1]  3.00  8.50 12.75 18.00
