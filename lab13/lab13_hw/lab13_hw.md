---
title: "Lab 13 Homework"
author: "Laurine Cabiling"
date: "2023-03-04"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above. For any included plots, make sure they are clearly labeled. You are free to use any plot type that you feel best communicates the results of your analysis.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the libraries  

```r
library(tidyverse)
library(janitor)
library(here)
#install.packages("ggmap")
library(ggmap)
library(naniar)
```


```r
#library(albersusa)
```

## Load the Data
We will use two separate data sets for this homework.  

1. The first [data set](https://rcweb.dartmouth.edu/~f002d69/workshops/index_rspatial.html) represent sightings of grizzly bears (Ursos arctos) in Alaska.  

2. The second data set is from Brandell, Ellen E (2021), Serological dataset and R code for: Patterns and processes of pathogen exposure in gray wolves across North America, Dryad, [Dataset](https://doi.org/10.5061/dryad.5hqbzkh51).  

1. Load the `grizzly` data and evaluate its structure.  

```r
grizzly <- read_csv(here("lab13", "data","bear-sightings.csv"))
```

```
## Rows: 494 Columns: 3
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## dbl (3): bear.id, longitude, latitude
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
glimpse(grizzly)
```

```
## Rows: 494
## Columns: 3
## $ bear.id   <dbl> 7, 57, 69, 75, 104, 108, 115, 116, 125, 135, 137, 162, 185, …
## $ longitude <dbl> -148.9560, -152.6228, -144.9374, -152.8485, -143.2948, -149.…
## $ latitude  <dbl> 62.65822, 58.35064, 62.38227, 59.90122, 61.07311, 62.91605, …
```

```r
miss_var_summary(grizzly)
```

```
## # A tibble: 3 × 3
##   variable  n_miss pct_miss
##   <chr>      <int>    <dbl>
## 1 bear.id        0        0
## 2 longitude      0        0
## 3 latitude       0        0
```

```r
summary(grizzly)
```

```
##     bear.id       longitude         latitude    
##  Min.   :   7   Min.   :-166.2   Min.   :55.02  
##  1st Qu.:2569   1st Qu.:-154.2   1st Qu.:58.13  
##  Median :4822   Median :-151.0   Median :60.97  
##  Mean   :4935   Mean   :-149.1   Mean   :61.41  
##  3rd Qu.:7387   3rd Qu.:-145.6   3rd Qu.:64.13  
##  Max.   :9996   Max.   :-131.3   Max.   :70.37
```

2. Use the range of the latitude and longitude to build an appropriate bounding box for your map.  

```r
lat <- c(55.02, 70.37)
long <- c(-166.2, -131.3)
bbox <- make_bbox(long, lat, f=0.05)
```


3. Load a map from `stamen` in a terrain style projection and display the map.  

```r
map1 <- get_map(bbox, maptype = "terrain", source = "stamen")
```

```
## ℹ Map tiles by Stamen Design, under CC BY 3.0. Data by OpenStreetMap, under ODbL.
```


4. Build a final map that overlays the recorded observations of grizzly bears in Alaska.  

```r
ggmap(map1)+
  geom_point(data = grizzly, aes(longitude, latitude), size = 0.5)+
  labs(x = "Longitude", y= "Latitude", title="Grizzly Bear Sightings")
```

![](lab13_hw_files/figure-html/unnamed-chunk-6-1.png)<!-- -->


Let's switch to the wolves data. Brandell, Ellen E (2021), Serological dataset and R code for: Patterns and processes of pathogen exposure in gray wolves across North America, Dryad, [Dataset](https://doi.org/10.5061/dryad.5hqbzkh51).  

5. Load the data and evaluate its structure.  

```r
wolves <- read_csv(here("lab13", "data", "wolves_data", "wolves_dataset.csv"))
```

```
## Rows: 1986 Columns: 23
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (4): pop, age.cat, sex, color
## dbl (19): year, lat, long, habitat, human, pop.density, pack.size, standard....
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
glimpse(wolves)
```

```
## Rows: 1,986
## Columns: 23
## $ pop                <chr> "AK.PEN", "AK.PEN", "AK.PEN", "AK.PEN", "AK.PEN", "…
## $ year               <dbl> 2006, 2006, 2006, 2006, 2006, 2006, 2006, 2006, 200…
## $ age.cat            <chr> "S", "S", "A", "S", "A", "A", "A", "P", "S", "P", "…
## $ sex                <chr> "F", "M", "F", "M", "M", "M", "F", "M", "F", "M", "…
## $ color              <chr> "G", "G", "G", "B", "B", "G", "G", "G", "G", "G", "…
## $ lat                <dbl> 57.03983, 57.03983, 57.03983, 57.03983, 57.03983, 5…
## $ long               <dbl> -157.8427, -157.8427, -157.8427, -157.8427, -157.84…
## $ habitat            <dbl> 254.08, 254.08, 254.08, 254.08, 254.08, 254.08, 254…
## $ human              <dbl> 10.42, 10.42, 10.42, 10.42, 10.42, 10.42, 10.42, 10…
## $ pop.density        <dbl> 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, 8, …
## $ pack.size          <dbl> 8.78, 8.78, 8.78, 8.78, 8.78, 8.78, 8.78, 8.78, 8.7…
## $ standard.habitat   <dbl> -1.6339, -1.6339, -1.6339, -1.6339, -1.6339, -1.633…
## $ standard.human     <dbl> -0.9784, -0.9784, -0.9784, -0.9784, -0.9784, -0.978…
## $ standard.pop       <dbl> -0.6827, -0.6827, -0.6827, -0.6827, -0.6827, -0.682…
## $ standard.packsize  <dbl> 1.3157, 1.3157, 1.3157, 1.3157, 1.3157, 1.3157, 1.3…
## $ standard.latitude  <dbl> 0.7214, 0.7214, 0.7214, 0.7214, 0.7214, 0.7214, 0.7…
## $ standard.longitude <dbl> -2.1441, -2.1441, -2.1441, -2.1441, -2.1441, -2.144…
## $ cav.binary         <dbl> 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
## $ cdv.binary         <dbl> 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, …
## $ cpv.binary         <dbl> 0, 0, 1, 1, 0, 1, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, …
## $ chv.binary         <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, …
## $ neo.binary         <dbl> NA, NA, NA, 0, 0, NA, NA, 1, 0, 1, NA, 0, NA, NA, N…
## $ toxo.binary        <dbl> NA, NA, NA, 1, 0, NA, NA, 1, 0, 0, NA, 0, NA, NA, N…
```

```r
miss_var_summary(wolves)
```

```
## # A tibble: 23 × 3
##    variable    n_miss pct_miss
##    <chr>        <int>    <dbl>
##  1 toxo.binary    827   41.6  
##  2 color          616   31.0  
##  3 chv.binary     548   27.6  
##  4 neo.binary     538   27.1  
##  5 cav.binary     321   16.2  
##  6 age.cat        102    5.14 
##  7 cdv.binary      21    1.06 
##  8 sex             19    0.957
##  9 cpv.binary       7    0.352
## 10 pop              0    0    
## # … with 13 more rows
```

```r
summary(wolves)
```

```
##      pop                 year        age.cat              sex           
##  Length:1986        Min.   :1992   Length:1986        Length:1986       
##  Class :character   1st Qu.:2006   Class :character   Class :character  
##  Mode  :character   Median :2011   Mode  :character   Mode  :character  
##                     Mean   :2010                                        
##                     3rd Qu.:2016                                        
##                     Max.   :2019                                        
##                                                                         
##     color                lat             long            habitat       
##  Length:1986        Min.   :33.89   Min.   :-157.84   Min.   :  254.1  
##  Class :character   1st Qu.:44.60   1st Qu.:-123.73   1st Qu.:10375.2  
##  Mode  :character   Median :46.83   Median :-110.99   Median :11211.3  
##                     Mean   :50.43   Mean   :-116.86   Mean   :12797.4  
##                     3rd Qu.:57.89   3rd Qu.:-110.55   3rd Qu.:11860.8  
##                     Max.   :80.50   Max.   : -82.42   Max.   :34676.6  
##                                                                        
##      human          pop.density      pack.size    standard.habitat  
##  Min.   :   0.02   Min.   : 3.74   Min.   :3.55   Min.   :-1.63390  
##  1st Qu.:  80.60   1st Qu.: 7.40   1st Qu.:5.62   1st Qu.:-0.30620  
##  Median :2787.67   Median :11.63   Median :6.37   Median :-0.19650  
##  Mean   :2335.38   Mean   :14.91   Mean   :6.47   Mean   : 0.01158  
##  3rd Qu.:3973.47   3rd Qu.:25.32   3rd Qu.:8.25   3rd Qu.:-0.11130  
##  Max.   :6228.64   Max.   :33.96   Max.   :9.56   Max.   : 2.88180  
##                                                                     
##  standard.human     standard.pop      standard.packsize standard.latitude  
##  Min.   :-0.9834   Min.   :-1.13460   Min.   :-1.7585   Min.   :-1.805900  
##  1st Qu.:-0.9444   1st Qu.:-0.74630   1st Qu.:-0.5418   1st Qu.:-0.636900  
##  Median : 0.3648   Median :-0.29760   Median :-0.1009   Median :-0.392600  
##  Mean   : 0.1461   Mean   : 0.05084   Mean   :-0.0422   Mean   :-0.000006  
##  3rd Qu.: 0.9383   3rd Qu.: 1.15480   3rd Qu.: 1.0041   3rd Qu.: 0.814300  
##  Max.   : 2.0290   Max.   : 2.07150   Max.   : 1.7742   Max.   : 3.281900  
##                                                                            
##  standard.longitude    cav.binary       cdv.binary       cpv.binary    
##  Min.   :-2.144100   Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:-0.359500   1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:1.0000  
##  Median : 0.306900   Median :1.0000   Median :0.0000   Median :1.0000  
##  Mean   :-0.000005   Mean   :0.8529   Mean   :0.2219   Mean   :0.7943  
##  3rd Qu.: 0.330200   3rd Qu.:1.0000   3rd Qu.:0.0000   3rd Qu.:1.0000  
##  Max.   : 1.801500   Max.   :1.0000   Max.   :1.0000   Max.   :1.0000  
##                      NA's   :321      NA's   :21       NA's   :7       
##    chv.binary       neo.binary      toxo.binary    
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :1.0000   Median :0.0000   Median :0.0000  
##  Mean   :0.8018   Mean   :0.2804   Mean   :0.4832  
##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.0000  
##  NA's   :548      NA's   :538      NA's   :827
```


6. How many distinct wolf populations are included in this study? Mae a new object that restricts the data to the wolf populations in the lower 48 US states.  

```r
wolves %>% 
  summarize(population = n_distinct(pop))
```

```
## # A tibble: 1 × 1
##   population
##        <int>
## 1         17
```

```r
table(wolves$pop)
```

```
## 
##  AK.PEN BAN.JAS      BC  DENALI   ELLES    GTNP  INT.AK MEXICAN      MI      MT 
##     100      96     145     154      11      60      35     181     102     351 
##   N.NWT     ONT   SE.AK     SNF  SS.NWT     YNP    YUCH 
##      67      60      10      92      34     383     105
```

```r
wolves_lower_48 <- wolves %>% 
  filter(pop == "MT"| pop == "YNP"| pop == "GTNP"| pop == "SNF"| pop == "MI" | pop == "MEXICAN")
```


7. Use the range of the latitude and longitude to build an appropriate bounding box for your map.  

```r
summary(wolves_lower_48)
```

```
##      pop                 year        age.cat              sex           
##  Length:1169        Min.   :1997   Length:1169        Length:1169       
##  Class :character   1st Qu.:2007   Class :character   Class :character  
##  Mode  :character   Median :2011   Mode  :character   Mode  :character  
##                     Mean   :2010                                        
##                     3rd Qu.:2014                                        
##                     Max.   :2019                                        
##                                                                         
##     color                lat             long            habitat     
##  Length:1169        Min.   :33.89   Min.   :-110.99   Min.   : 9511  
##  Class :character   1st Qu.:44.60   1st Qu.:-110.99   1st Qu.:11166  
##  Mode  :character   Median :44.60   Median :-110.55   Median :11211  
##                     Mean   :43.95   Mean   :-106.91   Mean   :12744  
##                     3rd Qu.:46.83   3rd Qu.:-109.17   3rd Qu.:11211  
##                     Max.   :47.75   Max.   : -86.82   Max.   :32018  
##                                                                      
##      human       pop.density      pack.size     standard.habitat   
##  Min.   :2788   Min.   : 3.99   Min.   :4.040   Min.   :-0.419600  
##  1st Qu.:3240   1st Qu.:11.63   1st Qu.:5.620   1st Qu.:-0.202400  
##  Median :3924   Median :23.03   Median :5.620   Median :-0.196500  
##  Mean   :3810   Mean   :19.33   Mean   :6.431   Mean   : 0.004642  
##  3rd Qu.:3973   3rd Qu.:28.93   3rd Qu.:8.250   3rd Qu.:-0.196500  
##  Max.   :6229   Max.   :33.96   Max.   :8.250   Max.   : 2.533100  
##                                                                    
##  standard.human    standard.pop     standard.packsize  standard.latitude
##  Min.   :0.3648   Min.   :-1.1081   Min.   :-1.47050   Min.   :-1.8059  
##  1st Qu.:0.5834   1st Qu.:-0.2976   1st Qu.:-0.54180   1st Qu.:-0.6369  
##  Median :0.9144   Median : 0.9119   Median :-0.54180   Median :-0.6369  
##  Mean   :0.8591   Mean   : 0.5197   Mean   :-0.06482   Mean   :-0.7071  
##  3rd Qu.:0.9383   3rd Qu.: 1.5378   3rd Qu.: 1.00410   3rd Qu.:-0.3926  
##  Max.   :2.0290   Max.   : 2.0715   Max.   : 1.00410   Max.   :-0.2927  
##                                                                         
##  standard.longitude   cav.binary       cdv.binary       cpv.binary    
##  Min.   :0.3069     Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.3069     1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:1.0000  
##  Median :0.3302     Median :1.0000   Median :0.0000   Median :1.0000  
##  Mean   :0.5207     Mean   :0.8342   Mean   :0.2526   Mean   :0.8764  
##  3rd Qu.:0.4022     3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.5716     Max.   :1.0000   Max.   :1.0000   Max.   :1.0000  
##                     NA's   :222      NA's   :17       NA's   :4       
##    chv.binary       neo.binary      toxo.binary    
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :1.0000   Median :0.0000   Median :0.0000  
##  Mean   :0.7903   Mean   :0.3777   Mean   :0.4817  
##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.0000  
##  NA's   :382      NA's   :388      NA's   :677
```

```r
lat_wolves <- c(33.89, 47.75)
long_wolves <- c(-110.99, -86.82)
bbox_wolves <- make_bbox(long_wolves, lat_wolves, f= 0.05)
```


8.  Load a map from `stamen` in a `terrain-lines` projection and display the map.  

```r
map2 <- get_map(bbox_wolves, maptype = "terrain-lines", source = "stamen")
```

```
## ℹ Map tiles by Stamen Design, under CC BY 3.0. Data by OpenStreetMap, under ODbL.
```

```r
ggmap(map2)
```

![](lab13_hw_files/figure-html/unnamed-chunk-12-1.png)<!-- -->


9. Build a final map that overlays the recorded observations of wolves in the lower 48 states.  

```r
ggmap(map2)+
  geom_point(data = wolves_lower_48, aes(long, lat), size = 3)
```

![](lab13_hw_files/figure-html/unnamed-chunk-13-1.png)<!-- -->


10. Use the map from #9 above, but add some aesthetics. Try to `fill` and `color` by population.  

```r
ggmap(map2)+
  geom_point(data = wolves_lower_48, aes(long, lat, color = pop), size = 3)+
  labs(x = "Longitude", y= "Latitude", title="Wolves Population")+
  scale_color_discrete(name="Population")
```

![](lab13_hw_files/figure-html/unnamed-chunk-14-1.png)<!-- -->


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences. 
