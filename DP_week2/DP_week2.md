DP_Week2
================
Cátia Reis
2022-06-12

-   [Week 2](#week-2)
    -   [Subjective experience of
        silence](#subjective-experience-of-silence)
    -   [Loading a dataset](#loading-a-dataset)
-   [References](#references)

## Week 2

### Subjective experience of silence

For my Master thesis, or, at least, for my internship, I will be
exploring **silence** somewhere in Italy. I like the concept of silence
because it can mean different things for different persons but it can
also be explored in so many different ways.

Intuitively, silence for me means :

1.  The absence of **sound** : This idea is as fascinating as me as the
    idea of *nothingness*. What is the absence of sound, and does it
    even exist? If it exists, can I experience it or does the absence of
    sound require no hearer?
2.  The absence of **noise** : What I mean by noise is, for example, the
    sound of cars when you live near a road or the sound of construction
    work.
3.  The absence of **mental noise**: Say sometimes we may feel like our
    mind is full of thoughts that go everywhere at once. This is what I
    would call *mental noise*. So silence of mind would be something
    like breathing fresh air ?

These are only a few ideas of what silence could mean, and this can vary
with people. Some people find silence in environments I would call noisy
and vice-versa.

#### Purple Hibiscus & Under the Udala Trees

Back in 2021, I did a semester in the English Master and we had to read
Chimamanda Ngozi Adichie’s *Purple Hibiscus* and Chinelo Okparanta’s
*Under the Udala Trees*. I think the topic of silence had already
started to grow on me slowly and I decided to analyze the topic of
silence in this novel. I discovered a silence that was both oppressive
and quietening as well as an expressive silence that allowed characters
to communicate with each other.

|                                                                               Purple Hibiscus                                                                                |                                                                Under The Udala Trees                                                                |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://static.fnac-static.com/multimedia/Images/FR/NR/80/11/44/4460928/1540-0/tsp20190111222358/Purple-Hibiscus.jpg" style="width:50.0%" alt="Purple Hibiscus" /> | <img src="https://images-eu.ssl-images-amazon.com/images/I/81lkwx77O5L._AC_UL600_SR600,600_.jpg" style="width:50.0%" alt="Under The Udala Trees" /> |

Ramalingam (2021) helped me do this sort of table with the pictures of
the books I am mentioning in this report.

The following quote is from *Under the Udala Trees* and is another of
silence. In this passage, the main character gets silenced by another
character :

> ‘There are punishments for people who’ve done what I’ve done,’ I began
> again, pulling myself away from him. ’Stoning and dro-’/ He placed a
> finger over my lips, and just like that, he hushed me, cancelled all
> the words that had been getting ready to make their way out of my
> mouth. (Okparanta 2017, 233)

### Loading a dataset

Sleep is another domain that fits perfectly into the topic of silence. I
think the idea of sleep without dreams can be conceived as a form of
silence of our “conscious self.” I have this idea that my “self”
somewhat ‘goes somewhere’ or simply is silent for the time I go to
sleep.

In this r code chunk section, we see how I loaded the sleep dataset :

``` r
data(sleep)   # i am loading the 'sleep' built-in dataset from R Studio
```

Let’s see it displayed in a beautiful table.

``` r
library(knitr) # necessary to use the kable function
kable(sleep)
```

| extra | group | ID  |
|------:|:------|:----|
|   0.7 | 1     | 1   |
|  -1.6 | 1     | 2   |
|  -0.2 | 1     | 3   |
|  -1.2 | 1     | 4   |
|  -0.1 | 1     | 5   |
|   3.4 | 1     | 6   |
|   3.7 | 1     | 7   |
|   0.8 | 1     | 8   |
|   0.0 | 1     | 9   |
|   2.0 | 1     | 10  |
|   1.9 | 2     | 1   |
|   0.8 | 2     | 2   |
|   1.1 | 2     | 3   |
|   0.1 | 2     | 4   |
|  -0.1 | 2     | 5   |
|   4.4 | 2     | 6   |
|   5.5 | 2     | 7   |
|   1.6 | 2     | 8   |
|   4.6 | 2     | 9   |
|   3.4 | 2     | 10  |

See you soon for a new data practical !

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-adichie_purple_2017" class="csl-entry">

Adichie, Chimamanda Ngozi. 2017. *Purple Hibiscus*. London: 4th Estate.

</div>

<div id="ref-okparanta_under_2017" class="csl-entry">

Okparanta, Chinelo. 2017. *Under the Udala Trees*. London: Granta.

</div>

<div id="ref-ramalingam_7_2021" class="csl-entry">

Ramalingam, Aravind. 2021. “7 Advanced Markdown Tips!” *Analytics
Vidhya*.
<https://medium.com/analytics-vidhya/7-advanced-markdown-tips-5a031620bf52>.

</div>

</div>
