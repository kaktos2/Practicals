DP_Week4
================
Cátia Reis
2022-06-12

-   [Data practical 4](#data-practical-4)
-   [MERGE!](#merge)
-   [References](#references)

## Data practical 4

``` r
library(readr)
library(dplyr)
library(dslabs)
```

``` r
skate <- read.csv("https://raw.githubusercontent.com/the-pudding/data/master/skate-music/soundtrack_data.csv")
```

Now, let’s filter the skate dataset to look at “Electronic” music with a
total of uses in the videos that is equal or superior to 20.

``` r
skate_filter<-skate %>% filter(genre=="Electronic",tote>=10)
skate_filter
```

    ##             artist tote  group genre_fake year      genre  id
    ## 1              Sol   35   high        rap 2008 Electronic   6
    ## 2       Odd Nosdam   26   high        rap 2008 Electronic  13
    ## 3            Baron   20 medium       rock 2009 Electronic  24
    ## 4              M83   14 medium       rock 2009 Electronic  48
    ## 5            Enoch   13 medium       rock 2009 Electronic  55
    ## 6 Adeodat Warfield   11 medium       rock 2009 Electronic  78
    ## 7        John Maus   11 medium       rock 2009 Electronic  86
    ## 8          Mophono   10 medium       rock 2009 Electronic 102
    ## 9            Unkle   10 medium       rock 2009 Electronic 108

I am happy to announce that M83 is in fourth place of the most used
electronic music in skate videos.

Since there are a couple of columns we do not really care about, let’s
select those that matter.

``` r
skate_selected <- skate_filter %>% select(artist,tote,genre,year)
```

In the following code, the first rows are displayed.

``` r
head(skate_selected)
```

    ##             artist tote      genre year
    ## 1              Sol   35 Electronic 2008
    ## 2       Odd Nosdam   26 Electronic 2008
    ## 3            Baron   20 Electronic 2009
    ## 4              M83   14 Electronic 2009
    ## 5            Enoch   13 Electronic 2009
    ## 6 Adeodat Warfield   11 Electronic 2009

Now, we can find the last rows.

``` r
tail(skate_selected)
```

    ##             artist tote      genre year
    ## 4              M83   14 Electronic 2009
    ## 5            Enoch   13 Electronic 2009
    ## 6 Adeodat Warfield   11 Electronic 2009
    ## 7        John Maus   11 Electronic 2009
    ## 8          Mophono   10 Electronic 2009
    ## 9            Unkle   10 Electronic 2009

Here, you can see the structure of the dataset.

``` r
str(skate_selected)
```

    ## 'data.frame':    9 obs. of  4 variables:
    ##  $ artist: chr  "Sol" "Odd Nosdam" "Baron" "M83" ...
    ##  $ tote  : int  35 26 20 14 13 11 11 10 10
    ##  $ genre : chr  "Electronic" "Electronic" "Electronic" "Electronic" ...
    ##  $ year  : int  2008 2008 2009 2009 2009 2009 2009 2009 2009

Now, let’s arrange our data. It will show the rows ordered by “tote”
from the lowest to the highest value.

``` r
skate_arranged<-skate_selected %>% arrange(desc(tote,genre))
skate_arranged
```

    ##             artist tote      genre year
    ## 1              Sol   35 Electronic 2008
    ## 2       Odd Nosdam   26 Electronic 2008
    ## 3            Baron   20 Electronic 2009
    ## 4              M83   14 Electronic 2009
    ## 5            Enoch   13 Electronic 2009
    ## 6 Adeodat Warfield   11 Electronic 2009
    ## 7        John Maus   11 Electronic 2009
    ## 8          Mophono   10 Electronic 2009
    ## 9            Unkle   10 Electronic 2009

We can see that the most popular electronic artist is Sol.

<!--Describe any patterns or lack of patterns that you see in the data (note: you can also rearrange the data in other ways if that helps, but look at it and write up in a sentence or two your findings)-->

In the following code chunk, I decided to take the initial dataset to
see the total of times each genre was used in skate videos.

``` r
total<-skate %>% group_by(genre) %>% summarize(total_use_of_genre=sum(tote)) %>% arrange(desc(total_use_of_genre))
total
```

    ## # A tibble: 8 x 2
    ##   genre             total_use_of_genre
    ##   <chr>                          <int>
    ## 1 Indie/Alternative                889
    ## 2 Classic Rock                     727
    ## 3 Hip Hop                          666
    ## 4 Punk                             587
    ## 5 Metal                            447
    ## 6 Electronic                       391
    ## 7 Jazz/Soul                        347
    ## 8 Other                            234

Let’s use a function to see if we have NA’s in our data…

``` r
any(is.na(skate))
```

    ## [1] FALSE

If there were NA values in my dataset and I would want to exclude them,
I would use “filter(!is.na(name_of_colum_where_there_are_NA)).” But as
we have seen with the previous formula there are none.

## MERGE!

This is all I could think of when I saw we were going to join two
datasets : [a good old Friends
reference](https://youtu.be/lP2pz7E7hm4?t=15).

Let’s ‘merge’ the `results_us_election_2016` and `murders` datasets.

``` r
head(full_join(results_us_election_2016,murders))
```

    ## Joining, by = "state"

    ##          state electoral_votes clinton trump others abb        region
    ## 1   California              55    61.7  31.6    6.7  CA          West
    ## 2        Texas              38    43.2  52.2    4.5  TX         South
    ## 3      Florida              29    47.8  49.0    3.2  FL         South
    ## 4     New York              29    59.0  36.5    4.5  NY     Northeast
    ## 5     Illinois              20    55.8  38.8    5.4  IL North Central
    ## 6 Pennsylvania              20    47.9  48.6    3.6  PA     Northeast
    ##   population total
    ## 1   37253956  1257
    ## 2   25145561   805
    ## 3   19687653   669
    ## 4   19378102   517
    ## 5   12830632   364
    ## 6   12702379   457

<!-- describe relationship -->

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
