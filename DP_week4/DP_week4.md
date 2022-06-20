DP_Week4
================
Cátia Reis
2022-06-20

-   [Skate music dataset](#skate-music-dataset)
    -   [Filtering](#filtering)
    -   [Selecting](#selecting)
    -   [Displaying rows](#displaying-rows)
    -   [Structure](#structure)
    -   [Arranging](#arranging)
    -   [Summarizing](#summarizing)
    -   [NA](#na)
-   [Joining two datasets](#joining-two-datasets)
-   [References](#references)

``` r
library(readr)
library(dplyr)
library(dslabs)
library(knitr)
```

## Skate music dataset

I load the same dataset that used in week 3. It is the dataset from The
Pudding article by Wilber (2018). You can find the dataset
[here](https://github.com/the-pudding/data/blob/master/skate-music/soundtrack_data.csv)
or in the week 3 folder.

``` r
skate <- read.csv("https://raw.githubusercontent.com/the-pudding/data/master/skate-music/soundtrack_data.csv")
```

### Filtering

Now, let’s filter the skate dataset to look at “Electronic” music with a
total of uses in the videos that is equal or superior to 10.

``` r
skate_filter<-skate %>% filter(genre=="Electronic",tote>=10)
skate_filter %>% kable()
```

| artist           | tote | group  | genre_fake | year | genre      |  id |
|:-----------------|-----:|:-------|:-----------|-----:|:-----------|----:|
| Sol              |   35 | high   | rap        | 2008 | Electronic |   6 |
| Odd Nosdam       |   26 | high   | rap        | 2008 | Electronic |  13 |
| Baron            |   20 | medium | rock       | 2009 | Electronic |  24 |
| M83              |   14 | medium | rock       | 2009 | Electronic |  48 |
| Enoch            |   13 | medium | rock       | 2009 | Electronic |  55 |
| Adeodat Warfield |   11 | medium | rock       | 2009 | Electronic |  78 |
| John Maus        |   11 | medium | rock       | 2009 | Electronic |  86 |
| Mophono          |   10 | medium | rock       | 2009 | Electronic | 102 |
| Unkle            |   10 | medium | rock       | 2009 | Electronic | 108 |

From this list, I only know M83. We can see that they are in fourth
place of the most used electronic music in skate videos.

### Selecting

Since there are a couple of columns we do not really care about, let’s
select those that matter.

``` r
skate_selected <- skate_filter %>% select(artist,tote,genre,year)
```

### Displaying rows

In the following code, the first rows are displayed.

``` r
head(skate_selected) %>% kable()
```

| artist           | tote | genre      | year |
|:-----------------|-----:|:-----------|-----:|
| Sol              |   35 | Electronic | 2008 |
| Odd Nosdam       |   26 | Electronic | 2008 |
| Baron            |   20 | Electronic | 2009 |
| M83              |   14 | Electronic | 2009 |
| Enoch            |   13 | Electronic | 2009 |
| Adeodat Warfield |   11 | Electronic | 2009 |

Now, we can find the last rows.

``` r
tail(skate_selected) %>% kable()
```

|     | artist           | tote | genre      | year |
|:----|:-----------------|-----:|:-----------|-----:|
| 4   | M83              |   14 | Electronic | 2009 |
| 5   | Enoch            |   13 | Electronic | 2009 |
| 6   | Adeodat Warfield |   11 | Electronic | 2009 |
| 7   | John Maus        |   11 | Electronic | 2009 |
| 8   | Mophono          |   10 | Electronic | 2009 |
| 9   | Unkle            |   10 | Electronic | 2009 |

### Structure

Here, you can see the structure of the dataset.

``` r
str(skate_selected)
```

    ## 'data.frame':    9 obs. of  4 variables:
    ##  $ artist: chr  "Sol" "Odd Nosdam" "Baron" "M83" ...
    ##  $ tote  : int  35 26 20 14 13 11 11 10 10
    ##  $ genre : chr  "Electronic" "Electronic" "Electronic" "Electronic" ...
    ##  $ year  : int  2008 2008 2009 2009 2009 2009 2009 2009 2009

### Arranging

Now, let’s arrange our data. It will show the rows ordered by “tote”
from the highest to the lowest value.

``` r
skate_arranged<-skate_selected %>% arrange(desc(tote,genre))
skate_arranged %>% kable()
```

| artist           | tote | genre      | year |
|:-----------------|-----:|:-----------|-----:|
| Sol              |   35 | Electronic | 2008 |
| Odd Nosdam       |   26 | Electronic | 2008 |
| Baron            |   20 | Electronic | 2009 |
| M83              |   14 | Electronic | 2009 |
| Enoch            |   13 | Electronic | 2009 |
| Adeodat Warfield |   11 | Electronic | 2009 |
| John Maus        |   11 | Electronic | 2009 |
| Mophono          |   10 | Electronic | 2009 |
| Unkle            |   10 | Electronic | 2009 |

We can see that the most popular electronic artist is Sol.

### Summarizing

In the following code chunk, I decided to take the initial dataset to
see the total of times each genre was used in skate videos.

``` r
total<-skate %>% group_by(genre) %>% summarize(total_use_of_genre=sum(tote)) %>% arrange(desc(total_use_of_genre))
total %>% kable()
```

| genre             | total_use_of_genre |
|:------------------|-------------------:|
| Indie/Alternative |                889 |
| Classic Rock      |                727 |
| Hip Hop           |                666 |
| Punk              |                587 |
| Metal             |                447 |
| Electronic        |                391 |
| Jazz/Soul         |                347 |
| Other             |                234 |

### NA

Let’s use a function to see if we have NA’s in our data…

``` r
any(is.na(skate))
```

    ## [1] FALSE

If there were NA values in my dataset and I would want to exclude them,
I would use “filter(!is.na(name_of_colum_where_there_are_NA)).” But as
we have seen with the previous formula there are none.

## Joining two datasets

![Friends Chandler -
’MERGE’lol](https://i.makeagif.com/media/6-14-2016/35CLe6.gif)

Let’s ‘merge’ the `results_us_election_2016` and `murders` datasets.

``` r
head(full_join(results_us_election_2016,murders)) %>% kable()
```

    ## Joining, by = "state"

| state        | electoral_votes | clinton | trump | others | abb | region        | population | total |
|:-------------|----------------:|--------:|------:|-------:|:----|:--------------|-----------:|------:|
| California   |              55 |    61.7 |  31.6 |    6.7 | CA  | West          |   37253956 |  1257 |
| Texas        |              38 |    43.2 |  52.2 |    4.5 | TX  | South         |   25145561 |   805 |
| Florida      |              29 |    47.8 |  49.0 |    3.2 | FL  | South         |   19687653 |   669 |
| New York     |              29 |    59.0 |  36.5 |    4.5 | NY  | Northeast     |   19378102 |   517 |
| Illinois     |              20 |    55.8 |  38.8 |    5.4 | IL  | North Central |   12830632 |   364 |
| Pennsylvania |              20 |    47.9 |  48.6 |    3.6 | PA  | Northeast     |   12702379 |   457 |

I could look at the relationship between region and the votes for
clinton, trump and others to understand. This could potentially tell us
if there is a certain tendency to vote for either on of the candidates
depending on which region you come from. I would probably start by
filtering the “region” column.

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-irizarry_dslabs_2021" class="csl-entry">

Irizarry, Rafael A., and Amy Gill. 2021. “Dslabs: Data Science Labs.”
<https://CRAN.R-project.org/package=dslabs>.

</div>

<div id="ref-dplyr" class="csl-entry">

Wickham, Hadley, Romain François, Lionel Henry, and Kirill Müller. 2022.
*Dplyr: A Grammar of Data Manipulation*.

</div>

<div id="ref-wickham_readr_2022" class="csl-entry">

Wickham, Hadley, Jim Hester, and Jennifer Bryan. 2022. “Readr: Read
Rectangular Text Data.” <https://CRAN.R-project.org/package=readr>.

</div>

<div id="ref-wilber_good_2018" class="csl-entry">

Wilber, Jared. 2018. “The Good, the Rad, and the Gnarly.”
<https://pudding.cool/2018/06/skate-music>.

</div>

<div id="ref-knitr" class="csl-entry">

Xie, Yihui. 2022. *Knitr: A General-Purpose Package for Dynamic Report
Generation in R*. <https://yihui.org/knitr/>.

</div>

</div>
