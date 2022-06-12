DP_week6
================
Cátia Reis
06/04/2022

-   [Week 6](#week-6)
    -   [Paper planes](#paper-planes)

## Week 6

### Paper planes

For this week’s report, the dataset I will take is from an experiment
that I did with Bastien Nespolo for a class called “Coordination,
representations, communication”. We had a condition in which a
participant (later, the teacher) would learn how to do a paper plane.
The other condition, the teacher had to teach another participant (the
student) how to do the paper plane. Finally, we measured the performance
of the flight by collecting their time and distance of flight of the
paper planes.

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 4.1.2

``` r
library(ggthemes)
```

    ## Warning: package 'ggthemes' was built under R version 4.1.3

Let’s load the dataset from the csv file that we have in the week6’s
folder:

``` r
coordination<-read.table(file="coordination.csv", header=TRUE, sep=";",dec=",") 
```

``` r
str(coordination)
```

    ## 'data.frame':    20 obs. of  12 variables:
    ##  $ participants       : int  1 2 3 4 5 6 7 8 9 10 ...
    ##  $ roles              : chr  "Teacher" "Student" "Teacher" "Student" ...
    ##  $ distance1          : int  180 405 760 420 540 310 220 500 580 410 ...
    ##  $ distance2          : int  270 420 430 240 580 230 450 550 610 430 ...
    ##  $ distance3          : int  360 540 430 280 410 580 210 230 480 520 ...
    ##  $ average_distance   : num  270 455 540 313 510 ...
    ##  $ time1              : num  1.17 0.92 2.66 1.8 2.17 2.11 1.41 2.42 2.23 2.04 ...
    ##  $ time2              : num  2.14 2.4 2.23 1.97 2.17 1.52 2.18 2.15 2.6 2.03 ...
    ##  $ time3              : num  2.33 1.07 2.23 1.46 1.17 2.62 1.78 2.2 1.92 2.04 ...
    ##  $ average_flying_time: num  1.88 1.46 2.37 1.74 1.84 2.08 1.79 2.26 2.25 2.04 ...
    ##  $ learning_time      : num  4 5.65 7.75 8.42 10.83 ...
    ##  $ feedback_percentage: num  NA 13.4 NA 26.3 NA ...

In the coordination dataset, you will find 7 numerical variables, 4
integer variables and 1 character variable.

**Question 1** : Is there an impact of feedback on the performance of
the paper planes ?

For this, let’s make a plot that allows us to visualize both time and
feedback percentage.

``` r
ggplot(coordination, aes(feedback_percentage, average_distance, colour=roles,label=rownames(coordination))) + geom_point() + labs(y = "Average distance (cm)", x = "Feedback percentage")+  geom_text(hjust = -0.4) 
```

    ## Warning: Removed 10 rows containing missing values (geom_point).

    ## Warning: Removed 10 rows containing missing values (geom_text).

![](DP_week6_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

“This boxplot an interesting line it shows, Maybe even a correlation who
knows,

The feedback percentage, A matter of age it isn’t, But yes, a great
present.

The greater the feedback, Of \[?\] there is no lack,
<!-- word missing--> The longer the distance, Maybe this is a great
performance.”

**Question 2** : Is the last throw different than the first throw of
both conditions ? <!-- changer couleurs-->

``` r
ggplot(coordination, aes(distance1, distance2, colour=roles,label=rownames(coordination))) + geom_point() + labs(y = "Distance 2", x = "Distance 1")+  geom_text(hjust = -0.4) +   theme_economist()
```

![](DP_week6_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->
