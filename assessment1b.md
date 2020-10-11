HDAT9700: Assignment 1B - Chapters 4 & 5
================

### Submission instructions

This is an R Markdown document—an example of *literate programming*, an
approach which allows users to interweave text, statistical output and
the code that produces that output.

To complete your assignment:

  - Edit this file directly, interweaving text and R code as appropriate
    to answer the questions below. Remember to `Knit` the file to make
    sure everything is running smoothly. Detailed information on R
    Markdown is available
    [here](https://rmarkdown.rstudio.com/lesson-1.html), and there is a
    useful cheatsheet
    [here](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf).

  - Use git to `commit` changes you make in this repo locally.

  - `Push` the repo, together with this edited file and the
    corresponding `.md` file to GitHub Classroom.  
    You can `commit` and `push` as often as neccessary—your assessment
    will be graded on the most recent version of your repo at the
    assessment due date.

Good luck\!

-----

### Overview

For this assessment you will use a subset of data from a study of car
crashes after introduction of graduated driver licensing in Queensland
([Senserrick *et al*. Associations between graduated driver licensing
and road trauma reductions in a later licensing age jurisdiction:
Queensland, Australia. *PLoS ONE* 2018 Sep
25;13(9):e0204107](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0204107)).
This introduced increased restrictions on new (novice) drivers,
including introducing a 100-hour supervised driving requirement, as well
as restrictions on passenger carriage at night, use of high-powered
vehicles, and phone use. The purpose of this study was to quantify
changes in crashes involving novice drivers. The intervention was
implemented in July 2007. The data are monthly, from January 2002 to
December 2009.

The `crash.csv` file contains the following variables:

  - **month** - Month and year
  - **novice\_crash** - Number of crashes involving novice drivers
  - **total\_crash** - Total number of crashes

You may need to have the following packages installed: `astsa`,
`forecast`, and `zoo`.

The data are contained in your assignment repo in the file `crash.csv`
and can be read as follows:

``` r
library(readr)
crash <- read_csv('crash.csv')
```

    ## Parsed with column specification:
    ## cols(
    ##   month = col_character(),
    ##   novice_crash = col_double(),
    ##   total_crash = col_double()
    ## )

-----

### Assessment questions

1)  Create a plot(s) of the number of crashes, both overall
    (*total\_crash*) and for novice drivers (*novice\_crash*), as if you
    were preparing it for inclusion in a report or publication. The date
    of the intervention should be clearly indicated. (15%)

2)  Describe the characteristics of both time series in terms of the
    trend, seasonality, and outliers. Use plots and summary statistics
    to support your statements. (10%)

3)  Create the necessary vectors to fit the regression models listed
    below. Here, `time` is the time since start of the study, `grad` is
    an indicator for the graduated licensing intervention (before=0,
    after=1), `time.after` is the time since the intervention, `month`
    is a monthly dummy variable, and `grad.lag1` and `time.after.lag1`
    are `grad` and `time.after` delayed/lagged by one month. State which
    model you believe best describes the association between the
    intervention, and the number of crashes involving novice drivers
    over time. Provide evidence to justify your answer. (25%)
    
      - **Model 1** - novice\_crash \~ time + grad + time.after + month
      - **Model 2** - novice\_crash \~ time + grad + time.after
      - **Model 3** - novice\_crash \~ time + grad.lag1 +
        time.after.lag1 + month
      - **Model 4** - novice\_crash \~ time + grad.lag1 +
        time.after.lag1

4)  Using `auto.arima()`, identify the most appropriate ARIMA model
    orders for modelling the impact of the intervention on novice
    crashes, assuming an immediate (not delayed) impact. Think carefully
    about which parameters to pre-specify. State whether you would
    prefer the segmented regression model chosen in question (3), or
    this ARIMA model, and briefly justify your decision. (20%)

5)  Using the most appropriate model from question (3) or (4), describe
    the impact of the intervention on novice crashes. What is your
    conclusion about the effect of the intervention? Provide effect
    estimates and relevant statistics to support your answer. (15%)

6)  Including a negative control series is an interrupted time series
    analysis is one way of improving causal inference from interrupted
    time series analysis. Give an example of a negative control series
    and justify your selection, and explain how a negative control
    series can help with inference. (15%)

-----

### Solution

-----

### Student declaration

***Instructions: Indicate that you understand and agree with the
following three statements by typing an x in the square brackets below,
e.g. \[x\].***

I declare that this assessment item is my own work, except where
acknowledged, and has not been submitted for academic credit elsewhere
or previously, or produced independently of this course (e.g. for a
third party such as your place of employment) and acknowledge that the
assessor of this item may, for the purpose of assessing this item: (i)
Reproduce this assessment item and provide a copy to another member of
the University; and/or (ii) Communicate a copy of this assessment item
to a plagiarism checking service (which may then retain a copy of the
assessment item on its database for the purpose of future plagiarism
checking).

  - [ ] I understand and agree

I certify that I have read and understood the University Rules in
respect of Student Academic Misconduct.

  - [ ] I understand and agree

I have a backup copy of the assessment.

  - [ ] I understand and agree
