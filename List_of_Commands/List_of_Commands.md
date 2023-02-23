---
title: "List_of_Commands"
author: "Laurine Cabiling"
date: "2023-01-23"
output: 
  html_document: 
    keep_md: yes
---



#Intro
This is a list of commands from lecture, excluding commands we may have used independtly from homework assignments. Not all the codes are runable because there is no connected files.

##All Packages/libraries 

```r
#install.packages("tidyverse")
#install.packages("janitor")
#install.packages("skimr")
#install.packages("palmerpenguins")
#install.packages("naniar")
#install.packages("here")
#install.packages("RColorBrewer")
#install.packages("paletteer")
#install.packages("ggthemes")
#install.packages("gtools")
```







#install.packages("")# Lab 1 commands

```r
#get working directory
#getwd()
#set working directory 
#setwd()
```


```r
#making a vector or string of values into an object 
# c means concatenate
x <- c(3,43,7,8,534)
```


```r
#mean of object
mean(x)
```

```
## [1] 119
```


```r
#median of object
median(x)
```

```
## [1] 8
```

## "#" = titles 
## = reduced font size, the more # = reduced size
smallest font size 
_italics_
**bold**
line break = two places 

## Links 
[website name]
(website link)
(mailto: email address)


```r
#input code chunk with mac is ...
#`option+command+i`
```


```r
#install.packages("name of package")
#library("name of package") to download data every session
```


```r
#ggplot(data, subset(x = factor(cyl))) + geom_bar()
#to create a plot graph?
```

#Lab 2 commands


```r
#assigning values to an object 
x <- 34
s <- 44
```


```r
#printing object 
x
```

```
## [1] 34
```


```r
#suming objects 
distance <- sum(x,s)
```

## Types of Data

```r
#Five frequently used classes of data: 
  # 1. numeric
  # 2. integer - adding an L automatically denotes an integer
  # 3. character
  # 4. logical
  # 5. complex
my_numeric <- 43
my_integer <- 2L 
my_character <- "universe"
my_logical <- FALSE
my_complex <- 2+4i
```


```r
#find class of function
class(my_numeric)
```

```
## [1] "numeric"
```


```r
# is my numeric an integer? 
is.integer(my_numeric)
```

```
## [1] FALSE
```


```r
# create a new object specified as a different class
my_integer <- as.integer(my_numeric)
```


```r
# is there NA in my data - says which data is T/F
is.na(x)
```

```
## [1] FALSE
```


```r
# are there any NAs in my data - T/F
anyNA(x)
```

```
## [1] FALSE
```


```r
#to remove any NAs when calculating
# na.rm = T
mean(x, na.rm = T)
```

```
## [1] 34
```

data structures include...
  vectors
  lists
  matrices
  data frames
  factors
  

```r
#numeric vector
my_vector <- c(20,34,23)
```


```r
#character vector
days_of_the_week <- c("sunday", "monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday")
```


```r
# generate a sequence of numbers
my_vector_sequence <- c(1:100)
```


```r
# use [] to pull out elements in a vector
days_of_the_week[3]
```

```
## [1] "tuesday"
```


```r
# pull out data greater than ...
my_vector_sequence > 80
```

```
##   [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [13] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [25] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [37] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [49] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
##  [85]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [97]  TRUE  TRUE  TRUE  TRUE
```

```r
# pull out data greater than or equal to ...
my_vector_sequence >= 49
```

```
##   [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [13] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [25] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [37] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [49]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [61]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [73]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [85]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [97]  TRUE  TRUE  TRUE  TRUE
```

```r
# pull out data less than ...
my_vector_sequence < 30
```

```
##   [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [13]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [25]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [37] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [49] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [85] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [97] FALSE FALSE FALSE FALSE
```

```r
# pull out data less than or equal to...
my_vector_sequence <= 43
```

```
##   [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [13]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [25]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
##  [37]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE
##  [49] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [85] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [97] FALSE FALSE FALSE FALSE
```

```r
# pull out data equal to ...
my_vector_sequence == 39
```

```
##   [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [13] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [25] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [37] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [49] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [85] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
##  [97] FALSE FALSE FALSE FALSE
```

```r
# Use [] to get the values, not the logical evaluation
my_vector_sequence[my_vector_sequence <= 20]
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

## How to do Data Matrices 


```r
Philosophers_Stone <- c(317.5, 657.1)
Chamber_of_Secrets <- c(261.9, 616.9)
Prisoner_of_Azkaban <- c(249.5, 547.1)
Goblet_of_Fire <- c(290.0, 606.8)
Order_of_the_Phoenix <- c(292.0, 647.8)
Half_Blood_Prince <- c(301.9, 632.4)
Deathly_Hallows_1 <- c(295.9, 664.3)
Deathly_Hallows_2 <- c(381.0, 960.5)
```


```r
#combine all objects into one
box_office <- c(Philosophers_Stone, Chamber_of_Secrets, Prisoner_of_Azkaban, Goblet_of_Fire, Order_of_the_Phoenix, Half_Blood_Prince, Deathly_Hallows_1, Deathly_Hallows_2)
```


```r
#create the matrix, and organize using `nrow` and `byrow`
harry_potter_matrix <- matrix(box_office, nrow = 8, byrow = T)
```


```r
#name the vectors for the rows and columns 
region <- c("US", "non-US")
titles <- c("Philosophers_Stone", "Chamber_of_Secrets", "Prisoner_of_Azkaban", "Goblet_of_Fire", "Order_of_the_Phoenix", "Half_Blood_Prince", "Deathly_Hallows_1", "Deathly_Hallows_2")
```


```r
#name the columns
colnames(harry_potter_matrix) <- region
#name the rows
rownames(harry_potter_matrix) <- titles
```


```r
# print the matrix
harry_potter_matrix
```

```
##                         US non-US
## Philosophers_Stone   317.5  657.1
## Chamber_of_Secrets   261.9  616.9
## Prisoner_of_Azkaban  249.5  547.1
## Goblet_of_Fire       290.0  606.8
## Order_of_the_Phoenix 292.0  647.8
## Half_Blood_Prince    301.9  632.4
## Deathly_Hallows_1    295.9  664.3
## Deathly_Hallows_2    381.0  960.5
```


```r
#sum the rows 
global <- rowSums(harry_potter_matrix)
```


```r
#add new column to show calculation
all_harry_potter_matrix <- cbind(harry_potter_matrix, global)
```


```r
#sum the columns
final_earnings <- colSums(all_harry_potter_matrix)
```


```r
# pull out data, the first value is the column, then the row
harry_potter_matrix[2,1]
```

```
## [1] 261.9
```

```r
# pull out data, `:` selects specified elements in a column
harry_potter_matrix[1:4]
```

```
## [1] 317.5 261.9 249.5 290.0
```


```r
#calculate an entire row or column
non_us_earnings <- all_harry_potter_matrix[ ,2]
mean(non_us_earnings)
```

```
## [1] 666.6125
```

# Lab 3 commands 
Building data frames


```r
Sex <- c("Male", "Female", "Male")
Length <- c(3.2, 3.7, 3.4)
Weight <- c(2.9, 4.0, 3.1)
```


```r
#get the data frame
hbirds <- data.frame(Sex, Length, Weight)
```


```r
# column names
names(hbirds)
```

```
## [1] "Sex"    "Length" "Weight"
```


```r
# dimensions of data frame
dim(hbirds)
```

```
## [1] 3 3
```


```r
# structure of data frame
str(hbirds)
```

```
## 'data.frame':	3 obs. of  3 variables:
##  $ Sex   : chr  "Male" "Female" "Male"
##  $ Length: num  3.2 3.7 3.4
##  $ Weight: num  2.9 4 3.1
```


```r
# switching to lowercase
hbirds <- data.frame(sex = Sex, length_in = Length, weight_oz = Weight)
```


```r
#Select values in an entire column using `$` sign. 
w <- hbirds$weight_oz
```


```r
#add new data using `rbind()`, bind new vector to data frame row-wise
new_bird <- c("Female", 3.6, 3.9)
hbirds <- rbind(hbirds, new_bird)
```


```r
# adding columns
hbirds$neighborhood <- c("Lakewood", "Brentwood", "Lakewood", "Scenic Heights")
```


```r
#Saving our dataframe as a csv
write.csv(hbirds, "hbirds_data.csv", row.names = FALSE)
```


```r
#Opening a .csv file & give it a name
hbirds <- readr::read_csv("hbirds_data.csv")
```

```
## Rows: 4 Columns: 4
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (2): sex, neighborhood
## dbl (2): length_in, weight_oz
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```


```r
#Looking at the data frame in different ways

