---
title: "Midterm 1"
author: "Laurine Cabiling"
date: "2023-01-31"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your code should be organized, clean, and run free from errors. Remember, you must remove the `#` for any included code chunks to run. Be sure to add your name to the author header above.  

After the first 50 minutes, please upload your code (5 points). During the second 50 minutes, you may get help from each other- but no copy/paste. Upload the last version at the end of this time, but be sure to indicate it as final. If you finish early, you are free to leave.

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean! Use the tidyverse and pipes unless otherwise indicated. This exam is worth a total of 35 points. 

Please load the following libraries.

```r
library(tidyverse)
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
## ✔ ggplot2 3.4.0      ✔ purrr   1.0.0 
## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
## ✔ tidyr   1.2.1      ✔ stringr 1.5.0 
## ✔ readr   2.1.3      ✔ forcats 0.5.2 
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
library(janitor)
```

```
## 
## Attaching package: 'janitor'
## 
## The following objects are masked from 'package:stats':
## 
##     chisq.test, fisher.test
```

In the midterm 1 folder there is a second folder called `data`. Inside the `data` folder, there is a .csv file called `ecs21351-sup-0003-SupplementS1.csv`. These data are from Soykan, C. U., J. Sauer, J. G. Schuetz, G. S. LeBaron, K. Dale, and G. M. Langham. 2016. Population trends for North American winter birds based on hierarchical models. Ecosphere 7(5):e01351. 10.1002/ecs2.1351.  

Please load these data as a new object called `ecosphere`. In this step, I am providing the code to load the data, clean the variable names, and remove a footer that the authors used as part of the original publication.

```r
ecosphere <- read_csv("data/ecs21351-sup-0003-SupplementS1.csv", skip=2) %>% 
  clean_names() %>%
  slice(1:(n() - 18)) # this removes the footer
```

Problem 1. (1 point) Let's start with some data exploration. What are the variable names?

```r
names(ecosphere)
```

```
##  [1] "order"                       "family"                     
##  [3] "common_name"                 "scientific_name"            
##  [5] "diet"                        "life_expectancy"            
##  [7] "habitat"                     "urban_affiliate"            
##  [9] "migratory_strategy"          "log10_mass"                 
## [11] "mean_eggs_per_clutch"        "mean_age_at_sexual_maturity"
## [13] "population_size"             "winter_range_area"          
## [15] "range_in_cbc"                "strata"                     
## [17] "circles"                     "feeder_bird"                
## [19] "median_trend"                "lower_95_percent_ci"        
## [21] "upper_95_percent_ci"
```

Problem 2. (1 point) Use the function of your choice to summarize the data.

```r
glimpse(ecosphere)
```

```
## Rows: 551
## Columns: 21
## $ order                       <chr> "Anseriformes", "Anseriformes", "Anserifor…
## $ family                      <chr> "Anatidae", "Anatidae", "Anatidae", "Anati…
## $ common_name                 <chr> "American Black Duck", "American Wigeon", …
## $ scientific_name             <chr> "Anas rubripes", "Anas americana", "Buceph…
## $ diet                        <chr> "Vegetation", "Vegetation", "Invertebrates…
## $ life_expectancy             <chr> "Long", "Middle", "Middle", "Long", "Middl…
## $ habitat                     <chr> "Wetland", "Wetland", "Wetland", "Wetland"…
## $ urban_affiliate             <chr> "No", "No", "No", "No", "No", "No", "No", …
## $ migratory_strategy          <chr> "Short", "Short", "Moderate", "Moderate", …
## $ log10_mass                  <dbl> 3.09, 2.88, 2.96, 3.11, 3.02, 2.88, 2.56, …
## $ mean_eggs_per_clutch        <dbl> 9.0, 7.5, 10.5, 3.5, 9.5, 13.5, 10.0, 8.5,…
## $ mean_age_at_sexual_maturity <dbl> 1.0, 1.0, 3.0, 2.5, 2.0, 1.0, 0.6, 2.0, 1.…
## $ population_size             <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ winter_range_area           <dbl> 3212473, 7145842, 1812841, 360134, 854350,…
## $ range_in_cbc                <dbl> 99.1, 61.7, 69.8, 53.7, 5.3, 0.5, 17.9, 72…
## $ strata                      <dbl> 82, 124, 37, 19, 36, 5, 26, 134, 145, 103,…
## $ circles                     <dbl> 1453, 1951, 502, 247, 470, 97, 479, 2189, …
## $ feeder_bird                 <chr> "No", "No", "No", "No", "No", "No", "No", …
## $ median_trend                <dbl> 1.014, 0.996, 1.039, 0.998, 1.004, 1.196, …
## $ lower_95_percent_ci         <dbl> 0.971, 0.964, 1.016, 0.956, 0.975, 1.152, …
## $ upper_95_percent_ci         <dbl> 1.055, 1.009, 1.104, 1.041, 1.036, 1.243, …
```

