DP_week6
================
Cátia Reis
2022-06-20

-   [The coordination dataset](#the-coordination-dataset)
    -   [Question 1](#question-1)
    -   [Question 2](#question-2)
-   [References](#references)

``` r
library(dplyr)
library(ggplot2)
library(knitr)
```

## The coordination dataset

For this week’s report, the dataset I will take is from an experiment
that I did with B. a colleague from the masters for a class called “Coordination,
representations, communication.”

In this experiment, we used a paper plane task to understand if
face-to-face interaction had an impact on learning performance. We had a
**non-interactive condition** where one participant learned to do a
paper plane by themselves by watching a [youtube video
tutorial](https://youtu.be/FlE7mRZImuQ?t=48). Then, this same
participant taught another participant how to do the paper plane and
this constituted our **interactive condition**.

Let’s load the dataset from the csv file that we have in this week 6
folder:

``` r
coordination<-read.table(file="coordination.csv", header=TRUE, sep=";",dec=",") 
head(coordination) %>% kable()
```

| participants | roles   | distance1 | distance2 | distance3 | average_distance | time1 | time2 | time3 | average_flying_time | learning_time | feedback_percentage |
|-------------:|:--------|----------:|----------:|----------:|-----------------:|------:|------:|------:|--------------------:|--------------:|--------------------:|
|            1 | Teacher |       180 |       270 |       360 |           270.00 |  1.17 |  2.14 |  2.33 |                1.88 |          4.00 |                  NA |
|            2 | Student |       405 |       420 |       540 |           455.00 |  0.92 |  2.40 |  1.07 |                1.46 |          5.65 |               13.40 |
|            3 | Teacher |       760 |       430 |       430 |           540.00 |  2.66 |  2.23 |  2.23 |                2.37 |          7.75 |                  NA |
|            4 | Student |       420 |       240 |       280 |           313.33 |  1.80 |  1.97 |  1.46 |                1.74 |          8.42 |               26.28 |
|            5 | Teacher |       540 |       580 |       410 |           510.00 |  2.17 |  2.17 |  1.17 |                1.84 |         10.83 |                  NA |
|            6 | Student |       310 |       230 |       580 |           373.33 |  2.11 |  1.52 |  2.62 |                2.08 |          5.77 |               20.83 |

Let’s look at its structure

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

In the dataset, you can see that there is a *roles* column with two
options (teacher,student). The teacher stands for the non-interactive
condition while the student stands for the interactive condition.

We measured performance by throwing the planes 3 times and we recorded
their *distance* and *time*. Finally, we also coded what we consider
*feedbacks*. We considered that the more feedbacks you had in a
student-teacher pair, the more interactive the pair was. We also
recorded *learning time* to check if it also impacted the performances.

There are 7 numerical variables, 4 integer variables and 1 character
variable.

### Question 1

**How similar is the performance of the teachers’ planes to the
students’ planes ?**

``` r
ggplot(coordination, aes(average_distance, average_flying_time, colour=roles,label=rownames(coordination))) + geom_point() + labs(y = "Average Distance (cm)", x = "Average Flying Time (sec)") +  geom_text(hjust = -0.4)
```

![](DP_week6_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

This plot displays on the x-axis the average time flew by the planes and
on the y-axis the average distance that the plane flew. The colors
represent the different conditions which allows us to see the difference
between the teachers’ planes and students’ planes. Each pair is composed
of an even number (the student) and one uneven number (the teacher).
Thus, pair 1 is composed of 1 & 2, pair 2 is 3 & 4, etc.

For example, we see that teacher 19 has both high distance and time
while their student (number 20) has done one of the ‘worse’ performances
of our data. On the other hand, we can see that 17 & 18 or even 15 & 16
did a rather similar performance.

### Question 2

**Is there an impact of feedback on the performance of the paper planes
?**

``` r
ggplot(coordination, aes(feedback_percentage, average_distance, colour=roles,label=rownames(coordination))) + geom_point() + labs(y = "Average distance (cm)", x = "Feedback percentage")+  geom_text(hjust = -0.4) 
```

    ## Warning: Removed 10 rows containing missing values (geom_point).

    ## Warning: Removed 10 rows containing missing values (geom_text).

![](DP_week6_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

This plot shows the feedback percentage that a student received from the
teacher (x-axis) and it also shows the average distance of the plane
(y-axis). We can only see the scores for the students because the
teachers had no feedback since they watched a video.

We have an outlier, **student 12** has one of the best performances and
has one of the highest percentage of feedback.

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-ggplot2" class="csl-entry">

Wickham, Hadley, Winston Chang, Lionel Henry, Thomas Lin Pedersen,
Kohske Takahashi, Claus Wilke, Kara Woo, Hiroaki Yutani, Dewey
Dunnington, and RStudio. 2022. “Ggplot2: Create Elegant Data
Visualisations Using the Grammar of Graphics.”
<https://CRAN.R-project.org/package=ggplot2>.

</div>

<div id="ref-dplyr" class="csl-entry">

Wickham, Hadley, Romain François, Lionel Henry, and Kirill Müller. 2022.
*Dplyr: A Grammar of Data Manipulation*.

</div>

<div id="ref-knitr" class="csl-entry">

Xie, Yihui. 2022. *Knitr: A General-Purpose Package for Dynamic Report
Generation in R*. <https://yihui.org/knitr/>.

</div>

</div>
