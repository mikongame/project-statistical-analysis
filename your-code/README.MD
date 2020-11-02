<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100" align="right"/>


#   Project Ironhack Data Bootcamp: Statistical analysis on Happiness-Culture interaction

MIGUEL GARCÍA MELGAR

*Data Part Time Barcelona Dic 2019*


## Content
- [Project Description](#project)
- [Datasets](#Datasets)
- [Workflow](#workflow)
- [Results](#results)
- [Links](#links)

<a name="project"></a>

## Project Description

### Overview

In order to practice statistical analysis using the iterative data analysis process, I've chosen two datasets related to my backround in psychology.


### Technical Requirements

The technical requirements for this project have been:

* Trying to apply everything I have learned so far about data analysis such as data cleaning, data manipulation, data visualization, and various statistical analysis methods.

* Applying the iterative data analysis process -- setting expectations, collecting information, and reacting to data / revising expectations.

* Conducting an analysis in Jupyter Notebook using Pandas, Numpy, Scipy, Matplotlib, Seaborn, Plotly, and other Python libraries I've have learned, as necessary.

### Deliverables

The following deliverables were pushed to our Github repo for this chapter.

* * **A Jupyter Notebook (statistical-analysis.ipynb)** containing our Python codes, outputs, and data visualizations. Making sure to include explanations for each step in Markdown cells or Python comments.
* **A folder** named "data" containing the I used.
* **This README.md** containing a detailed explanation of the followed approach visializing and analysing the information.

<a name="Datasets"></a>

## Datasets
 
One is [Hofstede's six-dimensions model](https://data.world/adamhelsinger/geerthofstedeculturaldimension) has information on the results of several countries for various years and, similarly [World Happiness Report](https://www.kaggle.com/unsdsn/world-happiness); I will focus on 2015 data.
  
<a name="workflow"></a>

## Introduction

**Geert Hofstede's cultural dimensions theory** proposes a method of analyzing cultures based on a handful of continuums.

`Power distance index (PDI):` The power distance index is defined as “the extent to which the less powerful members of organizations and institutions (like the family) accept and expect that power is distributed unequally.”

`Individualism vs. collectivism (IDV):` This index explores the “degree to which people in a society are integrated into groups.”

`Uncertainty avoidance index (UAI):` The uncertainty avoidance index is defined as “a society's tolerance for ambiguity,” in which people embrace or avert an event of something unexpected, unknown, or away from the status quo.

`Masculinity vs. femininity (MAS):` In this dimension, masculinity is defined as “a preference in society for achievement, heroism, assertiveness and material rewards for success.”

`Long-term orientation vs. short-term orientation (LTO):` This dimension associates the connection of the past with the current and future actions/challenges.

`Indulgence vs. restraint (IND):` This dimension is essentially a measure of happiness; whether or not simple joys are fulfilled.

More contextual information about this model can be found in here: https://scholarworks.gvsu.edu/cgi/viewcontent.cgi?referer=https://en.wikipedia.org/&httpsredir=1&article=1014&context=orpc


**The World Happiness Report 2015** is a landmark survey of the state of global happiness which ranks 158 countries by their happiness levels based on six factors.


`Country:` Name of the country.

`Region:` Region the country belongs to.

`Happiness Rank:` Rank of the country based on the Happiness Score.

`Happiness Score:` A metric measured in 2015 by asking the sampled people the question: "How would you rate your happiness on a scale of 0 to 10 where 10 is the happiest."

`Economy:` real GDP per capita

`Family:` social support

`Health:` healthy life expectancy

`Freedom:` freedom to make life choices

`Trust:` perceptions of corruption

`Generosity:` perceptions of generosity

`Dystopia:` each country is compared against a hypothetical nation that represents the lowest national averages for each key variable and is, along with residual error, used as a regression benchmark.

## Workflow

###  Introduction
####  Objectives
####  Imports

###  1. EDA
####  Hofstede's six-dimensions model (2015)
#####  Context
#####  Read dataset and check head
#####  Check tail
#####  Check shape
#####  Check dtypes and columns
#####  Check nulls
##### Check duplicates
#####  See some descriptive statistics
####  World Happiness Report 2015
#####  Context
#####  Read dataset and check head
#####  Check tail
#####  Check shape
#####  Check dtypes and columns
#####  Check nulls
#####  Check duplicates
#####  See some descriptive statistics

###  2. Describe relationships between variables
####  Hofstede's six-dimensions model (2015)
####  World Happiness Report 2015

###  3. Features should be investigated in depth combining datasets
####  Merge of datasets

###  4. Data cleaning & manipulation
####  Feature reduction.
####  Remove columns with high proportion of missing values.
####  Remove records with missing values.
####  Adjust skewed data distribution.
#####  Normality testing
#####  Standardize measures and check correlations

###  5. Hypothesis testing

###  6. Bonus: Regression analysis and PCA
####  Regression model
####  PCA
#####  How much components are needed to explain >= 0.95 of variance?


## Conclusions

##### Hofstede's six-dimensions model (2015) correlations

**Most correlations seem to be negligible but there's still some significant ones:**
`Power distance` highly negatively correlates with `Individualism vs Collectivism`, and has low but significant correlations with `Uncertainty Avoidance`, positively, and negativley with  `Indulgence vs Restraint`. The latter also correlates moderately negatively with `Long Term versus Short Term Orientation`.

So the **more hierarchy** is accepted in a country, the **more colectivistic** the culture seems being also quite probable citizens' tendency to **avoid risk** and **surpress emotions and pleasure**.
In those countries where **pleasure seek is indulged**, usually there's also a common tendencty to think in the **short-term future**.

##### World Happiness Report 2015

**As the 6 indexes the test uses were chosen from factorizing Happiness Score, we will just focus on correletions between them.**
They all positively correlate except `Generosity` with a negligible negative correlation with `Economy`.
Moreover, the top 3 correlations, being correlations over 0.5, are the top 3 Happiness Score factors: `Economy`, `Family` and `Health`.


##### Correlations of the merged and standardized dataset (Happiness Score + 6 cultural dimensions)
**Most correlations seem to be negligible but there's still some significant ones:**
`Happiness Score` highly positively correlates with `Indulgence vs Restraint`(0.73), and moderately correlates with `Power distance` and `Individualism vs Collectivism`, respectively in a negative (-0.56) and in a positive(0.44) way.

So that **higher levels of happiness** are registered in coutries where **pleasure seek is indulged** and can be described as **egalitarian** and **individualistic**.

##### Hypothesis testing
As the hypothesis were sided and we have standardized data a one sided T-Test with a 95% confidence interval was performed. 

H0: Individualistic societies are happier (>) than colectivistic ones.
H1: Individualistic societies aren't happier (<=) than colectivistic ones.

With a stat=0.445 and p=0.001; **H0 has been accepted**.


##### According to the regression analysis using a multivariate OLS model:

The most important variables in the model are, in this order, "ind", "lto", "pdi" and "idv"; having an R-squared of 0.759, so that a lot of its variability depends on the variables included in the model.

It is kinda curious as its correlations coefficient were:

- `Indulgence vs Restraint` = 0.73, which is coherent with the regression coefficient of 0.77
- `Power - distance` = -0.56, differing in size from the regression coefficient, -0.21
- `Individualism vs Collectivism` = 0.44, which as PDI has a regression coef "halving" its correlation one being  0.163
- `Long Term vs Short Term Orientation` = -0.11, which is pretty interesting as its regression coefficient doubles and turns positive, 0.23

##### After doing a PCA

**87,9% of variance can be explained with 4 of the 6 possible components**, they're probably the top 4 obtained from the regression model but we can't be sure. 

We have also seen that with a 5th component 95% of the variability would be explained, but remember there were just 6, so it is not really a good idea to focus on few components we you are already using just a few.

## Future Improvements

* We have to find out why correlation coeficients differ but one of the main issues could be that the samble was not that big and it had to be reduced a lot. 

* There are currently 247 countries but one of our datasets had results from 111 countries and the other only considered 158 and they didn't always coincide plus there were some NaN values. We ended up with a dataset of just 57 countries' results. I shiould try to look for more complete and up-to-date data.

* It would be interesting to analyze how other indexes that conform Happiness Score correlate with the 6 cultural dimensions.

## Links
[Repository](https://github.com/mikongame/NLP-to-predict-Myers-Briggs-Personality-Type)  
[Slides](https://view.genial.ly/5e8203367fd6910db48a4a43/presentation-statistical-analysis-on-happiness-culture-interaction)
