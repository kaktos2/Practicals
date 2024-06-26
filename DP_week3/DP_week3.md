DP_week3
================
Cátia Reis
2022-06-20

-   [Practical - Week 3](#practical---week-3)
    -   [Dataset 1 - Built-in R
        dataset](#dataset-1---built-in-r-dataset)
    -   [Dataset 2 - External dataset](#dataset-2---external-dataset)
    -   [Dataset 3 - Dataset from
        dslabs](#dataset-3---dataset-from-dslabs)
-   [References](#references)

## Practical - Week 3

``` r
library(readr)
library(dslabs)
```

### Dataset 1 - Built-in R dataset

In the following code-chunk, I load the built-in R dataset called
“Titanic” in which we find basic information about passengers who have
survived the Titanic…

``` r
data(Titanic)
```

``` r
str(Titanic)
```

    ##  'table' num [1:4, 1:2, 1:2, 1:2] 0 0 35 0 0 0 17 0 118 154 ...
    ##  - attr(*, "dimnames")=List of 4
    ##   ..$ Class   : chr [1:4] "1st" "2nd" "3rd" "Crew"
    ##   ..$ Sex     : chr [1:2] "Male" "Female"
    ##   ..$ Age     : chr [1:2] "Child" "Adult"
    ##   ..$ Survived: chr [1:2] "No" "Yes"

In the R output (see above), we see that there are four CHARACTER
variables in this data set.

**Statistical data types.** These four variables are called NOMINAL
QUALITATIVE variables. I hesitated to say that the “class” variable was
*ordinal* because of the sequence “1st, 2nd, 3rd” but “crew” didn’t
quite fit in this.

### Dataset 2 - External dataset

Here, I load the dataset from The Pudding article by Wilber (2018) that
has data on **skate soundtracks** used in skateboarding videos. You can
find the dataset
[here](https://github.com/the-pudding/data/blob/master/skate-music/soundtrack_data.csv)
or in this folder just in case.

``` r
data_skate <- read.csv("https://raw.githubusercontent.com/the-pudding/data/master/skate-music/soundtrack_data.csv")
str(data_skate)
```

    ## 'data.frame':    568 obs. of  7 variables:
    ##  $ artist    : chr  "The Beatles" "Fugazi" "The Rolling Stones" "David Bowie" ...
    ##  $ tote      : int  46 43 40 39 36 35 33 30 29 28 ...
    ##  $ group     : chr  "high" "high" "high" "high" ...
    ##  $ genre_fake: chr  "rap" "rap" "rap" "rap" ...
    ##  $ year      : int  2008 2008 2008 2008 2008 2008 2008 2008 2008 2008 ...
    ##  $ genre     : chr  "Classic Rock" "Punk" "Classic Rock" "Classic Rock" ...
    ##  $ id        : int  1 2 3 4 5 6 7 8 9 10 ...

``` r
head(data_skate)
```

    ##               artist tote group genre_fake year        genre id
    ## 1        The Beatles   46  high        rap 2008 Classic Rock  1
    ## 2             Fugazi   43  high        rap 2008         Punk  2
    ## 3 The Rolling Stones   40  high        rap 2008 Classic Rock  3
    ## 4        David Bowie   39  high        rap 2008 Classic Rock  4
    ## 5      Black Sabbath   36  high        rap 2008        Metal  5
    ## 6                Sol   35  high        rap 2008   Electronic  6

There are seven variables but the author of the data set says that the
“genre_fake” column should be ignored as they used it for “testing
purposes.” <!-- cite source -->

There are three INTEGER variables (R data type is given first,
statistical type is given after the colon in the bullet list :

-   tote : quantitative discrete
-   year : qualitative
-   id : qualitative

The remaining variables are character variables :

-   artist : qualitative nominal
-   group : qualitative nominal
-   genre_fake : qualitative nominal
-   genre : qualitative nominal

### Dataset 3 - Dataset from dslabs

Now, let’s look at the `movielens` dataset found in the `dslabs` package
(Irizarry and Gill 2021).

``` r
str(movielens)
```

    ## 'data.frame':    100004 obs. of  7 variables:
    ##  $ movieId  : int  31 1029 1061 1129 1172 1263 1287 1293 1339 1343 ...
    ##  $ title    : chr  "Dangerous Minds" "Dumbo" "Sleepers" "Escape from New York" ...
    ##  $ year     : int  1995 1941 1996 1981 1989 1978 1959 1982 1992 1991 ...
    ##  $ genres   : Factor w/ 901 levels "(no genres listed)",..: 762 510 899 120 762 836 81 762 844 899 ...
    ##  $ userId   : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ rating   : num  2.5 3 3 2 4 2 2 2 3.5 2 ...
    ##  $ timestamp: int  1260759144 1260759179 1260759182 1260759185 1260759205 1260759151 1260759187 1260759148 1260759125 1260759131 ...

Out of 7 variables we have…:

-   Four integers : movieId, year, userId, timestamp
-   One character variable: title
-   One factor : genres
-   One numerical : rating.

The most important variables for this dataset are probably “title” and
“rating” which are respectively a “qualitative” and “quantitative
ordinal” variable.

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-irizarry_dslabs_2021" class="csl-entry">

Irizarry, Rafael A., and Amy Gill. 2021. “Dslabs: Data Science Labs.”
<https://CRAN.R-project.org/package=dslabs>.

</div>

<div id="ref-wickham_readr_2022" class="csl-entry">

Wickham, Hadley, Jim Hester, and Jennifer Bryan. 2022. “Readr: Read
Rectangular Text Data.” <https://CRAN.R-project.org/package=readr>.

</div>

<div id="ref-wilber_good_2018" class="csl-entry">

Wilber, Jared. 2018. “The Good, the Rad, and the Gnarly.” *The Pudding*.
<https://pudding.cool/2018/06/skate-music>.

</div>

</div>
