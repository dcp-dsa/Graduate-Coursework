# Module 2 Exercies

## Concept problems

### Summarizing Distributions

#### Topics

* Summarizing Distributions (ch 3 of ItS book)
  * What is central tendency
  * Mean and median
  * More measures of central tendency
  * Measures of variability
    * variance, standard deviation
  * shapes of distributions

#### Exercises

**note:** these concept problems are based on problems from
"[Introduction to Statistic](http://onlinestatbook.com/2/index.html)"

* Make up a dataset of 12 numbers with a positive skew. Use a
  statistical program to compute the skew. Is the mean larger than th
  median as it usually is for distributions with a positive skew? What
  is the value for skew?

* Repeat the above problem only this time make the dataset have a
  negative skew.

* Make up three datasets with 5 numbers each that have:
  * the same mean but different standard deviations.
  * the same mean but different medians.
  * Find the mean and median for the `iris.Sepal.Width` and
  `iris.Sepal.Width`.
  * the same median but different means.

* A sample of 30 distance scores measured in yeards has a mean of 10, a
  variance of 9, and a standard deviation of 3
  * You want to convert all your distances from yards to feet, so you
    multiply each score in the sample by 3. What are the new mean,
    variance, and standard deviation?
  * You then decide that you only want to look at the distance past a
    certain point. Thus, after multiplying the original scores by 3, you
    decide to subtract 4 feet from each of the scores. Now what are the
    new mean, variance, and standard deviation.

* You record the time in seconds it took for 8 participants to solve a
  puzzle. These times appear below. However, when the data was entered
  into the statistical program, the score that was supposed to be 22.1
  was 21.2. You had calculated the following measures of central
  tendency: the mean, the median, and the mean trimmed 25%. Which of
  these measures of central tendency will change when you correct the
  recording error?

  Time (in seconds): 15.2, 18.8, 19.3, 19.7, 20.2, 21.8, 22.1, 29.4

* For the test scores in the question above, which measures of
  variability (range, standard deviation, variance) would be changed if
  the 22.1 data point had been erroneously recorded as 21.2.

* You know the minimum, the maximum, and the 25th, 50th, and 75th
  percentiles of a distribution. Which of the following measures of
  central tendency or variability can you determine?

  mean, median, mode, trimean, geometric mean, range, interquartile
  range, variance, standard deviation

* For the numbers 1, 3, 4, 6, 12: Find the value v for which \sum(X-v)^2
  is minimized. Find the value v for which \sum(\abs{x-v}) is minimized.

### Describing bivariate data

#### Topics

* Describing bivariate data (ch 4 of ItS book)
  * Intro to bivariate data
  * Pearson's correlation
    * Possible values
    * Computing Pearson's r value
  * Variance sum laws

#### Exercises

* Make up a data set with 10 numbers that has a positive correlation.

* Make up a data set with 10 numbers that has a negative correlation.

* For a certain class, the relationship between the amount of time spent
  studying and the test grade earned was examined. It was determined that as
  the amount of time they studied increased, so did their grades. Is this a
  positive or negative association?

* True/False: The correlation in real life between height and weight is r=1.

* True/False: Two variables with a correlation of 0.3 have a stronger linear
  relationship than two variables with a correlation of -0.7.

* True/False: It is possible for variables to have r=0 but still have a strong
  association.

* “True/False: Two variables with a correlation of 0.3 have a stronger linear
  relationship than two variables with a correlation of -0.7.”

* “True/False: After polling a certain group of people, researchers found a 0.5
  correlation between the number of car accidents per year and the driver’s
  age. This means that older people get in more accidents.”

* What is the correlation between the Control-In and Control-Out scores?

### Relative Frequencies 

* (sec 9.2 pg 199) `summary()` on `iris` data set.

### Tabulating Factors and Creating Contingency Tables

From section 9.3 of R Cookbook starting on pg 200
* Contingency tables `(table(iris$Species, iris$Sepal.Length)`
* Graph a box plot of `iris$sepal.width`

### Calculuating quantiles (and quartiles)

From sections 9.6 and 9.7 of R Cookbook starting on pg 201

* `quantile(vec, .05)` with the `census` and `auto` datasets
* `quantile(vec, c(.05,.95))` with the `census` and `auto` datasets
* `quantile(vec)` with the `census` and `auto` datasets
* `boxplot(iris)` with the `iris` data
* `boxplot(iris$Sepal.width)` with the `iris` data (makes single
  boxplot)
* `boxplot(Sepal.Width~Species, data = irix)` (makes multiple boxplots)

### Inverting quartile

From sections 9.7 of R Cookbook starting on pg 202

* `mean(iris$Sepal.width < 2)`
