# Predicting 3 Day Eventing Scores

## Introduction

### What is 3 Day Eventing?
3-day eventing is a modern equestrian competition based on cavalry trials.  It is often considered the triathlon of equestrian sports as there are 3 different phases.  Each phase is meant to show the horse and rider's skills in the arena and over varied terrain.  Penalty points are accumulated over each phase so the horse and rider combination with the lowest score wins.

The first event, dressage, is based on the horse’s training.  It judges the horse and rider’s ability to perform a pattern of movements in an arena.  These movements originated on the battlefield as combat moves.  At the end of dressage, each horse and rider are given a penalty point score based off the percentage of points gained out of total possible points.  The percentage is subtracted from 100 to get the penalty score.

For example, let's say Jane and her horse score 98 out of 150 points.  That means she got 65.3%.  100 - 65.3 = 34.7.  So Jane's initial penalty score is 34.7

After dressage, horse and rider compete in cross country, where they complete a course of obstacles over varied terrain.  There is a time limit, and penalty points are added if the time limit is exceeded.  Additionally, if the horse refuses an obstacle and requires a second or third attempt, 20 penalty points are added to their score.  After 4 refusals, the horse and rider are eliminated. 

In our previous example, Jane and her horse scored 34.7 in dressage.  Let's say they had 1 refusal on cross country.  They add 20 penalty points to their score for a total of 54.7 going into the final phase.

Finally, the last phase of eventing is called show jumping, which tests that the horse and rider are fit enough to complete a course of fences made of light removable poles in an arena after a grueling day of cross-country riding.  The same principles of refusals and time penalties apply to show jumping, but there are also penalties for knocking down rails (4 penalties for each rail). 

Jane and her horse have a total of 54.7 penalties from dressage and cross country.  They knock down 2 rails, adding 8 penalty points to their score.  Jane and her horse finish the competition on 62.7 penalties.

At the end of the weekend, the horse and rider with the lowest penalty point score win. 

### Division Descriptions

Because there are so many competitors in 3 day eventing, competitions are split into different divisions depending on qualifying status.

| Division   | Classification |
|------------|----------------|
| Horse (H)  |The horse cannot have completed an event above the next highest level|
| Rider (R)  |Competitors who have not completed an event above the next highest level in the last five years|
| Amateur (A)|Competitors do not accept enumeration for riding or training horses
|Master (M)  |Competitors over age 40|
|Junior (J)  |Competitors under age 18|
|Youth (Y)   |Competitors under age 14|


### Question

In some cases, a competitor can qualify for more than one division.  For example, if a rider has not competed above a certain level, is an Amateur, and is riding a horse that has not competed at a higher level, they would qualify for both horse, rider, and amateur divisions.

If a rider has the choice between different divisions, it is up to them to decide which division to enter.  As a competitor who qualifies for multiple divisions, I wanted to see if there was a significant difference between different divisions.  I also wanted to see if there was a higher liklihood for competitors to be eliminated in different divisions.

It's important that scores remain consistent from year to year, ensuring that the tests are the same difficulty.  I will see if there is a difference in the final scores between different years of competition.


## The Data

Data were collected from http://livescore.useventing.com/ where the past years' scores from the American Eventing Championships are held.  There are 6 divisions represented over 3 years (2016-2018) of competition.  The way the website is structured, results from different years and divisions were in different tables.  The scores were inserted into an Excel spreadsheet.   Rider, Horse, and Owner names were removed as they were irrelevant to data analysis.  Scores of disqualified competitors were extracted and placed in a separate data table.  Additionally, the year and division were added as columns to create one large table containing all information.  This table was then imported into R.

The decision to split data into completed and incompleted was deliberate.  Many different options were considered, including adding a numerical value for the different types of disqualification and even removing the disqualified scores entirely.  In the end, it made the most sense to analyze the two data sets independently so that their data would not interfere with one another.

## Exploratory Data Analysis

[See Exploratory Data Analysis in full detail here](notebooks/SchoegglJacquieMSDS692ExploratoryDataAnalysis.ipynb)

[Exploratory Data Analysis for Incompleted Scores](notebooks/SchoegglJacquieMSDS692ExploratoryIncompleted.ipynb)

## Machine Learning | Linear Regression

### ANOVA and Post Hoc Testing
ANOVA methods were used to determine if there was a difference between final scores and divisions.

(spoiler alert!  There is a difference in final score between certain divisions)

Tukey HSD was used for post hoc testing to determine which divisions had significant differences.

[See Full Details on Machine Learning Here](notebooks/SchoegglJacquieMSDS692MachineLearning.ipynb)

### Predicting Final Place Given a Division and Dressage Score
Finally, we want to be able to predict the final place of a competitor given their division and initial dressage score.  

the `predict` command was used to predict the final score of a competitor given an intial dressage score and a division.


