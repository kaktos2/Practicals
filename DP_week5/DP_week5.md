DP_week5
================
Cátia Reis
2022-06-10

## Data visualization

Here are our beloved packages (bibliography in the previous reports).
<!--verifier-->

``` r
library(dslabs)
library(knitr)
library(tidyverse)
library(tidyr)
```

Here is my dataset of interest for this practical. I was looking for a
fun dataset on the web but, I was getting lost in searching. Thus, I
ended up choosing one of r’s datasets named “warpbreaks”.

First, let’s load it.

``` r
data(warpbreaks)
```

To understand this dataset, we need a bit of knowledge on weaving to
understand what the variables represent.
![](https://upload.wikimedia.org/wikipedia/commons/5/5e/Warp_and_weft_2.jpg)
This pitcure shows you what is meant by a warp.

Source: By Alfred Barlow, Ryj, PKM - Adapted from The History and
Principles of Weaving by Hand and by Power by , 1878, S. Low, Marston,
Searle & Rivington, London., CC BY-SA 3.0,
<https://commons.wikimedia.org/w/index.php?curid=94725908>

Here is its structure.

``` r
str(warpbreaks)
```

    ## 'data.frame':    54 obs. of  3 variables:
    ##  $ breaks : num  26 30 54 25 70 52 51 26 67 18 ...
    ##  $ wool   : Factor w/ 2 levels "A","B": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ tension: Factor w/ 3 levels "L","M","H": 1 1 1 1 1 1 1 1 1 2 ...

In this dataset, we find 1 numerical variable and 2 factor variables.
The break is the number of breaks in a warp. There are two types of wool
(A or B). And finally, there are three levels of tension which are low
(L), medium (M) and high (H).

``` r
str(starwars)
```

    ## tibble [87 x 14] (S3: tbl_df/tbl/data.frame)
    ##  $ name      : chr [1:87] "Luke Skywalker" "C-3PO" "R2-D2" "Darth Vader" ...
    ##  $ height    : int [1:87] 172 167 96 202 150 178 165 97 183 182 ...
    ##  $ mass      : num [1:87] 77 75 32 136 49 120 75 32 84 77 ...
    ##  $ hair_color: chr [1:87] "blond" NA NA "none" ...
    ##  $ skin_color: chr [1:87] "fair" "gold" "white, blue" "white" ...
    ##  $ eye_color : chr [1:87] "blue" "yellow" "red" "yellow" ...
    ##  $ birth_year: num [1:87] 19 112 33 41.9 19 52 47 NA 24 57 ...
    ##  $ sex       : chr [1:87] "male" "none" "none" "male" ...
    ##  $ gender    : chr [1:87] "masculine" "masculine" "masculine" "masculine" ...
    ##  $ homeworld : chr [1:87] "Tatooine" "Tatooine" "Naboo" "Tatooine" ...
    ##  $ species   : chr [1:87] "Human" "Droid" "Droid" "Human" ...
    ##  $ films     :List of 87
    ##   ..$ : chr [1:5] "The Empire Strikes Back" "Revenge of the Sith" "Return of the Jedi" "A New Hope" ...
    ##   ..$ : chr [1:6] "The Empire Strikes Back" "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith" ...
    ##   ..$ : chr [1:7] "The Empire Strikes Back" "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith" ...
    ##   ..$ : chr [1:4] "The Empire Strikes Back" "Revenge of the Sith" "Return of the Jedi" "A New Hope"
    ##   ..$ : chr [1:5] "The Empire Strikes Back" "Revenge of the Sith" "Return of the Jedi" "A New Hope" ...
    ##   ..$ : chr [1:3] "Attack of the Clones" "Revenge of the Sith" "A New Hope"
    ##   ..$ : chr [1:3] "Attack of the Clones" "Revenge of the Sith" "A New Hope"
    ##   ..$ : chr "A New Hope"
    ##   ..$ : chr "A New Hope"
    ##   ..$ : chr [1:6] "The Empire Strikes Back" "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith" ...
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "Revenge of the Sith" "A New Hope"
    ##   ..$ : chr [1:5] "The Empire Strikes Back" "Revenge of the Sith" "Return of the Jedi" "A New Hope" ...
    ##   ..$ : chr [1:4] "The Empire Strikes Back" "Return of the Jedi" "A New Hope" "The Force Awakens"
    ##   ..$ : chr "A New Hope"
    ##   ..$ : chr [1:3] "The Phantom Menace" "Return of the Jedi" "A New Hope"
    ##   ..$ : chr [1:3] "The Empire Strikes Back" "Return of the Jedi" "A New Hope"
    ##   ..$ : chr "A New Hope"
    ##   ..$ : chr [1:5] "The Empire Strikes Back" "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith" ...
    ##   ..$ : chr [1:5] "The Empire Strikes Back" "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith" ...
    ##   ..$ : chr [1:3] "The Empire Strikes Back" "Attack of the Clones" "Return of the Jedi"
    ##   ..$ : chr "The Empire Strikes Back"
    ##   ..$ : chr "The Empire Strikes Back"
    ##   ..$ : chr [1:2] "The Empire Strikes Back" "Return of the Jedi"
    ##   ..$ : chr "The Empire Strikes Back"
    ##   ..$ : chr [1:2] "Return of the Jedi" "The Force Awakens"
    ##   ..$ : chr "Return of the Jedi"
    ##   ..$ : chr "Return of the Jedi"
    ##   ..$ : chr "Return of the Jedi"
    ##   ..$ : chr "Return of the Jedi"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:2] "Attack of the Clones" "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:2] "Attack of the Clones" "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:2] "Attack of the Clones" "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "Return of the Jedi"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "Attack of the Clones" "The Phantom Menace"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "The Phantom Menace"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr "Attack of the Clones"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr "Revenge of the Sith"
    ##   ..$ : chr "Revenge of the Sith"
    ##   ..$ : chr [1:2] "Revenge of the Sith" "A New Hope"
    ##   ..$ : chr [1:2] "Attack of the Clones" "Revenge of the Sith"
    ##   ..$ : chr "Revenge of the Sith"
    ##   ..$ : chr "The Force Awakens"
    ##   ..$ : chr "The Force Awakens"
    ##   ..$ : chr "The Force Awakens"
    ##   ..$ : chr "The Force Awakens"
    ##   ..$ : chr "The Force Awakens"
    ##   ..$ : chr [1:3] "Attack of the Clones" "The Phantom Menace" "Revenge of the Sith"
    ##  $ vehicles  :List of 87
    ##   ..$ : chr [1:2] "Snowspeeder" "Imperial Speeder Bike"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Imperial Speeder Bike"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Tribubble bongo"
    ##   ..$ : chr [1:2] "Zephyr-G swoop bike" "XJ-6 airspeeder"
    ##   ..$ : chr(0) 
    ##   ..$ : chr "AT-ST"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Snowspeeder"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Tribubble bongo"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Sith speeder"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Flitknot speeder"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Koro-2 Exodrive airspeeder"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Tsmeu-6 personal wheel bike"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##  $ starships :List of 87
    ##   ..$ : chr [1:2] "X-wing" "Imperial shuttle"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "TIE Advanced x1"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "X-wing"
    ##   ..$ : chr [1:5] "Jedi starfighter" "Trade Federation cruiser" "Naboo star skiff" "Jedi Interceptor" ...
    ##   ..$ : chr [1:3] "Trade Federation cruiser" "Jedi Interceptor" "Naboo fighter"
    ##   ..$ : chr(0) 
    ##   ..$ : chr [1:2] "Millennium Falcon" "Imperial shuttle"
    ##   ..$ : chr [1:2] "Millennium Falcon" "Imperial shuttle"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "X-wing"
    ##   ..$ : chr "X-wing"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Slave 1"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Millennium Falcon"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "A-wing"
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Millennium Falcon"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Naboo Royal Starship"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Scimitar"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Jedi starfighter"
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Naboo fighter"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "Belbullab-22 starfighter"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr "T-70 X-wing fighter"
    ##   ..$ : chr(0) 
    ##   ..$ : chr(0) 
    ##   ..$ : chr [1:3] "H-type Nubian yacht" "Naboo star skiff" "Naboo fighter"

``` r
starwars_long <- starwars %>% 
  pivot_longer(c("mass","birth_year"), names_to = "variable")
starwars_long %>% head() %>% kable()
```

| name           | height | hair_color | skin_color  | eye_color | sex  | gender    | homeworld | species | films                                                                                                                                          | vehicles                            | starships                 | variable   | value |
|:---------------|-------:|:-----------|:------------|:----------|:-----|:----------|:----------|:--------|:-----------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------|:--------------------------|:-----------|------:|
| Luke Skywalker |    172 | blond      | fair        | blue      | male | masculine | Tatooine  | Human   | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Snowspeeder , Imperial Speeder Bike | X-wing , Imperial shuttle | mass       |    77 |
| Luke Skywalker |    172 | blond      | fair        | blue      | male | masculine | Tatooine  | Human   | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Snowspeeder , Imperial Speeder Bike | X-wing , Imperial shuttle | birth_year |    19 |
| C-3PO          |    167 | NA         | gold        | yellow    | none | masculine | Tatooine  | Droid   | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     |                                     |                           | mass       |    75 |
| C-3PO          |    167 | NA         | gold        | yellow    | none | masculine | Tatooine  | Droid   | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     |                                     |                           | birth_year |   112 |
| R2-D2          |     96 | NA         | white, blue | red       | none | masculine | Naboo     | Droid   | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens |                                     |                           | mass       |    32 |
| R2-D2          |     96 | NA         | white, blue | red       | none | masculine | Naboo     | Droid   | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens |                                     |                           | birth_year |    33 |

``` r
starwars_long %>% kable()
```

| name                  | height | hair_color    | skin_color          | eye_color     | sex            | gender    | homeworld      | species        | films                                                                                                                                          | vehicles                             | starships                                                                                                   | variable   |  value |
|:----------------------|-------:|:--------------|:--------------------|:--------------|:---------------|:----------|:---------------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------|:------------------------------------------------------------------------------------------------------------|:-----------|-------:|
| Luke Skywalker        |    172 | blond         | fair                | blue          | male           | masculine | Tatooine       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Snowspeeder , Imperial Speeder Bike  | X-wing , Imperial shuttle                                                                                   | mass       |   77.0 |
| Luke Skywalker        |    172 | blond         | fair                | blue          | male           | masculine | Tatooine       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Snowspeeder , Imperial Speeder Bike  | X-wing , Imperial shuttle                                                                                   | birth_year |   19.0 |
| C-3PO                 |    167 | NA            | gold                | yellow        | none           | masculine | Tatooine       | Droid          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     |                                      |                                                                                                             | mass       |   75.0 |
| C-3PO                 |    167 | NA            | gold                | yellow        | none           | masculine | Tatooine       | Droid          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     |                                      |                                                                                                             | birth_year |  112.0 |
| R2-D2                 |     96 | NA            | white, blue         | red           | none           | masculine | Naboo          | Droid          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens |                                      |                                                                                                             | mass       |   32.0 |
| R2-D2                 |     96 | NA            | white, blue         | red           | none           | masculine | Naboo          | Droid          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens |                                      |                                                                                                             | birth_year |   33.0 |
| Darth Vader           |    202 | none          | white               | yellow        | male           | masculine | Tatooine       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope                                                                 |                                      | TIE Advanced x1                                                                                             | mass       |  136.0 |
| Darth Vader           |    202 | none          | white               | yellow        | male           | masculine | Tatooine       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope                                                                 |                                      | TIE Advanced x1                                                                                             | birth_year |   41.9 |
| Leia Organa           |    150 | brown         | light               | brown         | female         | feminine  | Alderaan       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Imperial Speeder Bike                |                                                                                                             | mass       |   49.0 |
| Leia Organa           |    150 | brown         | light               | brown         | female         | feminine  | Alderaan       | Human          | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | Imperial Speeder Bike                |                                                                                                             | birth_year |   19.0 |
| Owen Lars             |    178 | brown, grey   | light               | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones, Revenge of the Sith , A New Hope                                                                                         |                                      |                                                                                                             | mass       |  120.0 |
| Owen Lars             |    178 | brown, grey   | light               | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones, Revenge of the Sith , A New Hope                                                                                         |                                      |                                                                                                             | birth_year |   52.0 |
| Beru Whitesun lars    |    165 | brown         | light               | blue          | female         | feminine  | Tatooine       | Human          | Attack of the Clones, Revenge of the Sith , A New Hope                                                                                         |                                      |                                                                                                             | mass       |   75.0 |
| Beru Whitesun lars    |    165 | brown         | light               | blue          | female         | feminine  | Tatooine       | Human          | Attack of the Clones, Revenge of the Sith , A New Hope                                                                                         |                                      |                                                                                                             | birth_year |   47.0 |
| R5-D4                 |     97 | NA            | white, red          | red           | none           | masculine | Tatooine       | Droid          | A New Hope                                                                                                                                     |                                      |                                                                                                             | mass       |   32.0 |
| R5-D4                 |     97 | NA            | white, red          | red           | none           | masculine | Tatooine       | Droid          | A New Hope                                                                                                                                     |                                      |                                                                                                             | birth_year |     NA |
| Biggs Darklighter     |    183 | black         | light               | brown         | male           | masculine | Tatooine       | Human          | A New Hope                                                                                                                                     |                                      | X-wing                                                                                                      | mass       |   84.0 |
| Biggs Darklighter     |    183 | black         | light               | brown         | male           | masculine | Tatooine       | Human          | A New Hope                                                                                                                                     |                                      | X-wing                                                                                                      | birth_year |   24.0 |
| Obi-Wan Kenobi        |    182 | auburn, white | fair                | blue-gray     | male           | masculine | Stewjon        | Human          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     | Tribubble bongo                      | Jedi starfighter , Trade Federation cruiser, Naboo star skiff , Jedi Interceptor , Belbullab-22 starfighter | mass       |   77.0 |
| Obi-Wan Kenobi        |    182 | auburn, white | fair                | blue-gray     | male           | masculine | Stewjon        | Human          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi , A New Hope                     | Tribubble bongo                      | Jedi starfighter , Trade Federation cruiser, Naboo star skiff , Jedi Interceptor , Belbullab-22 starfighter | birth_year |   57.0 |
| Anakin Skywalker      |    188 | blond         | fair                | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 | Zephyr-G swoop bike, XJ-6 airspeeder | Trade Federation cruiser, Jedi Interceptor , Naboo fighter                                                  | mass       |   84.0 |
| Anakin Skywalker      |    188 | blond         | fair                | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 | Zephyr-G swoop bike, XJ-6 airspeeder | Trade Federation cruiser, Jedi Interceptor , Naboo fighter                                                  | birth_year |   41.9 |
| Wilhuff Tarkin        |    180 | auburn, grey  | fair                | blue          | male           | masculine | Eriadu         | Human          | Revenge of the Sith, A New Hope                                                                                                                |                                      |                                                                                                             | mass       |     NA |
| Wilhuff Tarkin        |    180 | auburn, grey  | fair                | blue          | male           | masculine | Eriadu         | Human          | Revenge of the Sith, A New Hope                                                                                                                |                                      |                                                                                                             | birth_year |   64.0 |
| Chewbacca             |    228 | brown         | unknown             | blue          | male           | masculine | Kashyyyk       | Wookiee        | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | AT-ST                                | Millennium Falcon, Imperial shuttle                                                                         | mass       |  112.0 |
| Chewbacca             |    228 | brown         | unknown             | blue          | male           | masculine | Kashyyyk       | Wookiee        | The Empire Strikes Back, Revenge of the Sith , Return of the Jedi , A New Hope , The Force Awakens                                             | AT-ST                                | Millennium Falcon, Imperial shuttle                                                                         | birth_year |  200.0 |
| Han Solo              |    180 | brown         | fair                | brown         | male           | masculine | Corellia       | Human          | The Empire Strikes Back, Return of the Jedi , A New Hope , The Force Awakens                                                                   |                                      | Millennium Falcon, Imperial shuttle                                                                         | mass       |   80.0 |
| Han Solo              |    180 | brown         | fair                | brown         | male           | masculine | Corellia       | Human          | The Empire Strikes Back, Return of the Jedi , A New Hope , The Force Awakens                                                                   |                                      | Millennium Falcon, Imperial shuttle                                                                         | birth_year |   29.0 |
| Greedo                |    173 | NA            | green               | black         | male           | masculine | Rodia          | Rodian         | A New Hope                                                                                                                                     |                                      |                                                                                                             | mass       |   74.0 |
| Greedo                |    173 | NA            | green               | black         | male           | masculine | Rodia          | Rodian         | A New Hope                                                                                                                                     |                                      |                                                                                                             | birth_year |   44.0 |
| Jabba Desilijic Tiure |    175 | NA            | green-tan, brown    | orange        | hermaphroditic | masculine | Nal Hutta      | Hutt           | The Phantom Menace, Return of the Jedi, A New Hope                                                                                             |                                      |                                                                                                             | mass       | 1358.0 |
| Jabba Desilijic Tiure |    175 | NA            | green-tan, brown    | orange        | hermaphroditic | masculine | Nal Hutta      | Hutt           | The Phantom Menace, Return of the Jedi, A New Hope                                                                                             |                                      |                                                                                                             | birth_year |  600.0 |
| Wedge Antilles        |    170 | brown         | fair                | hazel         | male           | masculine | Corellia       | Human          | The Empire Strikes Back, Return of the Jedi , A New Hope                                                                                       | Snowspeeder                          | X-wing                                                                                                      | mass       |   77.0 |
| Wedge Antilles        |    170 | brown         | fair                | hazel         | male           | masculine | Corellia       | Human          | The Empire Strikes Back, Return of the Jedi , A New Hope                                                                                       | Snowspeeder                          | X-wing                                                                                                      | birth_year |   21.0 |
| Jek Tono Porkins      |    180 | brown         | fair                | blue          | male           | masculine | Bestine IV     | Human          | A New Hope                                                                                                                                     |                                      | X-wing                                                                                                      | mass       |  110.0 |
| Jek Tono Porkins      |    180 | brown         | fair                | blue          | male           | masculine | Bestine IV     | Human          | A New Hope                                                                                                                                     |                                      | X-wing                                                                                                      | birth_year |     NA |
| Yoda                  |     66 | white         | green               | brown         | male           | masculine | NA             | Yoda’s species | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi                                  |                                      |                                                                                                             | mass       |   17.0 |
| Yoda                  |     66 | white         | green               | brown         | male           | masculine | NA             | Yoda’s species | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi                                  |                                      |                                                                                                             | birth_year |  896.0 |
| Palpatine             |    170 | grey          | pale                | yellow        | male           | masculine | Naboo          | Human          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi                                  |                                      |                                                                                                             | mass       |   75.0 |
| Palpatine             |    170 | grey          | pale                | yellow        | male           | masculine | Naboo          | Human          | The Empire Strikes Back, Attack of the Clones , The Phantom Menace , Revenge of the Sith , Return of the Jedi                                  |                                      |                                                                                                             | birth_year |   82.0 |
| Boba Fett             |    183 | black         | fair                | brown         | male           | masculine | Kamino         | Human          | The Empire Strikes Back, Attack of the Clones , Return of the Jedi                                                                             |                                      | Slave 1                                                                                                     | mass       |   78.2 |
| Boba Fett             |    183 | black         | fair                | brown         | male           | masculine | Kamino         | Human          | The Empire Strikes Back, Attack of the Clones , Return of the Jedi                                                                             |                                      | Slave 1                                                                                                     | birth_year |   31.5 |
| IG-88                 |    200 | none          | metal               | red           | none           | masculine | NA             | Droid          | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | mass       |  140.0 |
| IG-88                 |    200 | none          | metal               | red           | none           | masculine | NA             | Droid          | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | birth_year |   15.0 |
| Bossk                 |    190 | none          | green               | red           | male           | masculine | Trandosha      | Trandoshan     | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | mass       |  113.0 |
| Bossk                 |    190 | none          | green               | red           | male           | masculine | Trandosha      | Trandoshan     | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | birth_year |   53.0 |
| Lando Calrissian      |    177 | black         | dark                | brown         | male           | masculine | Socorro        | Human          | The Empire Strikes Back, Return of the Jedi                                                                                                    |                                      | Millennium Falcon                                                                                           | mass       |   79.0 |
| Lando Calrissian      |    177 | black         | dark                | brown         | male           | masculine | Socorro        | Human          | The Empire Strikes Back, Return of the Jedi                                                                                                    |                                      | Millennium Falcon                                                                                           | birth_year |   31.0 |
| Lobot                 |    175 | none          | light               | blue          | male           | masculine | Bespin         | Human          | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | mass       |   79.0 |
| Lobot                 |    175 | none          | light               | blue          | male           | masculine | Bespin         | Human          | The Empire Strikes Back                                                                                                                        |                                      |                                                                                                             | birth_year |   37.0 |
| Ackbar                |    180 | none          | brown mottle        | orange        | male           | masculine | Mon Cala       | Mon Calamari   | Return of the Jedi, The Force Awakens                                                                                                          |                                      |                                                                                                             | mass       |   83.0 |
| Ackbar                |    180 | none          | brown mottle        | orange        | male           | masculine | Mon Cala       | Mon Calamari   | Return of the Jedi, The Force Awakens                                                                                                          |                                      |                                                                                                             | birth_year |   41.0 |
| Mon Mothma            |    150 | auburn        | fair                | blue          | female         | feminine  | Chandrila      | Human          | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Mon Mothma            |    150 | auburn        | fair                | blue          | female         | feminine  | Chandrila      | Human          | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | birth_year |   48.0 |
| Arvel Crynyd          |     NA | brown         | fair                | brown         | male           | masculine | NA             | Human          | Return of the Jedi                                                                                                                             |                                      | A-wing                                                                                                      | mass       |     NA |
| Arvel Crynyd          |     NA | brown         | fair                | brown         | male           | masculine | NA             | Human          | Return of the Jedi                                                                                                                             |                                      | A-wing                                                                                                      | birth_year |     NA |
| Wicket Systri Warrick |     88 | brown         | brown               | brown         | male           | masculine | Endor          | Ewok           | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | mass       |   20.0 |
| Wicket Systri Warrick |     88 | brown         | brown               | brown         | male           | masculine | Endor          | Ewok           | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | birth_year |    8.0 |
| Nien Nunb             |    160 | none          | grey                | black         | male           | masculine | Sullust        | Sullustan      | Return of the Jedi                                                                                                                             |                                      | Millennium Falcon                                                                                           | mass       |   68.0 |
| Nien Nunb             |    160 | none          | grey                | black         | male           | masculine | Sullust        | Sullustan      | Return of the Jedi                                                                                                                             |                                      | Millennium Falcon                                                                                           | birth_year |     NA |
| Qui-Gon Jinn          |    193 | brown         | fair                | blue          | male           | masculine | NA             | Human          | The Phantom Menace                                                                                                                             | Tribubble bongo                      |                                                                                                             | mass       |   89.0 |
| Qui-Gon Jinn          |    193 | brown         | fair                | blue          | male           | masculine | NA             | Human          | The Phantom Menace                                                                                                                             | Tribubble bongo                      |                                                                                                             | birth_year |   92.0 |
| Nute Gunray           |    191 | none          | mottled green       | red           | male           | masculine | Cato Neimoidia | Neimodian      | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | mass       |   90.0 |
| Nute Gunray           |    191 | none          | mottled green       | red           | male           | masculine | Cato Neimoidia | Neimodian      | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | birth_year |     NA |
| Finis Valorum         |    170 | blond         | fair                | blue          | male           | masculine | Coruscant      | Human          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Finis Valorum         |    170 | blond         | fair                | blue          | male           | masculine | Coruscant      | Human          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |   91.0 |
| Jar Jar Binks         |    196 | none          | orange              | orange        | male           | masculine | Naboo          | Gungan         | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | mass       |   66.0 |
| Jar Jar Binks         |    196 | none          | orange              | orange        | male           | masculine | Naboo          | Gungan         | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | birth_year |   52.0 |
| Roos Tarpals          |    224 | none          | grey                | orange        | male           | masculine | Naboo          | Gungan         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |   82.0 |
| Roos Tarpals          |    224 | none          | grey                | orange        | male           | masculine | Naboo          | Gungan         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Rugor Nass            |    206 | none          | green               | orange        | male           | masculine | Naboo          | Gungan         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Rugor Nass            |    206 | none          | green               | orange        | male           | masculine | Naboo          | Gungan         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Ric Olié              |    183 | brown         | fair                | blue          | NA             | NA        | Naboo          | NA             | The Phantom Menace                                                                                                                             |                                      | Naboo Royal Starship                                                                                        | mass       |     NA |
| Ric Olié              |    183 | brown         | fair                | blue          | NA             | NA        | Naboo          | NA             | The Phantom Menace                                                                                                                             |                                      | Naboo Royal Starship                                                                                        | birth_year |     NA |
| Watto                 |    137 | black         | blue, grey          | yellow        | male           | masculine | Toydaria       | Toydarian      | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | mass       |     NA |
| Watto                 |    137 | black         | blue, grey          | yellow        | male           | masculine | Toydaria       | Toydarian      | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | birth_year |     NA |
| Sebulba               |    112 | none          | grey, red           | orange        | male           | masculine | Malastare      | Dug            | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |   40.0 |
| Sebulba               |    112 | none          | grey, red           | orange        | male           | masculine | Malastare      | Dug            | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Quarsh Panaka         |    183 | black         | dark                | brown         | NA             | NA        | Naboo          | NA             | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Quarsh Panaka         |    183 | black         | dark                | brown         | NA             | NA        | Naboo          | NA             | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |   62.0 |
| Shmi Skywalker        |    163 | black         | fair                | brown         | female         | feminine  | Tatooine       | Human          | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | mass       |     NA |
| Shmi Skywalker        |    163 | black         | fair                | brown         | female         | feminine  | Tatooine       | Human          | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | birth_year |   72.0 |
| Darth Maul            |    175 | none          | red                 | yellow        | male           | masculine | Dathomir       | Zabrak         | The Phantom Menace                                                                                                                             | Sith speeder                         | Scimitar                                                                                                    | mass       |   80.0 |
| Darth Maul            |    175 | none          | red                 | yellow        | male           | masculine | Dathomir       | Zabrak         | The Phantom Menace                                                                                                                             | Sith speeder                         | Scimitar                                                                                                    | birth_year |   54.0 |
| Bib Fortuna           |    180 | none          | pale                | pink          | male           | masculine | Ryloth         | Twi’lek        | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Bib Fortuna           |    180 | none          | pale                | pink          | male           | masculine | Ryloth         | Twi’lek        | Return of the Jedi                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Ayla Secura           |    178 | none          | blue                | hazel         | female         | feminine  | Ryloth         | Twi’lek        | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | mass       |   55.0 |
| Ayla Secura           |    178 | none          | blue                | hazel         | female         | feminine  | Ryloth         | Twi’lek        | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | birth_year |   48.0 |
| Dud Bolt              |     94 | none          | blue, grey          | yellow        | male           | masculine | Vulpter        | Vulptereen     | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |   45.0 |
| Dud Bolt              |     94 | none          | blue, grey          | yellow        | male           | masculine | Vulpter        | Vulptereen     | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Gasgano               |    122 | none          | white, blue         | black         | male           | masculine | Troiken        | Xexto          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Gasgano               |    122 | none          | white, blue         | black         | male           | masculine | Troiken        | Xexto          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Ben Quadinaros        |    163 | none          | grey, green, yellow | orange        | male           | masculine | Tund           | Toong          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |   65.0 |
| Ben Quadinaros        |    163 | none          | grey, green, yellow | orange        | male           | masculine | Tund           | Toong          | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Mace Windu            |    188 | none          | dark                | brown         | male           | masculine | Haruun Kal     | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | mass       |   84.0 |
| Mace Windu            |    188 | none          | dark                | brown         | male           | masculine | Haruun Kal     | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | birth_year |   72.0 |
| Ki-Adi-Mundi          |    198 | white         | pale                | yellow        | male           | masculine | Cerea          | Cerean         | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | mass       |   82.0 |
| Ki-Adi-Mundi          |    198 | white         | pale                | yellow        | male           | masculine | Cerea          | Cerean         | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | birth_year |   92.0 |
| Kit Fisto             |    196 | none          | green               | black         | male           | masculine | Glee Anselm    | Nautolan       | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | mass       |   87.0 |
| Kit Fisto             |    196 | none          | green               | black         | male           | masculine | Glee Anselm    | Nautolan       | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      |                                                                                                             | birth_year |     NA |
| Eeth Koth             |    171 | black         | brown               | brown         | male           | masculine | Iridonia       | Zabrak         | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | mass       |     NA |
| Eeth Koth             |    171 | black         | brown               | brown         | male           | masculine | Iridonia       | Zabrak         | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | birth_year |     NA |
| Adi Gallia            |    184 | none          | dark                | blue          | female         | feminine  | Coruscant      | Tholothian     | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | mass       |   50.0 |
| Adi Gallia            |    184 | none          | dark                | blue          | female         | feminine  | Coruscant      | Tholothian     | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | birth_year |     NA |
| Saesee Tiin           |    188 | none          | pale                | orange        | male           | masculine | Iktotch        | Iktotchi       | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | mass       |     NA |
| Saesee Tiin           |    188 | none          | pale                | orange        | male           | masculine | Iktotch        | Iktotchi       | The Phantom Menace , Revenge of the Sith                                                                                                       |                                      |                                                                                                             | birth_year |     NA |
| Yarael Poof           |    264 | none          | white               | yellow        | male           | masculine | Quermia        | Quermian       | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |     NA |
| Yarael Poof           |    264 | none          | white               | yellow        | male           | masculine | Quermia        | Quermian       | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| Plo Koon              |    188 | none          | orange              | black         | male           | masculine | Dorin          | Kel Dor        | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      | Jedi starfighter                                                                                            | mass       |   80.0 |
| Plo Koon              |    188 | none          | orange              | black         | male           | masculine | Dorin          | Kel Dor        | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      | Jedi starfighter                                                                                            | birth_year |   22.0 |
| Mas Amedda            |    196 | none          | blue                | blue          | male           | masculine | Champala       | Chagrian       | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | mass       |     NA |
| Mas Amedda            |    196 | none          | blue                | blue          | male           | masculine | Champala       | Chagrian       | Attack of the Clones, The Phantom Menace                                                                                                       |                                      |                                                                                                             | birth_year |     NA |
| Gregar Typho          |    185 | black         | dark                | brown         | male           | masculine | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      | Naboo fighter                                                                                               | mass       |   85.0 |
| Gregar Typho          |    185 | black         | dark                | brown         | male           | masculine | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      | Naboo fighter                                                                                               | birth_year |     NA |
| Cordé                 |    157 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| Cordé                 |    157 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Cliegg Lars           |    183 | brown         | fair                | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| Cliegg Lars           |    183 | brown         | fair                | blue          | male           | masculine | Tatooine       | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |   82.0 |
| Poggle the Lesser     |    183 | none          | green               | yellow        | male           | masculine | Geonosis       | Geonosian      | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |   80.0 |
| Poggle the Lesser     |    183 | none          | green               | yellow        | male           | masculine | Geonosis       | Geonosian      | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |     NA |
| Luminara Unduli       |    170 | black         | yellow              | blue          | female         | feminine  | Mirial         | Mirialan       | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |   56.2 |
| Luminara Unduli       |    170 | black         | yellow              | blue          | female         | feminine  | Mirial         | Mirialan       | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |   58.0 |
| Barriss Offee         |    166 | black         | yellow              | blue          | female         | feminine  | Mirial         | Mirialan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |   50.0 |
| Barriss Offee         |    166 | black         | yellow              | blue          | female         | feminine  | Mirial         | Mirialan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |   40.0 |
| Dormé                 |    165 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| Dormé                 |    165 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Dooku                 |    193 | white         | fair                | brown         | male           | masculine | Serenno        | Human          | Attack of the Clones, Revenge of the Sith                                                                                                      | Flitknot speeder                     |                                                                                                             | mass       |   80.0 |
| Dooku                 |    193 | white         | fair                | brown         | male           | masculine | Serenno        | Human          | Attack of the Clones, Revenge of the Sith                                                                                                      | Flitknot speeder                     |                                                                                                             | birth_year |  102.0 |
| Bail Prestor Organa   |    191 | black         | tan                 | brown         | male           | masculine | Alderaan       | Human          | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |     NA |
| Bail Prestor Organa   |    191 | black         | tan                 | brown         | male           | masculine | Alderaan       | Human          | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |   67.0 |
| Jango Fett            |    183 | black         | tan                 | brown         | male           | masculine | Concord Dawn   | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |   79.0 |
| Jango Fett            |    183 | black         | tan                 | brown         | male           | masculine | Concord Dawn   | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |   66.0 |
| Zam Wesell            |    168 | blonde        | fair, green, yellow | yellow        | female         | feminine  | Zolan          | Clawdite       | Attack of the Clones                                                                                                                           | Koro-2 Exodrive airspeeder           |                                                                                                             | mass       |   55.0 |
| Zam Wesell            |    168 | blonde        | fair, green, yellow | yellow        | female         | feminine  | Zolan          | Clawdite       | Attack of the Clones                                                                                                                           | Koro-2 Exodrive airspeeder           |                                                                                                             | birth_year |     NA |
| Dexter Jettster       |    198 | none          | brown               | yellow        | male           | masculine | Ojom           | Besalisk       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |  102.0 |
| Dexter Jettster       |    198 | none          | brown               | yellow        | male           | masculine | Ojom           | Besalisk       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Lama Su               |    229 | none          | grey                | black         | male           | masculine | Kamino         | Kaminoan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |   88.0 |
| Lama Su               |    229 | none          | grey                | black         | male           | masculine | Kamino         | Kaminoan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Taun We               |    213 | none          | grey                | black         | female         | feminine  | Kamino         | Kaminoan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| Taun We               |    213 | none          | grey                | black         | female         | feminine  | Kamino         | Kaminoan       | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Jocasta Nu            |    167 | white         | fair                | blue          | female         | feminine  | Coruscant      | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| Jocasta Nu            |    167 | white         | fair                | blue          | female         | feminine  | Coruscant      | Human          | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Ratts Tyerell         |     79 | none          | grey, blue          | unknown       | male           | masculine | Aleen Minor    | Aleena         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | mass       |   15.0 |
| Ratts Tyerell         |     79 | none          | grey, blue          | unknown       | male           | masculine | Aleen Minor    | Aleena         | The Phantom Menace                                                                                                                             |                                      |                                                                                                             | birth_year |     NA |
| R4-P17                |     96 | none          | silver, red         | red, blue     | none           | feminine  | NA             | Droid          | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |     NA |
| R4-P17                |     96 | none          | silver, red         | red, blue     | none           | feminine  | NA             | Droid          | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |     NA |
| Wat Tambor            |    193 | none          | green, grey         | unknown       | male           | masculine | Skako          | Skakoan        | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |   48.0 |
| Wat Tambor            |    193 | none          | green, grey         | unknown       | male           | masculine | Skako          | Skakoan        | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| San Hill              |    191 | none          | grey                | gold          | male           | masculine | Muunilinst     | Muun           | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | mass       |     NA |
| San Hill              |    191 | none          | grey                | gold          | male           | masculine | Muunilinst     | Muun           | Attack of the Clones                                                                                                                           |                                      |                                                                                                             | birth_year |     NA |
| Shaak Ti              |    178 | none          | red, blue, white    | black         | female         | feminine  | Shili          | Togruta        | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |   57.0 |
| Shaak Ti              |    178 | none          | red, blue, white    | black         | female         | feminine  | Shili          | Togruta        | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |     NA |
| Grievous              |    216 | none          | brown, white        | green, yellow | male           | masculine | Kalee          | Kaleesh        | Revenge of the Sith                                                                                                                            | Tsmeu-6 personal wheel bike          | Belbullab-22 starfighter                                                                                    | mass       |  159.0 |
| Grievous              |    216 | none          | brown, white        | green, yellow | male           | masculine | Kalee          | Kaleesh        | Revenge of the Sith                                                                                                                            | Tsmeu-6 personal wheel bike          | Belbullab-22 starfighter                                                                                    | birth_year |     NA |
| Tarfful               |    234 | brown         | brown               | blue          | male           | masculine | Kashyyyk       | Wookiee        | Revenge of the Sith                                                                                                                            |                                      |                                                                                                             | mass       |  136.0 |
| Tarfful               |    234 | brown         | brown               | blue          | male           | masculine | Kashyyyk       | Wookiee        | Revenge of the Sith                                                                                                                            |                                      |                                                                                                             | birth_year |     NA |
| Raymus Antilles       |    188 | brown         | light               | brown         | male           | masculine | Alderaan       | Human          | Revenge of the Sith, A New Hope                                                                                                                |                                      |                                                                                                             | mass       |   79.0 |
| Raymus Antilles       |    188 | brown         | light               | brown         | male           | masculine | Alderaan       | Human          | Revenge of the Sith, A New Hope                                                                                                                |                                      |                                                                                                             | birth_year |     NA |
| Sly Moore             |    178 | none          | pale                | white         | NA             | NA        | Umbara         | NA             | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | mass       |   48.0 |
| Sly Moore             |    178 | none          | pale                | white         | NA             | NA        | Umbara         | NA             | Attack of the Clones, Revenge of the Sith                                                                                                      |                                      |                                                                                                             | birth_year |     NA |
| Tion Medon            |    206 | none          | grey                | black         | male           | masculine | Utapau         | Pau’an         | Revenge of the Sith                                                                                                                            |                                      |                                                                                                             | mass       |   80.0 |
| Tion Medon            |    206 | none          | grey                | black         | male           | masculine | Utapau         | Pau’an         | Revenge of the Sith                                                                                                                            |                                      |                                                                                                             | birth_year |     NA |
| Finn                  |     NA | black         | dark                | dark          | male           | masculine | NA             | Human          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | mass       |     NA |
| Finn                  |     NA | black         | dark                | dark          | male           | masculine | NA             | Human          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | birth_year |     NA |
| Rey                   |     NA | brown         | light               | hazel         | female         | feminine  | NA             | Human          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | mass       |     NA |
| Rey                   |     NA | brown         | light               | hazel         | female         | feminine  | NA             | Human          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | birth_year |     NA |
| Poe Dameron           |     NA | brown         | light               | brown         | male           | masculine | NA             | Human          | The Force Awakens                                                                                                                              |                                      | T-70 X-wing fighter                                                                                         | mass       |     NA |
| Poe Dameron           |     NA | brown         | light               | brown         | male           | masculine | NA             | Human          | The Force Awakens                                                                                                                              |                                      | T-70 X-wing fighter                                                                                         | birth_year |     NA |
| BB8                   |     NA | none          | none                | black         | none           | masculine | NA             | Droid          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | mass       |     NA |
| BB8                   |     NA | none          | none                | black         | none           | masculine | NA             | Droid          | The Force Awakens                                                                                                                              |                                      |                                                                                                             | birth_year |     NA |
| Captain Phasma        |     NA | unknown       | unknown             | unknown       | NA             | NA        | NA             | NA             | The Force Awakens                                                                                                                              |                                      |                                                                                                             | mass       |     NA |
| Captain Phasma        |     NA | unknown       | unknown             | unknown       | NA             | NA        | NA             | NA             | The Force Awakens                                                                                                                              |                                      |                                                                                                             | birth_year |     NA |
| Padmé Amidala         |    165 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      | H-type Nubian yacht, Naboo star skiff , Naboo fighter                                                       | mass       |   45.0 |
| Padmé Amidala         |    165 | brown         | light               | brown         | female         | feminine  | Naboo          | Human          | Attack of the Clones, The Phantom Menace , Revenge of the Sith                                                                                 |                                      | H-type Nubian yacht, Naboo star skiff , Naboo fighter                                                       | birth_year |   46.0 |

-   Make sure your data is in [tidy
    format](https://r4ds.had.co.nz/tidy-data.html)
-   Take a column in your data set and split the columns values into new
    columns with `separate()`
-   Take data from two or more columns and `unite()`
-   Create a plot using `ggplot()`