#structure
#str()

#a type of summary
#glimpse()

#a type of summary
#summary()

#number of rows or observations
#nrow()

#number of columns or variables 
#ncol()

#dimensions
#dim()

#names of column
#name()

#prints the first n rows of the data frame
#head(data, n = )

#prints the last n rows of the data frame
#tail(data, n = )

#table - useful when limited number of categorical variables
#table(data$variable)

#See the data frame in the separate tab
#View()
```


```r
#Looking at a class within the data frame
class(hbirds$neighborhood)
```

```
## [1] "character"
```

```r
#looking at the level within the data frame
levels(hbirds$neightborhood)
```

```
## Warning: Unknown or uninitialised column: `neightborhood`.
```

```
## NULL
```

```r
#changing the class of data
hbirds$neighborhood <- as.factor(hbirds$neighborhood)
```


```r
#subsets are to pull out observations that meet a critera in a variable
# little_fish <- subset(fish, length <= 110)
```

##Lab 4 commands


```r
#select is to filter but with columns instead of rows
#select(fish, "lakeid", "scalelength")
```


```r
#to add range of columns
#select(fish, fish_id:length)
```


```r
# use - operator to select everything except these variables
#select(fish, -fish_id, -annumber, -length)
```


```r
#select columns that contain a character string
#select(fish, contains("length"))

#select columns that start with this name
#select(fish, starts_with("radii"))

#select columns that end with a charater string
#select(fish, ends_with())

#select columns that match a regular expression
#select(fish, matches())

#select column names that are from a group of names
#select(fish, one_of())

#a column contains a letter (in this case "a") followed by a subsequent string (in this case "er").  
#select(fish,matches("a.+er"))

#select column based on class of data
#select_if(fish, is.numeric)

#select all columns that are NOT a class of data, add `~`
#select_if(fish,~is.numeric(.))
```


```r
#renaming columns
#mammals_new <- rename(mammals, genus = "Genus",wean_mass = "wean mass", max_life = "max. life", litter_size = "litter size", litters_per_year = "litters/year")

#to lower case all of the columns
#mammals <- select_all(mammals, tolower)

#to upper case all of the columns
#mammals <- select_all(mammals, toupper)

#to remove the blank spaces
#select_all(mammals, ~str_replace(., " ","_"))
#select_all(mammals, ~str_replace(., "[ ._/]", "" ))
```


```r
# filter extracts data that meets specific criteria within a variable
#filter(fish, lakeid == "AL")

# filter allows to use the expected operators to filter through data ;
  # >, >=, <, <=, != (not equal), and == (equal)

# filter multiple values within same variable
#filter(fish, length %in% c(167,175))

#between
#filter(fish, between(scalelength, 2.5, 3))

#extract observations "near" a certain value, and specify a tolerance
#filter(fish, near(radii_length_mm, 2, tol = 0.2))

#filter to extract data based on multiple conditions
#filter(fish, lakeid == "AL", length == 350)

# `|` operator means or 
#filter(fish, lakeid == "AL" | lenght > 350)

#will return rows where both conditions are met
#filter(condition1, condition2)

# will return all rows where condition one is true but condition 2 is not.  
#filter(condition1, !condition2)

# will return rows where condition 1 and/or condition 2 is met.  
#filter(condition1 | condition2)
  
# will return all rows where only one of the conditions is met, and not when both conditions are met. 
#filter(xor(condition1, condition2))
```


##Lab 5

How to change classes efficiently when wanting to change all of one class into another class 

```r
#mammals %>% mutate_if(is.character, as.factor)
```

In order to start combining `select()`, `filter()`, and other functions efficiently, we need to learn pipes. Pipes feed the output from one function into the input of another function. This helps us keep our code sequential and clean.  
### shift+Cmd+M to get pipe --- can combine column and row 

```r
#fish_subset <- fish %>% 
  #filter(lakeid == "AL" | lakeid == "AR") %>% 
  #filter(radii_length_mm >= 2, radii_length_mm <= 4)
```

The `arrange()` command is a bit like a sort command in excel. Note that the default is ascending order.  
To sort in decreasing order, wrap the variable name in `desc()`.

```r
#fish %>% 
  #select(lakeid, scalelength) %>% 
  #arrange(scalelength)
```

## `mutate()`  
Mutate allows us to create a new column from existing columns in a data frame. We are doing a small introduction here and will add some additional functions later. Let's convert the length variable from cm to millimeters and create a new variable called length_mm.  

### can do calculations and add it as a new column 

```r
#fish %>% 
 # mutate(length_mm = length*10) %>% 
 # select(fish_id, length, length_mm)
```

## `mutate_all()`
This last function is super helpful when cleaning data. With "wild" data, there are often mixed entries (upper and lowercase), blank spaces, odd characters, etc. These all need to be dealt with before analysis. 

```r
#mammals %>%
 # mutate_all(tolower)

#mammals %>% 
  #mutate(across(c("order", "family"), tolower))
