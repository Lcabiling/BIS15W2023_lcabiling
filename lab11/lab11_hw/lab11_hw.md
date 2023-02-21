---
title: "Lab 11 Homework"
author: "Laurine Cabiling"
date: "2023-02-21"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above. For any included plots, make sure they are clearly labeled. You are free to use any plot type that you feel best communicates the results of your analysis.  

**In this homework, you should make use of the aesthetics you have learned. It's OK to be flashy!**

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  


```r
#install.packages("RColorBrewer")
#install.packages("paletteer")
#install.packages("ggthemes")
```

## Load the libraries

```r
library(tidyverse)
library(janitor)
library(here)
library(naniar)
library(RColorBrewer)
library(paletteer)
library(ggthemes)
```


```r
ls("package:ggthemes")[grepl("theme_", ls("package:ggthemes"))]
```

```
##  [1] "theme_base"            "theme_calc"            "theme_clean"          
##  [4] "theme_economist"       "theme_economist_white" "theme_excel"          
##  [7] "theme_excel_new"       "theme_few"             "theme_fivethirtyeight"
## [10] "theme_foundation"      "theme_gdocs"           "theme_hc"             
## [13] "theme_igray"           "theme_map"             "theme_pander"         
## [16] "theme_par"             "theme_solarized"       "theme_solarized_2"    
## [19] "theme_solid"           "theme_stata"           "theme_tufte"          
## [22] "theme_wsj"
```

