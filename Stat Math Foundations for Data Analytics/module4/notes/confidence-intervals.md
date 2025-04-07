# Confidence intervals

Suppose we have a large population. For example the population could be all the people in the United States. Now suppose we are interested in a population parameter, say the height of a person. It would involve to many resources to accurately guage the mean height of all the people in the United States. So what we can do is take a random sample which is to say we take a subset of the larger popluation and then measure the height of this group of people. We can then infer from our sample what the population parameter is. How good our inference is depends on a few things like how the sample was taken and how large the sample is. What we can do to make our inference better is to take many random samples, all independent of each other and compare the menas of the heights of these random samples.

Lets take an example. We’ll take a large dataset as our population and one variable as the population parameter. We will pretend that we don’t know what the mean of the population parameter is. Our data set will be YRBSS. It stands for Youth Risk Behavior Surveillance System. It is a questionaire which monitors six types of health-risk behaviors that contribute to the leading causes of death and disability amoung youth and adults. It has about 173 thousand rows. In this data set there is a variable, which we will call $y$ that has to do with the number of days a person exercises throughout the week for at least 60 minutes at a time. It’s a number from 1 to 8. 1 stands for zero days spent exercising, all the way up to 8 which stands for 7 days. To get the data we enter the following into R:

``` r
> install.packages("devtools")
> devtools::install_github("hadley/yrbss")
> library('yrbss')
```

The data is in a variable called `survey` and the variable is called `q80` (question number 80). Most of the participants did not fill in this entry so there are a lot of NA (not applicable) entries. We can get rid of them with the `complete.cases command`:

``` r
  complete.cases(survey$qn80)$
```

Let’s say the mean of $y$ is some value $\mu$. Since $y$ is suppose to be a population then we’ll pretend we cannot calculate what $\mu$ actually is (though we actually could in this example because we have the data).

Let’s say we take 100 samples each of size $n$, each called $S_1$, $S_2$, …, $S_{100}$. Each of these samples has a mean which we will call $\bar{y}_1$, $\bar{y}_2$, …, $\bar{y}_{100}$. (The bar denotes we are thinking about *samples*. We want to know what the distribution of of these means $\bar{y}_1$, …, $\bar{y}_{100}$, collectively refered to as the variable $\bar{y}$, looks like. This is called a `sampling distribution`.

The central limit theorem of statistics tells us that as the number of samples goes up then the distribution will look more and more like a normal distribution.

Since $\bar{y}$ is a random variable we can ask about its distribution (the overall spread of the variable’s values), its mean, and its variance (how far, on average, are the points spread from the center).