```

## `if_else()`
We will briefly introduce `if_else()` here because it allows us to use `mutate()` but not have the entire column affected in the same way. In a sense, this can function like find and replace in a spreadsheet program. With `ifelse()`, you first specify a logical statement, afterwards what needs to happen if the statement returns `TRUE`, and lastly what needs to happen if it's  `FALSE`.  

mutating or changing all of the -999.00 into NA

```r
#mammals %>% 
  #select(genus, species, newborn) %>%
  #mutate(newborn_new = ifelse(newborn == -999.00, NA, newborn))%>% 
  #arrange(newborn)
```

Check out the way I am loading these data. If I know there are NAs, I can take care of them at the beginning. But, we should do this very cautiously. At times it is better to keep the original columns and data intact.  

```r
#superhero_info <- readr::read_csv("data/heroes_information.csv", na = c("", "-99", "-"))
#superhero_powers <- readr::read_csv("data/super_hero_powers.csv", na = c("", "-99", "-"))
```

The `clean_names` function takes care of everything in one line! Now that's a superpower!

```r
#superhero_powers <- janitor::clean_names(superhero_powers)

#superhero_info <-
 #janitor::clean_names(superhero_info)
```

## `tabyl`
The `janitor` package has many awesome functions that we will explore. Here is its version of `table` which not only produces counts but also percentages. Very handy! Let's use it to explore the proportion of good guys and bad guys in the `superhero_info` data.  


```r
#tabyl(superhero_info, alignment)
```


```r
#superhero_powers %>% 
 # filter(hero_names == "Loki") %>% 
 # select_if(all_vars(.=="TRUE"))
```

## dplyr Practice
Let's do a bit more practice to make sure that we understand `select()`, `filter()`, and `mutate()`. Start by building a new data frame `msleep24` from the `msleep` data that: contains the `name` and `vore` variables along with a new column called `sleep_total_24` which is the amount of time a species sleeps expressed as a proportion of a 24-hour day. Remove any rows with NA's and restrict the `sleep_total_24` values to less than 0.3. Arrange the output in descending order.  

```r
#msleep24 <- msleep %>% 
 # mutate(sleep_total_24 = sleep_total/24) %>% 
 # select(name, vore, sleep_total_24) %>% 
 # filter(!is.na(vore)) %>%  #removing NAs from a variable 
 # filter(sleep_total_24 <= 0.3) %>% 
 # arrange(desc(sleep_total_24))
```

Histogram

```r
#hist()
```

## `group_by()`
The `summarize()` function is most useful when used in conjunction with `group_by()`. Although producing a summary of body weight for all of the mammals in the data set is helpful, what if we were interested in body weight by feeding ecology?

```r
#msleep %>%
#  group_by(vore) %>% #we are grouping by feeding ecology, a categorical variable
#  summarize(min_bodywt = min(bodywt),
#            max_bodywt = max(bodywt),
#            mean_bodywt = mean(bodywt),
#            total=n())
```

## Counts
Although these summary functions are super helpful, oftentimes we are mostly interested in counts. The [janitor package](https://garthtarr.github.io/meatR/janitor.html) does a lot with counts, but there are also functions that are part of dplyr that are useful.  

`count()` is an easy way of determining how many observations you have within a column. It acts like a combination of `group_by()` and `n()`.

```r
#penguins %>% 
#  count(island, sort = T) #sort=T sorts the column in descending order
```

You can also use `count()` across multiple variables.

```r
#penguins %>% 
#  count(island, species, sort = T) # sort=T will arrange in descending order
```

You can also use `count()` to find NAs in data 

```r
#penguins %>% 
#  count(sex, island)
```

## `across()`
What about using `filter()` and `select()` across multiple variables? There is a function in dplyr called `across()` which is designed to work across multiple variables.

By using `across()` we can reduce the clutter and make things cleaner. 

```r
#penguins %>%
#  summarize(across(c(species, island, sex), n_distinct))
```

This is very helpful for continuous variables.

```r
#penguins %>%
#  summarize(across(contains("mm"), mean, na.rm=T))
```

`group_by` also works.

```r
#penguins %>%
#  group_by(sex) %>% 
#  summarize(across(contains("mm"), mean, na.rm=T))
```

Here we summarize across all variables.

```r
#penguins %>%
#  summarise_all(mean, na.rm=T)
```

the !c(...) says across all variables except ...

```r
#penguins %>%
#  summarise(across(!c(species, island, sex, year), 
#                   mean, na.rm=T))
```

All variables that include "bill"...all of the other dplyr operators also work.

```r
#penguins %>%
#  summarise(across(starts_with("bill"), mean, na.rm=T))
```

## Lab 6 

removes NAs from a variable

```r
#filter(!is.na(date)) 
```

#### summary statistics 
sd() = standard deviation
min() = minimum
max() = maximum
sum() = add
n() = returns the length of a column
first() = returns first value in a columns
last() = reutrns last value in a column
n_distinct() = number of distinct values ina columns 

summarize() function is useful when combined with group_by()

group_by() must be categorical

`count()` is an easy way of determining how many observations you have within a column. It acts like a combination of `group_by()` and `n()`

```r
#gives the same data

#penguins %>% 
  #count(island, sort = T) #sort=T sorts the column in descending order

#penguins %>% 
  #group_by(island) %>% 
  #summarize(n=n())