Problem 3. (2 points) How many distinct orders of birds are represented in the data?

```r
ecosphere %>% 
  summarize(distinct_orders_birds = n_distinct(order))
```

```
## # A tibble: 1 × 1
##   distinct_orders_birds
##                   <int>
## 1                    19
```

Problem 4. (2 points) Which habitat has the highest diversity (number of species) in the data?

```r
ecosphere %>% 
  group_by(habitat) %>% 
  summarize(total=n())
```

```
## # A tibble: 7 × 2
##   habitat   total
##   <chr>     <int>
## 1 Grassland    36
## 2 Ocean        44
## 3 Shrubland    82
## 4 Various      45
## 5 Wetland     153
## 6 Woodland    177
## 7 <NA>         14
```

Run the code below to learn about the `slice` function. Look specifically at the examples (at the bottom) for `slice_max()` and `slice_min()`. If you are still unsure, try looking up examples online (https://rpubs.com/techanswers88/dplyr-slice). Use this new function to answer question 5 below.

```r
?slice_max
```

Problem 5. (4 points) Using the `slice_max()` or `slice_min()` function described above which species has the largest and smallest winter range?

```r
slice_max(ecosphere, winter_range_area)
```

```
## # A tibble: 1 × 21
##   order     family commo…¹ scien…² diet  life_…³ habitat urban…⁴ migra…⁵ log10…⁶
##   <chr>     <chr>  <chr>   <chr>   <chr> <chr>   <chr>   <chr>   <chr>     <dbl>
## 1 Procella… Proce… Sooty … Puffin… Vert… Long    Ocean   No      Long        2.9
## # … with 11 more variables: mean_eggs_per_clutch <dbl>,
## #   mean_age_at_sexual_maturity <dbl>, population_size <dbl>,
## #   winter_range_area <dbl>, range_in_cbc <dbl>, strata <dbl>, circles <dbl>,
## #   feeder_bird <chr>, median_trend <dbl>, lower_95_percent_ci <dbl>,
## #   upper_95_percent_ci <dbl>, and abbreviated variable names ¹​common_name,
## #   ²​scientific_name, ³​life_expectancy, ⁴​urban_affiliate, ⁵​migratory_strategy,
## #   ⁶​log10_mass
```


```r
slice_min(ecosphere, winter_range_area)
```

```
## # A tibble: 1 × 21
##   order     family commo…¹ scien…² diet  life_…³ habitat urban…⁴ migra…⁵ log10…⁶
##   <chr>     <chr>  <chr>   <chr>   <chr> <chr>   <chr>   <chr>   <chr>     <dbl>
## 1 Passerif… Alaud… Skylark Alauda… Seed  Short   Grassl… No      Reside…    1.57
## # … with 11 more variables: mean_eggs_per_clutch <dbl>,
## #   mean_age_at_sexual_maturity <dbl>, population_size <dbl>,
## #   winter_range_area <dbl>, range_in_cbc <dbl>, strata <dbl>, circles <dbl>,
## #   feeder_bird <chr>, median_trend <dbl>, lower_95_percent_ci <dbl>,
## #   upper_95_percent_ci <dbl>, and abbreviated variable names ¹​common_name,
## #   ²​scientific_name, ³​life_expectancy, ⁴​urban_affiliate, ⁵​migratory_strategy,
## #   ⁶​log10_mass
```

Problem 6. (2 points) The family Anatidae includes ducks, geese, and swans. Make a new object `ducks` that only includes species in the family Anatidae. Restrict this new dataframe to include all variables except order and family.

```r
ducks <- ecosphere %>% 
            filter(family=="Anatidae") %>% 
            select(!c(order, family))
names(ducks)
```

```
##  [1] "common_name"                 "scientific_name"            
##  [3] "diet"                        "life_expectancy"            
##  [5] "habitat"                     "urban_affiliate"            
##  [7] "migratory_strategy"          "log10_mass"                 
##  [9] "mean_eggs_per_clutch"        "mean_age_at_sexual_maturity"
## [11] "population_size"             "winter_range_area"          
## [13] "range_in_cbc"                "strata"                     
## [15] "circles"                     "feeder_bird"                
## [17] "median_trend"                "lower_95_percent_ci"        
## [19] "upper_95_percent_ci"
```

```r
names(ecosphere)
```

```
##  [1] "order"                       "family"                     
##  [3] "common_name"                 "scientific_name"            
##  [5] "diet"                        "life_expectancy"            
##  [7] "habitat"                     "urban_affiliate"            
##  [9] "migratory_strategy"          "log10_mass"                 
## [11] "mean_eggs_per_clutch"        "mean_age_at_sexual_maturity"
## [13] "population_size"             "winter_range_area"          
## [15] "range_in_cbc"                "strata"                     
## [17] "circles"                     "feeder_bird"                
## [19] "median_trend"                "lower_95_percent_ci"        
## [21] "upper_95_percent_ci"
```

Problem 7. (2 points) We might assume that all ducks live in wetland habitat. Is this true for the ducks in these data? If there are exceptions, list the species below.

```r
ducks %>% 
  group_by(habitat) %>% 
  summarize(total=n())
```

```
## # A tibble: 2 × 2
##   habitat total
##   <chr>   <int>
## 1 Ocean       1
## 2 Wetland    43
```

```r
ducks %>% 
  filter(habitat=="Ocean")
```

```
## # A tibble: 1 × 19
##   common…¹ scien…² diet  life_…³ habitat urban…⁴ migra…⁵ log10…⁶ mean_…⁷ mean_…⁸
##   <chr>    <chr>   <chr> <chr>   <chr>   <chr>   <chr>     <dbl>   <dbl>   <dbl>
## 1 Common … Somate… Inve… Middle  Ocean   No      Short      3.31       5     2.5
## # … with 9 more variables: population_size <dbl>, winter_range_area <dbl>,
## #   range_in_cbc <dbl>, strata <dbl>, circles <dbl>, feeder_bird <chr>,
## #   median_trend <dbl>, lower_95_percent_ci <dbl>, upper_95_percent_ci <dbl>,
## #   and abbreviated variable names ¹​common_name, ²​scientific_name,
## #   ³​life_expectancy, ⁴​urban_affiliate, ⁵​migratory_strategy, ⁶​log10_mass,
## #   ⁷​mean_eggs_per_clutch, ⁸​mean_age_at_sexual_maturity
```
There is an exception is the Common Eider.

Problem 8. (4 points) In ducks, how is mean body mass associated with migratory strategy? Do the ducks that migrate long distances have high or low average body mass?

```r
names(ducks)
```

```
##  [1] "common_name"                 "scientific_name"            
##  [3] "diet"                        "life_expectancy"            
##  [5] "habitat"                     "urban_affiliate"            
##  [7] "migratory_strategy"          "log10_mass"                 
##  [9] "mean_eggs_per_clutch"        "mean_age_at_sexual_maturity"
## [11] "population_size"             "winter_range_area"          
## [13] "range_in_cbc"                "strata"                     
## [15] "circles"                     "feeder_bird"                
## [17] "median_trend"                "lower_95_percent_ci"        
## [19] "upper_95_percent_ci"
```


```r
ducks %>% 
  group_by(migratory_strategy) %>% 
  summarise(mean(log10_mass),
            total=n())
```

```
## # A tibble: 5 × 3
##   migratory_strategy `mean(log10_mass)` total
##   <chr>                           <dbl> <int>
## 1 Long                             2.87     2
## 2 Moderate                         3.11    17
## 3 Resident                         4.03     1
## 4 Short                            2.98    21
## 5 Withdrawal                       2.92     3
```
Birds have a greater mass, the shorter the migratory distance. Furthermore, long distance migratory birds seem to be the lightest on average; however, we have to be cautious as the average may be slightly biased as there were only two individuals who are long distance migratory birds. 

Problem 9. (2 points) Accipitridae is the family that includes eagles, hawks, kites, and osprey. First, make a new object `eagles` that only includes species in the family Accipitridae. Next, restrict these data to only include the variables common_name, scientific_name, and population_size.

```r
eagles <- ecosphere %>% 
  filter(family=="Accipitridae") %>% 
  select(common_name, scientific_name, population_size)
glimpse(eagles)
```

```
## Rows: 20
## Columns: 3
## $ common_name     <chr> "Bald Eagle", "Broad-winged Hawk", "Cooper's Hawk", "F…
## $ scientific_name <chr> "Haliaeetus leucocephalus", "Buteo platypterus", "Acci…
## $ population_size <dbl> NA, 1700000, 700000, 80000, 130000, NA, 50000, NA, 200…
```

Problem 10. (4 points) In the eagles data, any species with a population size less than 250,000 individuals is threatened. Make a new column `conservation_status` that shows whether or not a species is threatened.

```r
eagles_new <- eagles %>% 
  mutate(conservation_status = population_size<250000) %>% 
  select(common_name,scientific_name,population_size,conservation_status)
eagles_new
```

```
## # A tibble: 20 × 4
##    common_name         scientific_name          population_size conservation_s…¹
##    <chr>               <chr>                              <dbl> <lgl>           
##  1 Bald Eagle          Haliaeetus leucocephalus              NA NA              
##  2 Broad-winged Hawk   Buteo platypterus                1700000 FALSE           
##  3 Cooper's Hawk       Accipiter cooperii                700000 FALSE           
##  4 Ferruginous Hawk    Buteo regalis                      80000 TRUE            
##  5 Golden Eagle        Aquila chrysaetos                 130000 TRUE            
##  6 Gray Hawk           Buteo nitidus                         NA NA              
##  7 Harris's Hawk       Parabuteo unicinctus               50000 TRUE            
##  8 Hook-billed Kite    Chondrohierax uncinatus               NA NA              
##  9 Northern Goshawk    Accipiter gentilis                200000 TRUE            
## 10 Northern Harrier    Circus cyaneus                    700000 FALSE           
## 11 Red-shouldered Hawk Buteo lineatus                   1100000 FALSE           
## 12 Red-tailed Hawk     Buteo jamaicensis                2000000 FALSE           
## 13 Rough-legged Hawk   Buteo lagopus                     300000 FALSE           
## 14 Sharp-shinned Hawk  Accipiter striatus                500000 FALSE           
## 15 Short-tailed Hawk   Buteo brachyurus                      NA NA              
## 16 Snail Kite          Rostrhamus sociabilis                 NA NA              
## 17 Swainson's Hawk     Buteo swainsoni                   540000 FALSE           
## 18 White-tailed Hawk   Buteo albicaudatus                    NA NA              
## 19 White-tailed Kite   Elanus leucurus                       NA NA              
## 20 Zone-tailed Hawk    Buteo albonotatus                     NA NA              
## # … with abbreviated variable name ¹​conservation_status
```

Problem 11. (2 points) Consider the results from questions 9 and 10. Are there any species for which their threatened status needs further study? How do you know?


```r
eagles_new %>% 
  filter(is.na(conservation_status))
```

```
## # A tibble: 8 × 4
##   common_name       scientific_name          population_size conservation_status
##   <chr>             <chr>                              <dbl> <lgl>              
## 1 Bald Eagle        Haliaeetus leucocephalus              NA NA                 
## 2 Gray Hawk         Buteo nitidus                         NA NA                 
## 3 Hook-billed Kite  Chondrohierax uncinatus               NA NA                 
## 4 Short-tailed Hawk Buteo brachyurus                      NA NA                 
## 5 Snail Kite        Rostrhamus sociabilis                 NA NA                 
## 6 White-tailed Hawk Buteo albicaudatus                    NA NA                 
## 7 White-tailed Kite Elanus leucurus                       NA NA                 
## 8 Zone-tailed Hawk  Buteo albonotatus                     NA NA
```
Yes, we would want to look more into the species that are described as NA because that shows we do not have enough data on that select species, so we do not know if the need more protection. 

Problem 12. (4 points) Use the `ecosphere` data to perform one exploratory analysis of your choice. The analysis must have a minimum of three lines and two functions. You must also clearly state the question you are attempting to answer.


```r
ecosphere %>% 
  filter(family == "Alcidae") %>% 
  arrange(log10_mass) %>% 
  select(common_name, log10_mass, population_size, mean_eggs_per_clutch)
```

```
## # A tibble: 11 × 4
##    common_name        log10_mass population_size mean_eggs_per_clutch
##    <chr>                   <dbl>           <dbl>                <dbl>
##  1 Dovekie                  2.26              NA                  1  
##  2 Cassin's Auklet          2.27              NA                  1  
##  3 Ancient Murrelet         2.34              NA                  2  
##  4 Marbled Murrelet         2.34              NA                  1  
##  5 Black Guillemot          2.58              NA                  2  
##  6 Rhinoceros Auklet        2.68              NA                  1  
##  7 Pigeon Guillemot         2.72              NA                  1.5
##  8 Atlantic Puffin          2.77              NA                  1  
##  9 Razorbill                2.86              NA                  1  
## 10 Thick-billed Murre       2.98              NA                  1  
## 11 Common Murre             3                 NA                  1
```
What birds are in the Alcidae family, what are their sizes, and what can the lack of data of population size and average eggs per clutch possibly mean in terms of conservation efforts. Furthermore, is there a correlation between body mass and eggs per clutch? 

Please provide the names of the students you have worked with with during the exam:

```r
#Tatiana Aguilar 
```

Please be 100% sure your exam is saved, knitted, and pushed to your github repository. No need to submit a link on canvas, we will find your exam in your repository.
