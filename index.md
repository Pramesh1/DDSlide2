---
title       : Emigrating - Better off ?
subtitle    : DDP Slidify Assignment
author      : Pramesh Rogbeer
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
### 1. The Application 

**APPLICATION** :     [DDPFinal](https://pramesh.shinyapps.io/DDPFinal) located at https://pramesh.shinyapps.io/DDPFinal/

**OBJECTIVE**: Provide you with a few predictions on what to expect if you plan to emigrate.

**DATA** : Census data (and report) from 2013 was downloaded from the [UNDP site](http://hdr.undp.org/en/data) 



- The UNDP collects data from all over the world to calculate an annual  ***Human Development Index*** (HDI) for each country. This index provides a measure of people's wellbeing in different parts of the world. The HDI is made up of various independent indices. 

- The [DDPFinal](https://pramesh.shinyapps.io/DDPFinal) application uses a selection of these indices , but can be effortlessly modified to use a wider range .

- The [DDPFinal](https://pramesh.shinyapps.io/DDPFinal) application "predicts" how, compared to now, your quality of life could improve/degrade if you emigrated elsewhere

- the results are provided in tabular and graphical forms


Have fun !!



--- .class #id 

### 2. The Logic

### INPUT:  
 At the user interface: (1) your `current location` (2) where you want to `emigrate` , and (3) your `gender`. (Gender has an impact too - you can try it)

### OUTPUT: 
The output gives you the % change ( +ve or -ve) to expect in 12 different indicators. (e.g. life expectancy, taxation. etc.).The Computation is quite straighforward  :

`Result = (Value for Current Location - Value for Destination ) ` 

### RESULTS:
The results are presented in:

- a table (all values are in %)
- a histogram with values `>0` (improvements) and `<0` (loss in quality)




--- .class #id 

### 3. The coding
Some key points of the code : the full code is on my [github](https://github.com/Pramesh1/DDSlide2)  
(I set `echo=FALSE` to hide the code - it is too long)

For this presentation, I preset the input variables as follows:

```r
countryNow="Mauritius"
countryFuture="Germany"
gender="Male"
```


Output Result:
(Please take a look at the app on shiny.io to get an explanation of the result)


```
##     hdi.rank hdi.gii     hdi hdi.r    le    gni taxes   cpi     hom   sat
## 63      90.5   -87.7    18.4  -0.5 -11.4 -135.2  -2.8 -25.7     2.6  -1.2
## 631  BETTER!   Worse BETTER! Worse Worse  Worse Worse Worse BETTER! Worse
##      free   trust
## 63     -7      15
## 631 Worse BETTER!
```


--- .class #id 

### 4. CHALLENGES:

The `csv` data was loaded into a variable in the `server.R` file. But is was impossible to `dynamically` pass a list (countries listing) to the input part of the `ui.R` file. This problem could not be solved despite intensive search on the web.
I finally ended up building this list inside the `ui.R` file itself. 

Then there was the famous `UTF-8` encoding problem ... The app was not launching on the shiny server even though it was working perfectly on my laptop. After some search , I found out that I had to save the files with `UTF-8` encoding. Once this done, everything came back to normal.


I enjoyed this project quite a lot.

The application can be further improved. For example , a color scheme can be used for the histogram, e.g. GREEN for `>0` and RED for `<0` . 