```

## Lab 7

Dealing with NAs

is.na() = gives true/false for every data point
any_na() = true/false in general

Replacing values with NA (ie NA was given numerical value of -999)

In begining when uploading data into R...
  data %>%  na_if("-999")
  
counting amount of NAs in each variable
  summarize_all(~(sum(is.na(.))))
  
Replacing NAs with na_if() and mutate()
  ex. domesticated to NA
  msleep %>%  
    mutate(conservation_modified = na_if(conservation, "domesticated"))%>% 
    count(conservation_modified, sort = T) 
            #previously there were only 29 NA's
            
Naniar
  package build to manage NA's
  
naniar::miss_var_summary()

## Lab 8

here() 
read_csv(here("", "", ""))

`Tidy` data in the sense of the tidyverse follows three conventions:   
    (1) each variable has its own column  
    (2) each observation has its own row  
    (3) each value has its own cell  

wide format data = typically used for efficient data entry by scientists

pivot_longer() to shift data from wide to long format

Rules:  
+ `pivot_longer`(cols, names_to, values_to)
+ `cols` - Columns to pivot to longer format
+ `names_to` - Name of the new column; it will contain the column names of gathered columns as values
+ `values_to` - Name of the new column; it will contain the data stored in the values of gathered columns

example of pivot_longer()
  heartrate %>% 
  pivot_longer(-patient, #patient will not pivot/move
               names_to = "drug", #new column name 
               values_to = "heartrate") #values are moved to 
  
  Specify a range of columns that you want to pivot.
      billboard2 <- 
        billboard %>% 
        pivot_longer(wk1:wk76, # a range of columns
                      names_to = "week",
                      values_to = "rank",
                      values_drop_na = TRUE) #this will drop the NA's
  Specify columns that you want to stay fixed.     
      billboard3 <- 
        billboard %>% 
        pivot_longer(-c(artist, track, date.entered), #specific columns
                      names_to = "week",
                      values_to = "rank",
                      values_drop_na = TRUE)
                      
  Identify columns by a prefix, remove the prefix and all NA's.
      billboard %>% 
        pivot_longer(
        cols = starts_with("wk"),
        names_to = "week",
        names_prefix = "wk",
        values_to = "rank",
        values_drop_na = TRUE)
        
  More than one variable in a column name
  `names_sep` helps pull these apart, but we still have "exp" and "rep" to deal with.  
      qpcr_untidy %>% 
          pivot_longer(
            exp1_rep1:exp3_rep3,
            names_to= c("experiment", "replicate"),
            names_sep="_",
            values_to="mRNA_expression")
 
separate()           
   More than one value or observation in a row
        This is often caused by an entry error, but R will not be able to work with it                unless the values are separated. This doesn't use `pivot_longer()` but is a               common problem.    
        
        length_data %>% 
            transform(length = str_split(length, ";")) %>%
            unnest(length)  
         
   separate()` needs to know which column you want to split, the names of the new columns, and what to look for in terms of breaks in the data.  
   
          heartrate2 %>% 
              separate(patient, into= c("patient", "sex"), sep = "_")

`unite()` is the opposite of separate(). 
    Its syntax is straightforward. You only need to give a new column name and then list            the columns to combine with a separation character.
      
          heartrate3 %>% 
              unite(patient_sex, "patient", "sex", sep=" ")
    
    Look at Hw Lab 9 for separation and plotting     
        
pivot_wider() = goes from long data to wide data

Rules:  
+ `pivot_wider`(names_from, values_from)  
+ `names_from` - Values in the `names_from` column will become new column names  
+ `values_from` - Cell values will be taken from the `values_from` column  

When using `pivot_wider()` we use `names_from` to identify the variables (new column names) and `values_from` to identify the values associated with the new columns.

      tb_data %>% 
            pivot_wider(names_from = "key", 
                                  #the observations under key will become new columns
                        values_from = "value")
                        
  With multiple variables  
    edu_level %>% 
        pivot_wider(names_from = (education_level), 
                              #new column names come from the education_level column
                    values_from = c(mean_income, n)) 
                              #values come from two separate columns
## Lab 9

Data Types
+ `discrete` quantitative data that only contains integers
+ `continuous` quantitative data that can take any numerical value
+ `categorical` qualitative data that can take on a limited number of values

coord_flip() = switches the x and y axis to make things look neater if required

Plotting 

Boxplots
  Boxplots help us visualize a range of values. So, on the x-axis we typically have           something categorical and the y-axis is the range. In the case below, we are plotting     `log10.mass` by taxonomic class in the `homerange` data. `geom_boxplot()` is the geom     type for a standard box plot. The center line in each box represents the median, not      the mean.
  
        ggplot(dataset, aes(x= , y= )) +
          geom_boxplot()
  
Scatterplot
  Scatter plots are good at revealing relationships that are not readily visible in the         raw data. For now, we will not add regression lines or calculate any r^2^ values.
      Scatter plots allow for comparisons of two continuous variables.

        ggplot(dataset, aes(x= , y= )) +
          geom_point()
          
  In big data sets with lots of overlapping values, over-plotting can be an issue.              `geom_jitter()` is similar to `geom_point()` but it helps with over plotting by            adding some random noise to the data and separating some of the individual points.
  
         ggplot(dataset, aes(x= , y= )) +
          geom_jitter()
  
  To add a regression (best of fit) line, we just add another layer.
    "se" is standard error, T = True/ F= False
    
        ggplot(dataset, aes(x= , y= )) +
          geom_point() +
          geom_smooth(method = lm, se = T)
          

Bar Plots:

    geom_bar()
      The simplest type of bar plot counts the number of observations in a categorical              variable. Notice that we do not specify a y-axis because it is count by default.

          ggplot(dataset, aes(x= )) +
            geom_bar()
            
    geom_bar() with stat="identity"
      `stat="identity"` allows us to map a variable to the y-axis so that we aren't               restricted to counts.

      Example:
        homerange %>% 
            filter(family=="salmonidae") %>% 
            ggplot(aes(x=common.name, y=log10.mass))+
            geom_bar(stat="identity")

    geom_col()
      This allows us to specify an x-axis and a y-axis
        
          ggplot(dataset, aes(x= )) +
            geom_col()
            
  Barplots and multiple variables
      Use fill to build a stacked bar plot that shows the proportions of a given dataset        group
      
        ex.
            homerange %>% 
              ggplot(aes(x = taxon, fill = trophic.guild)) + geom_bar() +
              coord_flip() +
              labs(title = "Observations by Taxon in Homerange Data",
                  x = "Taxonomic Group",
                  fill = "Trophic Guild")
              
      We can also have counts of each trophic guild within taxonomic group shown                side-by-side by specifying ...
      
      position="dodge"
       
        ex. 
          homerange %>% 
            ggplot(aes(x = taxon, fill = trophic.guild)) + geom_bar(position = "dodge") +
            coord_flip() +
            labs(title = "Observations by Taxon in Homerange Data",
                x = "Taxonomic Group",
                fill = "Trophic Guild")
      
     Here is the same plot oriented vertically
          homerange %>% 
            ggplot(aes(x = taxon, fill = trophic.guild)) +
            geom_bar(position = "dodge") +
            theme(axis.text.x = element_text(angle = 60, hjust = 1)) +
            labs(title = "Observations by Taxon in Homerange Data",
                x = "Taxonomic Group",
                fill= "Trophic Guild")
                
     We can also scale all bars to a percentage (or proportion).
        homerange %>% 
          ggplot(aes(x = taxon, fill = trophic.guild))+
          geom_bar(position = position_fill())+ 
          scale_y_continuous(labels = scales::percent)+
          coord_flip()
     
## Lab 10 

  Remove/cancel scientific notation for the session 
    option 1:
       options(scipen == value)
            ex. options(scipen == 999)
    option 2:
       scale_y_log10()

