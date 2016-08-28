---
title       : Fantasy Football Rankings and Tiers
subtitle    : version 0.01
author      : hcam
job         : Rn00b
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github:
    user: hcam
    repo: slidifyFF16
    
---

## Fantasy Football Rankings and Tiers

Welcome to the 2016 Fantasy Football Season. 

Data is provided from borischen.co and fantasypros.com.


--- .class #id 

## Purpose

In order to help with your draft this season.  We pulled the rankings and tiers from borischen.co and presented it in two tabs ("Top 200" and "By Position").  Feel free to use this to dominate your draft, and set your team up for sucess this season.  

---

## Prepping data


```r
require(dplyr)
dataurl <- "https://s3-us-west-1.amazonaws.com/fftiers/out/current/weekly-ALL.csv"
ffdata <- read.csv(dataurl, stringsAsFactors = FALSE)
ffdata$Pos <- gsub('[0-9]+', '', ffdata$Position) #creates new column for Position
print(head(ffdata))
```

```
##   Rank       Player.Name Tier Position Team Bye.Week Best.Rank Worst.Rank
## 1    1     Antonio Brown    1      WR1  PIT        8         1          5
## 2    2 Odell Beckham Jr.    1      WR2  NYG        8         1          9
## 3    3       Julio Jones    1      WR3  ATL       11         1         10
## 4    4       Todd Gurley    1      RB1   LA        8         1         12
## 5    5     David Johnson    1      RB2  ARI        9         1         36
## 6    6   Adrian Peterson    2      RB3  MIN        6         1         25
##   Avg.Rank   Std.Dev Pos
## 1   1.3250 0.7870038  WR
## 2   3.0375 1.5119834  WR
## 3   3.3625 1.3345762  WR
## 4   4.9250 2.8096930  RB
## 5   6.1625 4.6702349  RB
## 6   7.8875 3.9749017  RB
```

---

## Using dplyr package to filter data.


```r
head(filter(ffdata, Pos == "WR"))
```

```
##   Rank       Player.Name Tier Position Team Bye.Week Best.Rank Worst.Rank
## 1    1     Antonio Brown    1      WR1  PIT        8         1          5
## 2    2 Odell Beckham Jr.    1      WR2  NYG        8         1          9
## 3    3       Julio Jones    1      WR3  ATL       11         1         10
## 4    7        A.J. Green    2      WR4  CIN        9         4         18
## 5    8   DeAndre Hopkins    2      WR5  HOU        9         3         19
## 6   12        Dez Bryant    2      WR6  DAL        7         4         35
##   Avg.Rank   Std.Dev Pos
## 1   1.3250 0.7870038  WR
## 2   3.0375 1.5119834  WR
## 3   3.3625 1.3345762  WR
## 4   8.4500 2.8324018  WR
## 5   8.9375 2.8781233  WR
## 6  12.2875 6.0315706  WR
```
# Good luck to all in your drafts this season! More updates to come!



