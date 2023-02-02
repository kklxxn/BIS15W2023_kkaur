---
title: "Lab 6 Homework"
author: "Khushleen Kaur"
date: "2023-02-01"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the libraries

```r
library(tidyverse)
library(janitor)
library(skimr)
```

For this assignment we are going to work with a large data set from the [United Nations Food and Agriculture Organization](http://www.fao.org/about/en/) on world fisheries. These data are pretty wild, so we need to do some cleaning. First, load the data.  

Load the data `FAO_1950to2012_111914.csv` as a new object titled `fisheries`.

```r
fisheries <- readr::read_csv(file = "data/FAO_1950to2012_111914.csv")
```

```
## Rows: 17692 Columns: 71
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (69): Country, Common name, ISSCAAP taxonomic group, ASFIS species#, ASF...
## dbl  (2): ISSCAAP group#, FAO major fishing area
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

1. Do an exploratory analysis of the data (your choice). What are the names of the variables, what are the dimensions, are there any NA's, what are the classes of the variables?  

```r
summary(fisheries)
```

```
##    Country          Common name        ISSCAAP group#  ISSCAAP taxonomic group
##  Length:17692       Length:17692       Min.   :11.00   Length:17692           
##  Class :character   Class :character   1st Qu.:33.00   Class :character       
##  Mode  :character   Mode  :character   Median :36.00   Mode  :character       
##                                        Mean   :37.38                          
##                                        3rd Qu.:38.00                          
##                                        Max.   :77.00                          
##  ASFIS species#     ASFIS species name FAO major fishing area
##  Length:17692       Length:17692       Min.   :18.00         
##  Class :character   Class :character   1st Qu.:31.00         
##  Mode  :character   Mode  :character   Median :37.00         
##                                        Mean   :45.34         
##                                        3rd Qu.:57.00         
##                                        Max.   :88.00         
##    Measure              1950               1951               1952          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1953               1954               1955               1956          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1957               1958               1959               1960          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1961               1962               1963               1964          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1965               1966               1967               1968          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1969               1970               1971               1972          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1973               1974               1975               1976          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1977               1978               1979               1980          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1981               1982               1983               1984          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1985               1986               1987               1988          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1989               1990               1991               1992          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1993               1994               1995               1996          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      1997               1998               1999               2000          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      2001               2002               2003               2004          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      2005               2006               2007               2008          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##      2009               2010               2011               2012          
##  Length:17692       Length:17692       Length:17692       Length:17692      
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
## 
```

```r
anyNA(fisheries)
```

```
## [1] TRUE
```
2. Use `janitor` to rename the columns and make them easier to use. As part of this cleaning step, change `country`, `isscaap_group_number`, `asfis_species_number`, and `fao_major_fishing_area` to data class factor. 

```r
fisheries <- clean_names(fisheries)
fisheries
```

```
## # A tibble: 17,692 × 71
##    country common_…¹ issca…² issca…³ asfis…⁴ asfis…⁵ fao_m…⁶ measure x1950 x1951
##    <chr>   <chr>       <dbl> <chr>   <chr>   <chr>     <dbl> <chr>   <chr> <chr>
##  1 Albania Angelsha…      38 Sharks… 10903X… Squati…      37 Quanti… <NA>  <NA> 
##  2 Albania Atlantic…      36 Tunas,… 175010… Sarda …      37 Quanti… <NA>  <NA> 
##  3 Albania Barracud…      37 Miscel… 177100… Sphyra…      37 Quanti… <NA>  <NA> 
##  4 Albania Blue and…      45 Shrimp… 228020… Ariste…      37 Quanti… <NA>  <NA> 
##  5 Albania Blue whi…      32 Cods, … 148040… Microm…      37 Quanti… <NA>  <NA> 
##  6 Albania Bluefish       37 Miscel… 170202… Pomato…      37 Quanti… <NA>  <NA> 
##  7 Albania Bogue          33 Miscel… 170392… Boops …      37 Quanti… <NA>  <NA> 
##  8 Albania Caramote…      45 Shrimp… 228010… Penaeu…      37 Quanti… <NA>  <NA> 
##  9 Albania Catshark…      38 Sharks… 108010… Scylio…      37 Quanti… <NA>  <NA> 
## 10 Albania Common c…      57 Squids… 321020… Sepia …      37 Quanti… <NA>  <NA> 
## # … with 17,682 more rows, 61 more variables: x1952 <chr>, x1953 <chr>,
## #   x1954 <chr>, x1955 <chr>, x1956 <chr>, x1957 <chr>, x1958 <chr>,
## #   x1959 <chr>, x1960 <chr>, x1961 <chr>, x1962 <chr>, x1963 <chr>,
## #   x1964 <chr>, x1965 <chr>, x1966 <chr>, x1967 <chr>, x1968 <chr>,
## #   x1969 <chr>, x1970 <chr>, x1971 <chr>, x1972 <chr>, x1973 <chr>,
## #   x1974 <chr>, x1975 <chr>, x1976 <chr>, x1977 <chr>, x1978 <chr>,
## #   x1979 <chr>, x1980 <chr>, x1981 <chr>, x1982 <chr>, x1983 <chr>, …
```


```r
fisheries$country <- as.factor(fisheries$country)
fisheries$isscaap_group_number <- as.factor(fisheries$isscaap_group_number)
fisheries$asfis_species_number <- as.factor(fisheries$asfis_species_number)
fisheries$fao_major_fishing_area <- as.factor(fisheries$fao_major_fishing_area)
```

We need to deal with the years because they are being treated as characters and start with an X. We also have the problem that the column names that are years actually represent data. We haven't discussed tidy data yet, so here is some help. You should run this ugly chunk to transform the data for the rest of the homework. It will only work if you have used janitor to rename the variables in question 2!

```r
fisheries_tidy <- fisheries %>% 
  pivot_longer(-c(country,common_name,isscaap_group_number,isscaap_taxonomic_group,asfis_species_number,asfis_species_name,fao_major_fishing_area,measure),
               names_to = "year",
               values_to = "catch",
               values_drop_na = TRUE) %>% 
  mutate(year= as.numeric(str_replace(year, 'x', ''))) %>% 
  mutate(catch= str_replace(catch, c(' F'), replacement = '')) %>% 
  mutate(catch= str_replace(catch, c('...'), replacement = '')) %>% 
  mutate(catch= str_replace(catch, c('-'), replacement = '')) %>% 
  mutate(catch= str_replace(catch, c('0 0'), replacement = ''))

fisheries_tidy$catch <- as.numeric(fisheries_tidy$catch)
```

3. How many countries are represented in the data? Provide a count and list their names.

```r
# list of country names
levels(fisheries_tidy$country)
```

```
##   [1] "Saint Barth\xe9lemy"       "R\xe9union"               
##   [3] "C\xf4te d'Ivoire"          "Cura\xe7ao"               
##   [5] "Albania"                   "Algeria"                  
##   [7] "American Samoa"            "Angola"                   
##   [9] "Anguilla"                  "Antigua and Barbuda"      
##  [11] "Argentina"                 "Aruba"                    
##  [13] "Australia"                 "Bahamas"                  
##  [15] "Bahrain"                   "Bangladesh"               
##  [17] "Barbados"                  "Belgium"                  
##  [19] "Belize"                    "Benin"                    
##  [21] "Bermuda"                   "Bonaire/S.Eustatius/Saba" 
##  [23] "Bosnia and Herzegovina"    "Brazil"                   
##  [25] "British Indian Ocean Ter"  "British Virgin Islands"   
##  [27] "Brunei Darussalam"         "Bulgaria"                 
##  [29] "Cabo Verde"                "Cambodia"                 
##  [31] "Cameroon"                  "Canada"                   
##  [33] "Cayman Islands"            "Channel Islands"          
##  [35] "Chile"                     "China"                    
##  [37] "China, Hong Kong SAR"      "China, Macao SAR"         
##  [39] "Colombia"                  "Comoros"                  
##  [41] "Congo, Dem. Rep. of the"   "Congo, Republic of"       
##  [43] "Cook Islands"              "Costa Rica"               
##  [45] "Croatia"                   "Cuba"                     
##  [47] "Cyprus"                    "Denmark"                  
##  [49] "Djibouti"                  "Dominica"                 
##  [51] "Dominican Republic"        "Ecuador"                  
##  [53] "Egypt"                     "El Salvador"              
##  [55] "Equatorial Guinea"         "Eritrea"                  
##  [57] "Estonia"                   "Ethiopia"                 
##  [59] "Falkland Is.(Malvinas)"    "Faroe Islands"            
##  [61] "Fiji, Republic of"         "Finland"                  
##  [63] "France"                    "French Guiana"            
##  [65] "French Polynesia"          "French Southern Terr"     
##  [67] "Gabon"                     "Gambia"                   
##  [69] "Georgia"                   "Germany"                  
##  [71] "Ghana"                     "Gibraltar"                
##  [73] "Greece"                    "Greenland"                
##  [75] "Grenada"                   "Guadeloupe"               
##  [77] "Guam"                      "Guatemala"                
##  [79] "Guinea"                    "GuineaBissau"             
##  [81] "Guyana"                    "Haiti"                    
##  [83] "Honduras"                  "Iceland"                  
##  [85] "India"                     "Indonesia"                
##  [87] "Iran (Islamic Rep. of)"    "Iraq"                     
##  [89] "Ireland"                   "Isle of Man"              
##  [91] "Israel"                    "Italy"                    
##  [93] "Jamaica"                   "Japan"                    
##  [95] "Jordan"                    "Kenya"                    
##  [97] "Kiribati"                  "Korea, Dem. People's Rep" 
##  [99] "Korea, Republic of"        "Kuwait"                   
## [101] "Latvia"                    "Lebanon"                  
## [103] "Liberia"                   "Libya"                    
## [105] "Lithuania"                 "Madagascar"               
## [107] "Malaysia"                  "Maldives"                 
## [109] "Malta"                     "Marshall Islands"         
## [111] "Martinique"                "Mauritania"               
## [113] "Mauritius"                 "Mayotte"                  
## [115] "Mexico"                    "Micronesia, Fed.States of"
## [117] "Monaco"                    "Montenegro"               
## [119] "Montserrat"                "Morocco"                  
## [121] "Mozambique"                "Myanmar"                  
## [123] "Namibia"                   "Nauru"                    
## [125] "Netherlands"               "Netherlands Antilles"     
## [127] "New Caledonia"             "New Zealand"              
## [129] "Nicaragua"                 "Nigeria"                  
## [131] "Niue"                      "Norfolk Island"           
## [133] "Northern Mariana Is."      "Norway"                   
## [135] "Oman"                      "Other nei"                
## [137] "Pakistan"                  "Palau"                    
## [139] "Palestine, Occupied Tr."   "Panama"                   
## [141] "Papua New Guinea"          "Peru"                     
## [143] "Philippines"               "Pitcairn Islands"         
## [145] "Poland"                    "Portugal"                 
## [147] "Puerto Rico"               "Qatar"                    
## [149] "Romania"                   "Russian Federation"       
## [151] "Saint Helena"              "Saint Kitts and Nevis"    
## [153] "Saint Lucia"               "Saint Vincent/Grenadines" 
## [155] "SaintMartin"               "Samoa"                    
## [157] "Sao Tome and Principe"     "Saudi Arabia"             
## [159] "Senegal"                   "Serbia and Montenegro"    
## [161] "Seychelles"                "Sierra Leone"             
## [163] "Singapore"                 "Sint Maarten"             
## [165] "Slovenia"                  "Solomon Islands"          
## [167] "Somalia"                   "South Africa"             
## [169] "Spain"                     "Sri Lanka"                
## [171] "St. Pierre and Miquelon"   "Sudan"                    
## [173] "Sudan (former)"            "Suriname"                 
## [175] "Svalbard and Jan Mayen"    "Sweden"                   
## [177] "Syrian Arab Republic"      "Taiwan Province of China" 
## [179] "Tanzania, United Rep. of"  "Thailand"                 
## [181] "TimorLeste"                "Togo"                     
## [183] "Tokelau"                   "Tonga"                    
## [185] "Trinidad and Tobago"       "Tunisia"                  
## [187] "Turkey"                    "Turks and Caicos Is."     
## [189] "Tuvalu"                    "Ukraine"                  
## [191] "Un. Sov. Soc. Rep."        "United Arab Emirates"     
## [193] "United Kingdom"            "United States of America" 
## [195] "Uruguay"                   "US Virgin Islands"        
## [197] "Vanuatu"                   "Venezuela, Boliv Rep of"  
## [199] "Viet Nam"                  "Wallis and Futuna Is."    
## [201] "Western Sahara"            "Yemen"                    
## [203] "Yugoslavia SFR"            "Zanzibar"
```

```r
#number of countries
n_distinct(fisheries_tidy$country)
```

```
## [1] 203
```

4. Refocus the data only to include country, isscaap_taxonomic_group, asfis_species_name, asfis_species_number, year, catch.

```r
fisheries_selected <- fisheries_tidy %>% 
  select("country", "isscaap_taxonomic_group", "asfis_species_name", "asfis_species_number", "year", "catch")
fisheries_selected
```

```
## # A tibble: 376,771 × 6
##    country isscaap_taxonomic_group asfis_species_name asfis_specie…¹  year catch
##    <fct>   <chr>                   <chr>              <fct>          <dbl> <dbl>
##  1 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      1995    NA
##  2 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      1996    53
##  3 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      1997    20
##  4 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      1998    31
##  5 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      1999    30
##  6 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      2000    30
##  7 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      2001    16
##  8 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      2002    79
##  9 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      2003     1
## 10 Albania Sharks, rays, chimaeras Squatinidae        10903XXXXX      2004     4
## # … with 376,761 more rows, and abbreviated variable name ¹​asfis_species_number
```

5. Based on the asfis_species_number, how many distinct fish species were caught as part of these data?

```r
n_distinct(fisheries_selected$asfis_species_number)
```

```
## [1] 1551
```
6. Which country had the largest overall catch in the year 2000?

- China had the largest overall catch 

```r
fisheries_selected %>% 
  filter(year == 2000) %>% 
  select("country", "catch") %>% 
  arrange(desc(catch))
```

```
## # A tibble: 8,793 × 2
##    country                  catch
##    <fct>                    <dbl>
##  1 China                     9068
##  2 Peru                      5717
##  3 Russian Federation        5065
##  4 Viet Nam                  4945
##  5 Chile                     4299
##  6 China                     3288
##  7 China                     2782
##  8 United States of America  2438
##  9 China                     1234
## 10 Philippines                999
## # … with 8,783 more rows
```
7. Which country caught the most sardines (_Sardina pilchardus_) between the years 1990-2000?

- Morocco

```r
fisheries_selected %>% 
  filter(asfis_species_name == "Sardina pilchardus") %>% 
  filter(between(year, 1990, 2000)) %>% 
  group_by(country) %>% 
  summarise(sum = sum(catch, na.rm = T)) %>% 
  arrange(desc(sum))
```

```
## # A tibble: 37 × 2
##    country                 sum
##    <fct>                 <dbl>
##  1 Morocco                7470
##  2 Spain                  3507
##  3 Russian Federation     1639
##  4 Ukraine                1030
##  5 France                  966
##  6 Portugal                818
##  7 Greece                  528
##  8 Italy                   507
##  9 Serbia and Montenegro   478
## 10 Denmark                 477
## # … with 27 more rows
```

8. Which five countries caught the most cephalopods between 2008-2012?

- India, China, Spain, Algeria, France

```r
fisheries_selected %>% 
  filter(asfis_species_name == "Cephalopoda") %>% 
  filter(between(year, 2008, 2012)) %>% 
  group_by(country) %>% 
  summarise(sum=sum(catch, na.rm = T)) %>% 
  arrange(desc(sum))
```

```
## # A tibble: 16 × 2
##    country                    sum
##    <fct>                    <dbl>
##  1 India                      570
##  2 China                      257
##  3 Spain                      198
##  4 Algeria                    162
##  5 France                     101
##  6 Mauritania                  90
##  7 TimorLeste                  76
##  8 Italy                       66
##  9 Mozambique                  16
## 10 Cambodia                    15
## 11 Taiwan Province of China    13
## 12 Madagascar                  11
## 13 Croatia                      7
## 14 Israel                       0
## 15 Somalia                      0
## 16 Viet Nam                     0
```

9. Which species had the highest catch total between 2008-2012? (hint: Osteichthyes is not a species)

- Theragra chalcogramma

```r
fisheries_selected %>% 
  filter(between(year, 2008, 2012)) %>% 
  group_by(asfis_species_name) %>% 
  summarise(sum=sum(catch, na.rm = T)) %>% 
  arrange(desc(sum))
```

```
## # A tibble: 1,472 × 2
##    asfis_species_name       sum
##    <chr>                  <dbl>
##  1 Osteichthyes          107808
##  2 Theragra chalcogramma  41075
##  3 Engraulis ringens      35523
##  4 Katsuwonus pelamis     32153
##  5 Trichiurus lepturus    30400
##  6 Clupea harengus        28527
##  7 Thunnus albacares      20119
##  8 Scomber japonicus      14723
##  9 Gadus morhua           13253
## 10 Thunnus alalunga       12019
## # … with 1,462 more rows
```

10. Use the data to do at least one analysis of your choice.

- Which year were the most total fish caught, no considering individual species
- 2007, where 268130 fish were caught in total


```r
fisheries_tidy %>% 
  select("year", "catch") %>% 
  group_by(year) %>% 
  summarise(total_fish = sum(catch, na.rm = T)) %>% 
  arrange(desc(total_fish))
```

```
## # A tibble: 63 × 2
##     year total_fish
##    <dbl>      <dbl>
##  1  2007     268130
##  2  2006     257669
##  3  2001     257320
##  4  2002     255807
##  5  2012     255406
##  6  2008     255013
##  7  2004     254115
##  8  2005     251877
##  9  2009     251181
## 10  2010     244839
## # … with 53 more rows
```


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