## Resources
The idea for this assignment came from [Rebecca Barter's](http://www.rebeccabarter.com/blog/2017-11-17-ggplot2_tutorial/) ggplot tutorial so if you get stuck this is a good place to have a look.  

## Gapminder
For this assignment, we are going to use the dataset [gapminder](https://cran.r-project.org/web/packages/gapminder/index.html). Gapminder includes information about economics, population, and life expectancy from countries all over the world. You will need to install it before use. This is the same data that we will use for midterm 2 so this is good practice.

```r
#install.packages("gapminder")
library("gapminder")
```

## Questions
The questions below are open-ended and have many possible solutions. Your approach should, where appropriate, include numerical summaries and visuals. Be creative; assume you are building an analysis that you would ultimately present to an audience of stakeholders. Feel free to try out different `geoms` if they more clearly present your results.  


```r
options(scipen=999)
```

**1. Use the function(s) of your choice to get an idea of the overall structure of the data frame, including its dimensions, column names, variable classes, etc. As part of this, determine how NA's are treated in the data.**  

```r
glimpse(gapminder)
```

```
## Rows: 1,704
## Columns: 6
## $ country   <fct> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan", …
## $ continent <fct> Asia, Asia, Asia, Asia, Asia, Asia, Asia, Asia, Asia, Asia, …
## $ year      <int> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997, …
## $ lifeExp   <dbl> 28.801, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.8…
## $ pop       <int> 8425333, 9240934, 10267083, 11537966, 13079460, 14880372, 12…
## $ gdpPercap <dbl> 779.4453, 820.8530, 853.1007, 836.1971, 739.9811, 786.1134, …
```

```r
dim(gapminder)
```

```
## [1] 1704    6
```

```r
names(gapminder)
```

```
## [1] "country"   "continent" "year"      "lifeExp"   "pop"       "gdpPercap"
```

```r
naniar::miss_var_summary(gapminder)
```

```
## # A tibble: 6 × 3
##   variable  n_miss pct_miss
##   <chr>      <int>    <dbl>
## 1 country        0        0
## 2 continent      0        0
## 3 year           0        0
## 4 lifeExp        0        0
## 5 pop            0        0
## 6 gdpPercap      0        0
```

```r
hist(gapminder$lifeExp)
```

![](lab11_hw_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

```r
gapminder
```

```
## # A tibble: 1,704 × 6
##    country     continent  year lifeExp      pop gdpPercap
##    <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
##  1 Afghanistan Asia       1952    28.8  8425333      779.
##  2 Afghanistan Asia       1957    30.3  9240934      821.
##  3 Afghanistan Asia       1962    32.0 10267083      853.
##  4 Afghanistan Asia       1967    34.0 11537966      836.
##  5 Afghanistan Asia       1972    36.1 13079460      740.
##  6 Afghanistan Asia       1977    38.4 14880372      786.
##  7 Afghanistan Asia       1982    39.9 12881816      978.
##  8 Afghanistan Asia       1987    40.8 13867957      852.
##  9 Afghanistan Asia       1992    41.7 16317921      649.
## 10 Afghanistan Asia       1997    41.8 22227415      635.
## # … with 1,694 more rows
```

**2. Among the interesting variables in gapminder is life expectancy. How has global life expectancy changed between 1952 and 2007?**
The average global life expectancy has increased between 1952 and 2007.

```r
gapminder %>% 
  filter(year >= 1952, year <= 2007) %>% 
  mutate(year=as.factor(year)) %>% 
  group_by(year) %>%
  mutate(global_life_exp = mean(lifeExp)) %>% 
  arrange(desc(global_life_exp)) %>% 
  ggplot(aes(x=year, y=global_life_exp))+
  geom_line()+
  geom_point(shape=5)+
  labs(title = "Global Life Expectancy (1952-2007)",
       x = "Year",
       y = "Global Life Expectancy")+
  theme(plot.title = element_text(size=rel(1.25), hjust=0.5))+
  theme_clean()
```

![](lab11_hw_files/figure-html/unnamed-chunk-12-1.png)<!-- -->

```r
gapminder %>% 
  filter(year >=1952 | year<=2007) %>% 
  mutate(year=as.factor(year)) %>% 
  ggplot(aes(x=lifeExp, group=year, fill=year))+
  geom_density(alpha=0.5)+
  labs(title = "Distribution of Global Life Expectancy",
       x = "Year",
       y = "Life Expectancy") +
  theme(plot.title = element_text(size=rel(1.25), hjust=0.5))
```

![](lab11_hw_files/figure-html/unnamed-chunk-13-1.png)<!-- -->


**3. How do the distributions of life expectancy compare for the years 1952 and 2007?**


```r
gapminder %>% 
  filter(year == 1952 | year == 2007) %>% 
  mutate(year=as.factor(year)) %>% 
  select(country, year, lifeExp) %>% 
  ggplot(aes(group = year, x=year, y=lifeExp, fill=year))+
  geom_boxplot()+
  labs(title = "Distribution of Life Expectancy (1952 v. 2007)",
       x = "Year",
       y = "Life Expectancy") +
  theme(plot.title = element_text(size=rel(1.25), hjust=0.5))+
  theme_clean()
```

![](lab11_hw_files/figure-html/unnamed-chunk-14-1.png)<!-- -->


```r
gapminder %>% 
  filter(year==1952 | year==2007) %>% 
  mutate(year=as.factor(year)) %>% 
  ggplot(aes(x=lifeExp, group=year, fill=year))+
  geom_density(alpha=0.5)+
  labs(title = "Distribution of Life Expectancy (1952 v. 2007)",
       x = "Year",
       y = "Life Expectancy") +
  theme(plot.title = element_text(size=rel(1.25), hjust=0.5))
```

![](lab11_hw_files/figure-html/unnamed-chunk-15-1.png)<!-- -->


**4. Your answer above doesn't tell the whole story since life expectancy varies by region. Make a summary that shows the min, mean, and max life expectancy by continent for all years represented in the data.**


```r
gapminder %>% 
  group_by(continent, year) %>% 
  summarise(min_life_exp = min(lifeExp),
            mean_life_exp = mean(lifeExp),
            max_life_exp = max(lifeExp),
            .groups='keep')
```

```
## # A tibble: 60 × 5
## # Groups:   continent, year [60]
##    continent  year min_life_exp mean_life_exp max_life_exp
##    <fct>     <int>        <dbl>         <dbl>        <dbl>
##  1 Africa     1952         30            39.1         52.7
##  2 Africa     1957         31.6          41.3         58.1
##  3 Africa     1962         32.8          43.3         60.2
##  4 Africa     1967         34.1          45.3         61.6
##  5 Africa     1972         35.4          47.5         64.3
##  6 Africa     1977         36.8          49.6         67.1
##  7 Africa     1982         38.4          51.6         69.9
##  8 Africa     1987         39.9          53.3         71.9
##  9 Africa     1992         23.6          53.6         73.6
## 10 Africa     1997         36.1          53.6         74.8
## # … with 50 more rows
```

**5. How has life expectancy changed between 1952-2007 for each continent?**

```r
gapminder %>% 
  group_by(continent) %>% 
  ggplot(aes(x=continent, y=lifeExp, fill=continent))+
  geom_boxplot()+
  labs(title = "Distribution of life expectancy of each continent",
       x = "Continent",
       y = "Life Expectancy (year)")+
  theme(plot.title = element_text(hjust = 0.5))+
  theme_clean()
```

![](lab11_hw_files/figure-html/unnamed-chunk-17-1.png)<!-- -->

```r
gapminder %>% 
  group_by(year, continent) %>% 
  summarize(mean=mean(lifeExp),
            .groups = 'keep') %>% 
  ggplot(aes(x=year, y=mean, group=continent, color=continent))+
  geom_line()+
    labs(title = "Distribution of life expectancy of each continent",
       x = "Continent",
       y = "Life Expectancy (year)")+
  theme(plot.title = element_text(hjust = 0.5))
```

![](lab11_hw_files/figure-html/unnamed-chunk-18-1.png)<!-- -->


**6. We are interested in the relationship between per capita GDP and life expectancy; i.e. does having more money help you live longer?**
Yes, there seems to be some relationship between per capita GDP and life expectancy, specifically more money does seem to play a part in surviving to an older age.

```r
gapminder %>% 
  ggplot(aes(x=lifeExp, y=gdpPercap))+
  geom_point()+
  labs(title = "Relationship between per capita GDP and life expectancy",
       x = "Life Expectancy (year)",
       y = "Per Capita GDP")+
  theme(plot.title = element_text(hjust = 0.5))+
  theme_clean()
```

![](lab11_hw_files/figure-html/unnamed-chunk-19-1.png)<!-- -->

**7. Which countries have had the largest population growth since 1952?**

```r
gapminder %>% 
  select(country, year, pop) %>% 
  filter(year == 1952 | year == 2007) %>% 
  pivot_wider(names_from = year,
              values_from = pop,
              names_prefix = "yr_") %>% 
  mutate(delta = yr_2007 - yr_1952) %>% 
  arrange(desc(delta))
```

```
## # A tibble: 142 × 4
##    country         yr_1952    yr_2007     delta
##    <fct>             <int>      <int>     <int>
##  1 China         556263527 1318683096 762419569
##  2 India         372000000 1110396331 738396331
##  3 United States 157553000  301139947 143586947
##  4 Indonesia      82052000  223547000 141495000
##  5 Brazil         56602560  190010647 133408087
##  6 Pakistan       41346560  169270617 127924057
##  7 Bangladesh     46886859  150448339 103561480
##  8 Nigeria        33119096  135031164 101912068
##  9 Mexico         30144317  108700891  78556574
## 10 Philippines    22438691   91077287  68638596
## # … with 132 more rows
```

**8. Use your results from the question above to plot population growth for the top five countries since 1952.**

```r
gapminder %>% 
  filter(country == "China" | 
          country == "India" |
          country == "United States" |
          country == "Indonesia" |
          country == "Brazil") %>% 
  select(country,year,pop) %>% 
  ggplot(aes(x=year, y=pop, color = country))+
  geom_line()+
  theme(axis.text.x = element_text(angle = 60, hjust = 1))+
  labs(title = "Top 5 Countries of Population Growth",
       x = "Year",
       y = "Population")
```

![](lab11_hw_files/figure-html/unnamed-chunk-21-1.png)<!-- -->


**9. How does per-capita GDP growth compare between these same five countries?**

```r
gapminder %>% 
  filter(country == "China" | 
          country == "India" |
          country == "United States" |
          country == "Indonesia" |
          country == "Brazil") %>% 
  select(country,year, gdpPercap) %>% 
  ggplot(aes(x=year, y=gdpPercap, color = country))+
  geom_line()+
  theme(axis.text.x = element_text(angle = 60, hjust = 1))+
  labs(title = "Top 5 Countries of GDP/capita Growth",
       x = "Year",
       y = "GDP/capita")+
  theme_clean()
```

![](lab11_hw_files/figure-html/unnamed-chunk-22-1.png)<!-- -->

**10. Make one plot of your choice that uses faceting!**


```r
gapminder %>% 
  filter(country == "China" | 
          country == "India" |
          country == "United States" |
          country == "Indonesia" |
          country == "Brazil") %>% 
  select(country,year, gdpPercap, continent) %>% 
  ggplot(aes(x=year, y=gdpPercap, color = country))+
  geom_line()+
  facet_wrap(.~continent)+
  theme(axis.text.x = element_text(angle = 60, hjust = 1))+
  labs(title = "Top 5 Countries of GDP/capita Growth",
       x = "Year",
       y = "GDP/capita")
```

![](lab11_hw_files/figure-html/unnamed-chunk-23-1.png)<!-- -->

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences. 
