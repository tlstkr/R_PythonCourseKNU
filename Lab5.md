Task 1
------

#### Create pmean function

``` r
pmean <- function(directory, pollutant, id = 1:332) {
  data <- data.frame()
  for(i in id) {
    data <- rbind(data, read.csv(paste(directory, sprintf("%03d.csv", i), sep="/")))
  }
  return(mean(data[,pollutant], na.rm = TRUE))
}

pmean("specdata", "sulfate", 1:10)
```

    ## [1] 4.064128

``` r
pmean("specdata", "sulfate", 55)
```

    ## [1] 3.587319

``` r
pmean("specdata", "nitrate", 1:10)
```

    ## [1] 0.7976266

Task 2
------

#### Create complete function

``` r
complete <- function(directory, id) {
  data <- data.frame()
  for(i in id) { 
    data <- rbind(data, data.frame(i, sum(complete.cases(read.csv(paste(directory, sprintf("%03d.csv", i), sep="/"))))))
  }
  return (data)
}

complete("specdata", 1)
```

    ##   i sum.complete.cases.read.csv.paste.directory..sprintf...03d.csv...
    ## 1 1                                                               117

``` r
complete("specdata", c(2, 4, 8, 10, 12))
```

    ##    i sum.complete.cases.read.csv.paste.directory..sprintf...03d.csv...
    ## 1  2                                                              1041
    ## 2  4                                                               474
    ## 3  8                                                               192
    ## 4 10                                                               148
    ## 5 12                                                                96

``` r
complete("specdata", 50:60)
```

    ##     i sum.complete.cases.read.csv.paste.directory..sprintf...03d.csv...
    ## 1  50                                                               459
    ## 2  51                                                               193
    ## 3  52                                                               812
    ## 4  53                                                               342
    ## 5  54                                                               219
    ## 6  55                                                               372
    ## 7  56                                                               642
    ## 8  57                                                               452
    ## 9  58                                                               391
    ## 10 59                                                               445
    ## 11 60                                                               448

Task 3
------

#### Create corr function

``` r
corr <- function(directory, threshold = 0) {
  res_v <- c()
  for(i in 1:332) {
    df <- read.csv(paste(directory, sprintf("%03d.csv", i), sep="/"))
    df <- df[complete.cases(df),]
    if(nrow(df) > threshold) {
      res_v <- c(res_v, cor(df[,"sulfate"], df[,"nitrate"]))
    }
  }
  return (res_v)
}

cr <- corr("specdata", 150)
head(cr); summary(cr)
```

    ## [1] -0.01895754 -0.14051254 -0.04389737 -0.06815956 -0.12350667 -0.07588814

    ##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
    ## -0.21057 -0.04999  0.09463  0.12525  0.26844  0.76313

``` r
cr <- corr("specdata", 400)
head(cr); summary(cr)
```

    ## [1] -0.01895754 -0.04389737 -0.06815956 -0.07588814  0.76312884 -0.15782860

    ##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
    ## -0.17623 -0.03109  0.10021  0.13969  0.26849  0.76313

``` r
cr <- corr("specdata", 5000)
head(cr); summary(cr) ; length(cr)
```

    ## NULL

    ## Length  Class   Mode 
    ##      0   NULL   NULL

    ## [1] 0