Reorder x: `ggplot(aes(x=reorder(x-data, y-data), y=y-data))

####Aesthetics

Labels: To add custom labels, we use the `labs` command.
  labs()
 
    + labs(title = "",
        x="",
        y="")

Theme: We can improve the plot further by adjusting the size and face of the text.
  `theme()`
  
    +  theme(plot.title = element_text(size=rel(1.25), hjust=0.5))
    
    `rel()` option changes the relative size of the title to keep things consistent.   
           the rel() gives size of the title
    `hjust` allows control of title position.
          the hjust = 1 (all the way right) ; =0 (all the way to the left) ; =0.5 (in the                 center) 
  
Fill: is a common grouping option; notice that an appropriate key is displayed when you use one of these options.
  fill=
    
      ex.
        elephants %>% 
            ggplot(aes(x=sex, fill=sex))+
            geom_bar()
            
`size` adjusts the size of points relative to a continuous variable.
  size= 
    
      ex. 
        life_history %>% 
            ggplot(aes(x=gestation,y=log10(mass), size=mass))+
            geom_point(na.rm = T)
            
      Play with point size.
        +geom_point(size=2)
        
      Map shapes to another categorical variable.
        geom_point(aes(shape=thermoregulation, color=thermoregulation), size=1.75)

Using `group`
  In addition to `fill`, `group` is an aesthetic that accomplishes the same function but    does not add color.
  
      ex. 
          I use `group` to make individual box plots for each taxon.
              homerange %>% 
                  ggplot(aes(x = class, y = log10.mass, group = taxon)) +
                  geom_boxplot()
          I can also use `fill` to associate the different taxa with a color coded key.
              homerange %>% 
                  ggplot(aes(x = class, y = log10.mass, fill = taxon)) +
                  geom_boxplot()
                  
## Lab 11

Plotting:

Line Plots:
  Line plots are great when you need to show changes over time.
  geom_line()
  
      ggplot(aes(x= , y= , group= , color= ))+
        geom_line()+
        geom_point(shape = )
        
      ex. 
        deserts2 %>% 
          filter(species_id=="DM" | species_id=="DS") %>% 
          group_by(year, species_id) %>% 
          summarise(n=n(), .groups='keep') %>% 
          ggplot(aes(x=year, y=n, group=species_id, color=species_id))+
          geom_line()+
          geom_point(shape=5)+
          theme(axis.text.x = element_text(angle = 60, hjust = 1))+
          labs(title = "Number of samples for species DM & DS",
              x = "Year",
              fill = "n")
              
Histograms:
  Histograms are frequently used by biologists; they show the distribution of continuous      variables. As students, you almost certainly have seen histograms of grade               distributions. Without getting into the statistics, a histogram `bins` the data and      you specify the number of bins that encompass a range of observations. For               something like grades, this is easy because the number of bins corresponds to the        grades A-F. By default, R uses a formula to calculate the number of bins but some        adjustment is often required.
  
  geom_histogram()
  
      ex. 
      homerange %>% 
        ggplot(aes(x = log10.mass)) +
        geom_histogram(alpha = 0.4, color = "black", fill = "lightgreen", bins=40)+
        labs(title = "Distribution of Body Mass")
  
Colors:
Let's play with the colors. This shows all 657 of R's built-in colors. Notice that `color` and `fill` do different things!

      grDevices::colors()
          #lists all available colors
  [1] "white"               
  [2] "aliceblue"           
  [3] "antiquewhite"        
  [4] "antiquewhite1"       
  [5] "antiquewhite2"       
  [6] "antiquewhite3"       
  [7] "antiquewhite4"       
  [8] "aquamarine"          
  [9] "aquamarine1"         
 [10] "aquamarine2"         
 [11] "aquamarine3"         
 [12] "aquamarine4"         
 [13] "azure"               
 [14] "azure1"              
 [15] "azure2"              
 [16] "azure3"              
 [17] "azure4"              
 [18] "beige"               
 [19] "bisque"              
 [20] "bisque1"             
 [21] "bisque2"             
 [22] "bisque3"             
 [23] "bisque4"             
 [24] "black"               
 [25] "blanchedalmond"      
 [26] "blue"                
 [27] "blue1"               
 [28] "blue2"               
 [29] "blue3"               
 [30] "blue4"               
 [31] "blueviolet"          
 [32] "brown"               
 [33] "brown1"              
 [34] "brown2"              
 [35] "brown3"              
 [36] "brown4"              
 [37] "burlywood"           
 [38] "burlywood1"          
 [39] "burlywood2"          
 [40] "burlywood3"          
 [41] "burlywood4"          
 [42] "cadetblue"           
 [43] "cadetblue1"          
 [44] "cadetblue2"          
 [45] "cadetblue3"          
 [46] "cadetblue4"          
 [47] "chartreuse"          
 [48] "chartreuse1"         
 [49] "chartreuse2"         
 [50] "chartreuse3"         
 [51] "chartreuse4"         
 [52] "chocolate"           
 [53] "chocolate1"          
 [54] "chocolate2"          
 [55] "chocolate3"          
 [56] "chocolate4"          
 [57] "coral"               
 [58] "coral1"              
 [59] "coral2"              
 [60] "coral3"              
 [61] "coral4"              
 [62] "cornflowerblue"      
 [63] "cornsilk"            
 [64] "cornsilk1"           
 [65] "cornsilk2"           
 [66] "cornsilk3"           
 [67] "cornsilk4"           
 [68] "cyan"                
 [69] "cyan1"               
 [70] "cyan2"               
 [71] "cyan3"               
 [72] "cyan4"               
 [73] "darkblue"            
 [74] "darkcyan"            
 [75] "darkgoldenrod"       
 [76] "darkgoldenrod1"      
 [77] "darkgoldenrod2"      
 [78] "darkgoldenrod3"      
 [79] "darkgoldenrod4"      
 [80] "darkgray"            
 [81] "darkgreen"           
 [82] "darkgrey"            
 [83] "darkkhaki"           
 [84] "darkmagenta"         
 [85] "darkolivegreen"      
 [86] "darkolivegreen1"     
 [87] "darkolivegreen2"     
 [88] "darkolivegreen3"     
 [89] "darkolivegreen4"     
 [90] "darkorange"          
 [91] "darkorange1"         
 [92] "darkorange2"         
 [93] "darkorange3"         
 [94] "darkorange4"         
 [95] "darkorchid"          
 [96] "darkorchid1"         
 [97] "darkorchid2"         
 [98] "darkorchid3"         
 [99] "darkorchid4"         
[100] "darkred"             
[101] "darksalmon"          
[102] "darkseagreen"        
[103] "darkseagreen1"       
[104] "darkseagreen2"       
[105] "darkseagreen3"       
[106] "darkseagreen4"       
[107] "darkslateblue"       
[108] "darkslategray"       
[109] "darkslategray1"      
[110] "darkslategray2"      
[111] "darkslategray3"      
[112] "darkslategray4"      
[113] "darkslategrey"       
[114] "darkturquoise"       
[115] "darkviolet"          
[116] "deeppink"            
[117] "deeppink1"           
[118] "deeppink2"           
[119] "deeppink3"           
[120] "deeppink4"           
[121] "deepskyblue"         
[122] "deepskyblue1"        
[123] "deepskyblue2"        
[124] "deepskyblue3"        
[125] "deepskyblue4"        
[126] "dimgray"             
[127] "dimgrey"             
[128] "dodgerblue"          
[129] "dodgerblue1"         
[130] "dodgerblue2"         
[131] "dodgerblue3"         
[132] "dodgerblue4"         
[133] "firebrick"           
[134] "firebrick1"          
[135] "firebrick2"          
[136] "firebrick3"          
[137] "firebrick4"          
[138] "floralwhite"         
[139] "forestgreen"         
[140] "gainsboro"           
[141] "ghostwhite"          
[142] "gold"                
[143] "gold1"               
[144] "gold2"               
[145] "gold3"               
[146] "gold4"               
[147] "goldenrod"           
[148] "goldenrod1"          
[149] "goldenrod2"          
[150] "goldenrod3"          
[151] "goldenrod4"          
[152] "gray"                
[153] "gray0"               
[154] "gray1"               
[155] "gray2"               
[156] "gray3"               
[157] "gray4"               
[158] "gray5"               
[159] "gray6"               
[160] "gray7"              
[161] "gray8"               
[162] "gray9"               
[163] "gray10"              
[164] "gray11"              
[165] "gray12"              
[166] "gray13"              
[167] "gray14"              
[168] "gray15"              
[169] "gray16"              
[170] "gray17"              
[171] "gray18"              
[172] "gray19"              
[173] "gray20"              
[174] "gray21"              
[175] "gray22"              
[176] "gray23"              
[177] "gray24"              
[178] "gray25"              
[179] "gray26"              
[180] "gray27"              
[181] "gray28"              
[182] "gray29"              
[183] "gray30"              
[184] "gray31"              
[185] "gray32"              
[186] "gray33"              
[187] "gray34"              
[188] "gray35"              
[189] "gray36"              
[190] "gray37"              
[191] "gray38"              
[192] "gray39"              
[193] "gray40"              
[194] "gray41"              
[195] "gray42"              
[196] "gray43"              
[197] "gray44"              
[198] "gray45"              
[199] "gray46"              
[200] "gray47"              
[201] "gray48"              
[202] "gray49"              
[203] "gray50"              
[204] "gray51"              
[205] "gray52"              
[206] "gray53"              
[207] "gray54"              
[208] "gray55"              
[209] "gray56"              
[210] "gray57"              
[211] "gray58"              
[212] "gray59"              
[213] "gray60"              
[214] "gray61"              
[215] "gray62"              
[216] "gray63"              
[217] "gray64"              
[218] "gray65"              
[219] "gray66"              
[220] "gray67"              
[221] "gray68"              
[222] "gray69"              
[223] "gray70"              
[224] "gray71"              
[225] "gray72"              
[226] "gray73"              
[227] "gray74"              
[228] "gray75"              
[229] "gray76"              
[230] "gray77"              
[231] "gray78"              
[232] "gray79"              
[233] "gray80"              
[234] "gray81"              
[235] "gray82"              
[236] "gray83"              
[237] "gray84"              
[238] "gray85"              
[239] "gray86"              
[240] "gray87"              
[241] "gray88"              
[242] "gray89"              
[243] "gray90"              
[244] "gray91"              
[245] "gray92"              
[246] "gray93"              
[247] "gray94"              
[248] "gray95"              
[249] "gray96"              
[250] "gray97"              
[251] "gray98"              
[252] "gray99"              
[253] "gray100"             
[254] "green"               
[255] "green1"              
[256] "green2"              
[257] "green3"              
[258] "green4"              
[259] "greenyellow"         
[260] "grey"                
[261] "grey0"               
[262] "grey1"               
[263] "grey2"               
[264] "grey3"               
[265] "grey4"               
[266] "grey5"               
[267] "grey6"               
[268] "grey7"               
[269] "grey8"               
[270] "grey9"               
[271] "grey10"              
[272] "grey11"              
[273] "grey12"              
[274] "grey13"              
[275] "grey14"              
[276] "grey15"              
[277] "grey16"              
[278] "grey17"              
[279] "grey18"              
[280] "grey19"              
[281] "grey20"              
[282] "grey21"              
[283] "grey22"              
[284] "grey23"              
[285] "grey24"              
[286] "grey25"              
[287] "grey26"              
[288] "grey27"              
[289] "grey28"              
[290] "grey29"              
[291] "grey30"              
[292] "grey31"              
[293] "grey32"              
[294] "grey33"              
[295] "grey34"              
[296] "grey35"              
[297] "grey36"              
[298] "grey37"              
[299] "grey38"              
[300] "grey39"              
[301] "grey40"              
[302] "grey41"              
[303] "grey42"              
[304] "grey43"              
[305] "grey44"              
[306] "grey45"              
[307] "grey46"              
[308] "grey47"              
[309] "grey48"              
[310] "grey49"              
[311] "grey50"              
[312] "grey51"              
[313] "grey52"              
[314] "grey53"              
[315] "grey54"              
[316] "grey55"              
[317] "grey56"              
[318] "grey57"              
[319] "grey58"              
[320] "grey59"              
[321] "grey60"              
[322] "grey61"              
[323] "grey62"              
[324] "grey63"              
[325] "grey64"              
[326] "grey65"              
[327] "grey66"              
[328] "grey67"              
[329] "grey68"              
[330] "grey69"              
[331] "grey70"              
[332] "grey71"              
[333] "grey72"              
[334] "grey73"              
[335] "grey74"              
[336] "grey75"              
[337] "grey76"              
[338] "grey77"              
[339] "grey78"              
[340] "grey79"              
[341] "grey80"              
[342] "grey81"              
[343] "grey82"              
[344] "grey83"              
[345] "grey84"              
[346] "grey85"              
[347] "grey86"              
[348] "grey87"              
[349] "grey88"              
[350] "grey89"              
[351] "grey90"              
[352] "grey91"              
[353] "grey92"              
[354] "grey93"              
[355] "grey94"              
[356] "grey95"              
[357] "grey96"              
[358] "grey97"              
[359] "grey98"              
[360] "grey99"              
[361] "grey100"             
[362] "honeydew"            
[363] "honeydew1"           
[364] "honeydew2"           
[365] "honeydew3"           
[366] "honeydew4"           
[367] "hotpink"             
[368] "hotpink1"            
[369] "hotpink2"            
[370] "hotpink3"            
[371] "hotpink4"            
[372] "indianred"           
[373] "indianred1"          
[374] "indianred2"          
[375] "indianred3"          
[376] "indianred4"          
[377] "ivory"               
[378] "ivory1"              
[379] "ivory2"              
[380] "ivory3"              
[381] "ivory4"              
[382] "khaki"               
[383] "khaki1"              
[384] "khaki2"              
[385] "khaki3"              
[386] "khaki4"              
[387] "lavender"            
[388] "lavenderblush"       
[389] "lavenderblush1"      
[390] "lavenderblush2"      
[391] "lavenderblush3"      
[392] "lavenderblush4"      
[393] "lawngreen"           
[394] "lemonchiffon"        
[395] "lemonchiffon1"       
[396] "lemonchiffon2"       
[397] "lemonchiffon3"       
[398] "lemonchiffon4"       
[399] "lightblue"           
[400] "lightblue1"          
[401] "lightblue2"          
[402] "lightblue3"          
[403] "lightblue4"          
[404] "lightcoral"          
[405] "lightcyan"           
[406] "lightcyan1"          
[407] "lightcyan2"          
[408] "lightcyan3"          
[409] "lightcyan4"          
[410] "lightgoldenrod"      
[411] "lightgoldenrod1"     
[412] "lightgoldenrod2"     
[413] "lightgoldenrod3"     
[414] "lightgoldenrod4"     
[415] "lightgoldenrodyellow"
[416] "lightgray"           
[417] "lightgreen"          
[418] "lightgrey"           
[419] "lightpink"           
[420] "lightpink1"          
[421] "lightpink2"          
[422] "lightpink3"          
[423] "lightpink4"          
[424] "lightsalmon"         
[425] "lightsalmon1"        
[426] "lightsalmon2"        
[427] "lightsalmon3"        
[428] "lightsalmon4"        
[429] "lightseagreen"       
[430] "lightskyblue"        
[431] "lightskyblue1"       
[432] "lightskyblue2"       
[433] "lightskyblue3"       
[434] "lightskyblue4"       
[435] "lightslateblue"      
[436] "lightslategray"      
[437] "lightslategrey"      
[438] "lightsteelblue"      
[439] "lightsteelblue1"     
[440] "lightsteelblue2"     
[441] "lightsteelblue3"     
[442] "lightsteelblue4"     
[443] "lightyellow"         
[444] "lightyellow1"        
[445] "lightyellow2"        
[446] "lightyellow3"        
[447] "lightyellow4"        
[448] "limegreen"           
[449] "linen"               
[450] "magenta"             
[451] "magenta1"            
[452] "magenta2"            
[453] "magenta3"            
[454] "magenta4"            
[455] "maroon"              
[456] "maroon1"             
[457] "maroon2"             
[458] "maroon3"             
[459] "maroon4"             
[460] "mediumaquamarine"    
[461] "mediumblue"          
[462] "mediumorchid"        
[463] "mediumorchid1"       
[464] "mediumorchid2"       
[465] "mediumorchid3"       
[466] "mediumorchid4"       
[467] "mediumpurple"        
[468] "mediumpurple1"       
[469] "mediumpurple2"       
[470] "mediumpurple3"       
[471] "mediumpurple4"       
[472] "mediumseagreen"      
[473] "mediumslateblue"     
[474] "mediumspringgreen"   
[475] "mediumturquoise"     
[476] "mediumvioletred"     
[477] "midnightblue"        
[478] "mintcream"           
[479] "mistyrose"           
[480] "mistyrose1"          
[481] "mistyrose2"          
[482] "mistyrose3"          
[483] "mistyrose4"          
[484] "moccasin"            
[485] "navajowhite"         
[486] "navajowhite1"        
[487] "navajowhite2"        
[488] "navajowhite3"        
[489] "navajowhite4"        
[490] "navy"                
[491] "navyblue"            
[492] "oldlace"             
[493] "olivedrab"           
[494] "olivedrab1"          
[495] "olivedrab2"          
[496] "olivedrab3"          
[497] "olivedrab4"          
[498] "orange"              
[499] "orange1"             
[500] "orange2"             
[501] "orange3"             
[502] "orange4"             
[503] "orangered"           
[504] "orangered1"          
[505] "orangered2"          
[506] "orangered3"          
[507] "orangered4"          
[508] "orchid"              
[509] "orchid1"             
[510] "orchid2"             
[511] "orchid3"             
[512] "orchid4"             
[513] "palegoldenrod"       
[514] "palegreen"           
[515] "palegreen1"          
[516] "palegreen2"          
[517] "palegreen3"          
[518] "palegreen4"          
[519] "paleturquoise"       
[520] "paleturquoise1"      
[521] "paleturquoise2"      
[522] "paleturquoise3"      
[523] "paleturquoise4"      
[524] "palevioletred"       
[525] "palevioletred1"      
[526] "palevioletred2"      
[527] "palevioletred3"      
[528] "palevioletred4"      
[529] "papayawhip"          
[530] "peachpuff"           
[531] "peachpuff1"          
[532] "peachpuff2"          
[533] "peachpuff3"          
[534] "peachpuff4"          
[535] "peru"                
[536] "pink"                
[537] "pink1"               
[538] "pink2"               
[539] "pink3"               
[540] "pink4"               
[541] "plum"                
[542] "plum1"               
[543] "plum2"               
[544] "plum3"               
[545] "plum4"               
[546] "powderblue"          
[547] "purple"              
[548] "purple1"             
[549] "purple2"             
[550] "purple3"             
[551] "purple4"             
[552] "red"                 
[553] "red1"                
[554] "red2"                
[555] "red3"                
[556] "red4"                
[557] "rosybrown"           
[558] "rosybrown1"          
[559] "rosybrown2"          
[560] "rosybrown3"          
[561] "rosybrown4"          
[562] "royalblue"           
[563] "royalblue1"          
[564] "royalblue2"          
[565] "royalblue3"          
[566] "royalblue4"          
[567] "saddlebrown"         
[568] "salmon"              
[569] "salmon1"             
[570] "salmon2"             
[571] "salmon3"             
[572] "salmon4"             
[573] "sandybrown"          
[574] "seagreen"            
[575] "seagreen1"           
[576] "seagreen2"           
[577] "seagreen3"           
[578] "seagreen4"           
[579] "seashell"            
[580] "seashell1"           
[581] "seashell2"           
[582] "seashell3"           
[583] "seashell4"           
[584] "sienna"              
[585] "sienna1"             
[586] "sienna2"             
[587] "sienna3"             
[588] "sienna4"             
[589] "skyblue"             
[590] "skyblue1"            
[591] "skyblue2"            
[592] "skyblue3"            
[593] "skyblue4"            
[594] "slateblue"           
[595] "slateblue1"          
[596] "slateblue2"          
[597] "slateblue3"          
[598] "slateblue4"          
[599] "slategray"           
[600] "slategray1"          
[601] "slategray2"          
[602] "slategray3"          
[603] "slategray4"          
[604] "slategrey"           
[605] "snow"                
[606] "snow1"               
[607] "snow2"               
[608] "snow3"               
[609] "snow4"               
[610] "springgreen"         
[611] "springgreen1"        
[612] "springgreen2"        
[613] "springgreen3"        
[614] "springgreen4"        
[615] "steelblue"           
[616] "steelblue1"          
[617] "steelblue2"          
[618] "steelblue3"          
[619] "steelblue4"          
[620] "tan"                 
[621] "tan1"                
[622] "tan2"                
[623] "tan3"                
[624] "tan4"                
[625] "thistle"             
[626] "thistle1"            
[627] "thistle2"            
[628] "thistle3"            
[629] "thistle4"            
[630] "tomato"              
[631] "tomato1"             
[632] "tomato2"             
[633] "tomato3"             
[634] "tomato4"             
[635] "turquoise"           
[636] "turquoise1"          
[637] "turquoise2"          
[638] "turquoise3"          
[639] "turquoise4"          
[640] "violet"              
[641] "violetred"           
[642] "violetred1"          
[643] "violetred2"          
[644] "violetred3"          
[645] "violetred4"          
[646] "wheat"               
[647] "wheat1"              
[648] "wheat2"              
[649] "wheat3"              
[650] "wheat4"              
[651] "whitesmoke"          
[652] "yellow"              
[653] "yellow1"             
[654] "yellow2"             
[655] "yellow3"             
[656] "yellow4"             
[657] "yellowgreen" 


Density Plots:
  Density plots are similar to histograms but they use a smoothing function to make the       distribution more even and clean looking. They do not use bins.
  geom_density()
  
      ex. 
        ggplot(aes(x = log10.mass)) +
        geom_density(fill="deepskyblue4", alpha  =0.4, color = "black")+
        labs(title = "Distribution of Body Mass")

  I like to see both the histogram and the density curve so I often plot them together.        Note that I assign the density plot a different color.
        homerange %>% 
          ggplot(aes(x=log10.mass)) +
          geom_histogram(aes(y = ..density..), fill = "deepskyblue4", alpha = 0.4, color                 = "black")+
          geom_density(color = "red")+
          labs(title = "Distribution of Body Mass")

Create Categories with mutate and case_when()
  `case_when()` is a very handy function from `dplyr` which allows us to calculate a new       variable from other variables. We use `case_when()` within `mutate()` to do              this.`case_when()` allows us to specify multiple conditions.
          
          ex. 
            homerange <- homerange %>% 
              mutate(mass_category = case_when(log10.mass <= 1.75 ~ "small",
                                              log10.mass > 1.75 & log10.mass <= 2.75 ~                                                             "medium",
                                              log10.mass > 2.75 ~ "large"))

    library(gtools)
      quantiles the values to make it easier to code case_when()
          quartiles <- quantcut(homerange$log10.hra)
          table(quartiles)

Legends:
  legend.position = ""
  
     ex.
        p+theme_linedraw()+
          theme(legend.position = "bottom",
          axis.text.x = element_text(angle = 60, hjust=1))+
          labs(title = "Observations by Taxon in Homerange Data",
              x = NULL,
              y= "n",
              fill = "Trophic Guild")
              
ggthemes
  Here is a list of the `ggthemes`
 [1] "theme_base"           
 [2] "theme_calc"           
 [3] "theme_clean"          
 [4] "theme_economist"      
 [5] "theme_economist_white"
 [6] "theme_excel"          
 [7] "theme_excel_new"      
 [8] "theme_few"            
 [9] "theme_fivethirtyeight"
[10] "theme_foundation"     
[11] "theme_gdocs"          
[12] "theme_hc"             
[13] "theme_igray"          
[14] "theme_map"            
[15] "theme_pander"         
[16] "theme_par"            
[17] "theme_solarized"      
[18] "theme_solarized_2"    
[19] "theme_solid"          
[20] "theme_stata"          
[21] "theme_tufte"          
[22] "theme_wsj"            

RColorBrewer
  The default colors used by ggplot are often uninspiring. They don't make plots pop         out in presentations or publications, and you may want to use a customized palette to     make things visually consistent.  

  The thing to notice is that there are three different palettes: 
      1) sequential, 2) diverging, and 3) qualitative. 
        Within each of these there are several selections. You can bring up the colors by         using `display.brewer.pal()`. Specify the number of colors that you want and the         palette name.
      Be Aware of color blindness
  
      ex. to see the color pallete 
          display.brewer.pal(4,"GnBu")

guidelines:
+`scale_colour_brewer()` is for points  
+`scale_fill_brewer()` is for fills  

      ex. 
          + scale_fill_brewer(palette = "YlGnBu")

Manually Setting Colors:
    You can also use `paleteer` to build a custom palette for consistency. To access the        `paleteer` collection, I add it to a new object.
    
    colors <- paletteer::palettes_d_names
    
    Now we can display the palettes. Assign the palette to `my_palette` and then build         this base R bar plot. There are a lot of options; `paleteer` is a collection of          popular palettes.
    
          my_palette <- paletteer_d("ggprism::flames")
          
          ex.
            barplot(rep(1,14), axes=FALSE, col=second_palette)
          ex.  
            Now we just identify `my_palette` as part of `scale_fill_manual()`
            +scale_fill_manual(values=my_palette)
            
Adjusting the x and y limits
  To adjust limits, we can use the `xlim` and `ylim` commands. When you do this, any data     outside the specified ranges are not plotted.
  +xlim()
  +ylim()
  
        ex.
          homerange %>% 
            ggplot(aes(x = log10.mass, y = log10.hra, color = locomotion)) +
            geom_point() +
            xlim(0, 4) +
            ylim(1, 6)
  
Faceting
  It allows us to make multi-panel plots for easy comparison.
  
  ex. 
      The problem is that the plot becomes very busy. It is hard to interpret with each        migratory strategy mapped. We could build separate plots for each migratory              strategy, but this also makes it harder to compare. Instead, we can use faceting to       make a multi-panel plot.  
      
      `facet_wrap()` 
          makes a ribbon of panels, but you can control how you want them arranged.
          
          ecosphere %>% 
            ggplot(aes(x=diet, y=log10_mass, fill=migratory_strategy))+ 
            geom_boxplot(alpha=0.4) + 
            facet_wrap(~migratory_strategy, ncol=4)
  
      `facet_grid()` 
          allows control over the faceted variable; it can be arranged in rows or                      columns. 
          Will also allow the comparison of two categorical variables, just remember a~b              where a is rows and b is columns.
          rows~columns
          
          ecosphere %>% 
            ggplot(aes(x=diet, y=log10_mass, fill=migratory_strategy))+ 
            geom_boxplot(alpha=0.4)+ 
            facet_grid(migratory_strategy~.)
          
          ecosphere %>% 
            ggplot(aes(x=log10_mass))+
            geom_density()+
            facet_grid(diet~habitat, scales = "free_y")
          
          
          
          
          
          
          
          
          
          





