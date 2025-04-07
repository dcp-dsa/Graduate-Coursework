# Module 6: Regression & ANOVA testing

-   What the relationship between two variables (linear, curved?)

-   Can we predict the future relationship of variables given known data?

-   How accurate are our predictions?

# Ordinary Least Squares Regression

What is ordinary least squares regression? Take the points $(X_1,Y_1),
\ldots, (X_n,Y_n)$. Let $Y = (Y_1,\ldots, Y_n)$ and $X = (X_1,\ldots,
X_n)$. A linear regression model is a function $f(X) = \widehat{Y} =
\alpha + X\beta$. It is a linear line which best estimates the points given. Here $\widehat{Y} = (\widehat{Y}_1,\ldots,\widehat{Y}_n)$ is a vector of real numbers. We use the hat on $\widehat{Y}$ to signify that this is a calculated line not something that is observed. This equation means $\widehat{Y}_i = \alpha + X_i\beta$. For each $i$, $\widehat{Y}_i$ is the projection of $Y_i$ on to the line $\widehat{Y}$ (see the picture below). $\beta = (\beta_1,\ldots,\beta_n)$ is a vector of real numbers. The $\beta_i$ are called . $\alpha$ is a real number and is called the $y$-intercept. The $X_i$ are called the , inputs, or independent variables. The $Y_i$ is called the or . For each $i$ we define $\varepsilon_i = \widehat{Y}_i - Y_i$. The $\varepsilon_i$ are called (or ). If $\varepsilon = (\varepsilon_1,\ldots, \varepsilon_n)$. then $Y = \alpha
+ X\beta +\varepsilon$ i.e. $Y_i = X_i\beta + \varepsilon_i$ for each $i$. We want to know how good a git the line is to the data. The process of linear regression automatically chooses the error terms $\varepsilon_i$ so that $\mathbb{E}(\varepsilon) = 0$. We introduce the (or ) as $$RSS = \sum_{i=1}^n \varepsilon_i^2$$

[Link to video]()

The following is from a [UC Davis website](http://chemwiki.ucdavis.edu/Core/Analytical_Chemistry/Analytical_Chemistry_2.0/05_Standardizing_Analytical_Methods/5.4%3A_Linear_Regression_and_Calibration_Curves). In the picture, the $r_i$ are what we call the $\varepsilon_i$.

<img src="../modules/module2/images/Linear_regression_with_residuals.jpg" alt="linear regression img from a UCDavis website." width="240" />

### Concrete Example 1

The data set used is the `auto-mpg.csv` file.

``` r
> auto.data <- read.csv("datasets/auto-mpg/auto-mpg.csv", header = T, sep=",")
> x <- auto.data$weight
> y <- auto.data$displacement
> lm.fit <- lm(y~x)
> plot(x, y, xlab="weight", ylab="displacement")
> abline(lm.fit)
```

You can get details of the regression line by typing

``` r
> summary(lm.fit)

Call:
lm(formula = y ~ x)

Residuals:
     Min       1Q   Median       3Q      Max
-123.005  -18.836   -0.221   17.040  248.300

Coefficients:
              Estimate Std. Error t value Pr(>|t|)
(Intercept) -147.74719    6.88585  -21.46   <2e-16 ***
x              0.11486    0.00223   51.52   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 37.62 on 396 degrees of freedom
Multiple R-squared:  0.8702,    Adjusted R-squared:  0.8698
F-statistic:  2654 on 1 and 396 DF,  p-value: < 2.2e-16
```

## Concrete Example 2

The data set used is the stature-hand-foot.csv file.

The following is in R.

``` r
> stature.data <- read.csv("datasets/stature-hand-foot/stature-hand-foot.csv", header = T, sep=",")
> pairs(stature.data)
> x <- stature.data$height
> y <- stature.data$hand.length
> lm.fit <- lm(y~x)
> plot(x, y, xlab="height in (mm)", ylab="hand length (in mm)")
> abline(lm.fit)
> summary(lm.fit)

Call:
lm(formula = y ~ x)

Residuals:
    Min      1Q  Median      3Q     Max
-50.130  -1.206   0.055   1.301  49.357

Coefficients:
             Estimate Std. Error t value Pr(>|t|)
(Intercept) -8.638673   9.401507  -0.919     0.36
x            0.124069   0.005596  22.172   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 6.521 on 153 degrees of freedom
Multiple R-squared:  0.7626,    Adjusted R-squared:  0.7611
F-statistic: 491.6 on 1 and 153 DF,  p-value: < 2.2e-16
```

![linear regression on stature data](../modules/module2/images/stature-linear-regression-abline.png)

# Questions

How do measure how good the fit is?

What is a residual? Take a point on the graph and find its signed distance to the regression line. This is the residual for that point

(these questions and answers borrowed from R Cookbook)

1.  Is the model statistically significant? Consult the F statistic

2.  \* Are the coefficients significant? Consult the $t$ statistics and $p$-values in the summary or check the confidence intervals.

3.  Is the model useful? Consult the $R^2$ value

4.  Does the model fit the data well? Plot the residuals

5.  Does the data satisfy the assumptions behind the linear regression? Check whether the diagnostics confirm that a linear model is reasonable for your data

# Reading the summary output

Let’s take the above example using the `stature` data:

``` r
> stature.data <- read.csv("datasets/stature-hand-foot/stature-hand-foot.csv", header = T, sep=",")
> pairs(stature.data)
> x <- stature.data$height
> y <- stature.data$hand.length
> lm.fit <- lm(y~x)
> plot(x, y, xlab="height in (mm)", ylab="hand length (in mm)")
> abline(lm.fit)
> summary(lm.fit)

Call:
lm(formula = y ~ x)

Residuals:
    Min      1Q  Median      3Q     Max
-50.130  -1.206   0.055   1.301  49.357

Coefficients:
             Estimate Std. Error t value Pr(>|t|)
(Intercept) -8.638673   9.401507  -0.919     0.36
x            0.124069   0.005596  22.172   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 6.521 on 153 degrees of freedom
Multiple R-squared:  0.7626,    Adjusted R-squared:  0.7611
F-statistic: 491.6 on 1 and 153 DF,  p-value: < 2.2e-16
```

-   **Residuals**: This is the collection of differences between the the actual values of the variables you’re predicting and the predicted values from your regression $y - \widehat{y}$. Linear regresison lines are chosen so that the mean is always zero. This is why mean isn’t included since it’s always zero. Instead they give you quartile information.

    If you plot the residuals you want the plot to look like a normal distribution with mean zero. It’s important that the distribution is evenly distributed around zero. You can think about this like throwing darts on a dart board. You will probably miss the bullseye but when you do miss it you want your misses to be evenly distributed around the bullseye and not someplace else like around the bottom of the dart board.

-   **Estimated coefficients**: The value of the slope calculated by the regression line. Say you have two variables, $x_1$ and $x_2$ so your linear regression line might look like $y = 3.1 + 5.4 x_1 + 2.7 x_2$. $b_0$. 3.1 is the $y$-intercept, 5.4 is the estimated coefficient for the variable $x_1$, and 2.7 is the estimated coefficient for the variable $x_2$.

-   **Standard error of the coefficient**: Measures the variability in the estimate for the coefficient. You want a lower standard error but remember this value is relative to the coefficient. Usually, you would like the this value to be of an order of magnitude less than the estimated coefficient i.e. if you divide the coefficient by the std. error then you should get a number bigger than 10. For example, if you look at our `stature` example above, notice that the standard error of the $x$ variable is .005596 which is about 22 times smaller than the estimate for the coefficient (0.124069) so this is a good standard error.

-   **$t$-value of the coefficient estimate**: This measures whather or not the coefficient for this variable is meaningful for the model. This has to do which assigning a hypothesis test to the coefficient. The null hypothesis is that the coefficient should be zero. The alternative hypothesis is that the coefficient for the variable is not zero. The $t$ value helps us measure the probability that we would get the estimated coefficient if the coefficient should actually be zero. This is why we usually don’t worry about the $t$-value since the probability (the $p$-value) is given right next to it which is the more important number to look at.

-   **Variable $p$ value**: This is the probability that the variable we would get the estimated non-zero coefficient while the null hypothesis is true, i.e. that the coefficient should actually be zero. So this $p$-value is the probability that this coefficient is *not* relavant. You want this number to be as small as possible. Hence why they put markers next to this number indicating how small the probability is.

-   **Significance stars**: The stars a re shorthand for significance levels with the number of asterisks displayed according to the signifance level. `***` means highly signicant, `**` means somewhat significant, and `*` means only a little bit significant. In our case, `***` next to x means that is highly unlikely that there is no relationship between the variable `hand.length` ($y$) and `height` ($x$).

-   **Residual standard error / Degress of freedom**: The residual standard error is the standard deviation of your residuals. RSE is considered a measure of lack of fit to the data. If the linear regression line lies close to all the data points the linear regression line would be a good fit for the data and then the RSE would be small. If they lie far away then it would not be a good fit and the RSE would be large.

    You also want this number to be proportional to the quantiles of the residuals stated at the beginning of the summary output. For a normal distribution, the 1st and 3rd quantiles should be 1.5 +/- the std error.

    The Degrees of Freedom is the difference between the number of observations included in your training sample and the number of variables used in your model (intercept counts as a variable).

-   **$R^2$**: $R^2$ is a metric for evaluating the goodness of fit of your model. Higher is better with 1 being the best. Corresponds with the amount of variability in what you’re predicting that is explained by the model. In this case about 76.26% of the cause of the `hand.length` is due to the `height`. Remember that while a good $R^2$ value implies correlation, it does not imply causation.

-   **F-statistic and resulting $p$-value**: Performs an F-test on the model. This takes the parameters of our model (in our case we only have 1) and compares it to a model that has fewer parameters. In theory the model with more parameters should fit better. If the model with more parameters (your model) doesn’t perform better than the model with fewer parameters, the F-test will have a high p-value (probability NOT significant boost). If the model with more parameters is better than the model with fewer parameters, you will have a lower p-value.

    In the case where we have multiple variables, say we have a linear regressino equation of $\widehat{y} = b_0 + b_1 x_1 + \ldots + b_n x_m
            = 0$ then the F-statistic answers the following question: Is there a relationship between the response and the predictors? We can set up the following hypothesis test to answer the question: $$\begin{aligned}
                & H_0: b_1 = b_2 = \ldots = b_m \\
                & H_A: \text{at least one }b_j \text{ is non-zero}
            \end{aligned}$$ The actual value of the F-statistic is not too important because we have to compare this value with how large n (the numner data points) and m are compared to eachother. But what is important is the $p$-value next to the F-statistic. If the $p$-value is small, like between 0 and 0.05, then we can be reasonably certain that at least one of the variables is related to our $y$ variable of interest. This would say our model is significant.

    The DF, or degrees of freedom, pertains to how many variables are in the model. In our case there is one variable so there is one degree of freedom.

## Residuals

When you call

``` r
> summary(lm.fit)
```

one of the pieces of information you get is

``` r
Residuals:
    Min      1Q  Median      3Q     Max
-50.130  -1.206   0.055   1.301  49.357
```

The residuals can be seen graphically as the vertical signed distance from a point to the regression line. If the residuals are all zero then you have a perfect fit which would probably not happen. OLSR guarantees that the mean of the residuals is always zero which is why the mean isn’t included. The sign of the median tells us in which way the residuals are skewed. The min and max of the residuals help us find outliers.

The coefficients are $b_0, b_1, \ldots, b_i$. $b_0$ is called the intercept.

You can find the coefficients by typing

``` r
lm(y ~ x)
```

For the `stature` data set you would get something like

    Coefficients:
    (Intercept)            x
        -8.6387       0.1241

So the line which fits the stature data is of the form $y = -8.6387 + 0.1241x$.

## $R^2$ and Residual Standard Error

As defined above the residual sum of squares (or ) is $$RSS = \sum_{i=1}^n \varepsilon_i^2$$ An $R^2$ value close to 1 indicates that the model explains a large portion of the variance in the response variables.

(Description taken borrowed from [Stack Exchange](http://stats.stackexchange.com/questions/57746/what-is-residual-standard-error))

A fitted regression model uses the parameters to generate point estimate predictions which are the means of observed responses if you were to replicate the study with the same XX values an infinite number of times (and when the linear model is true). The difference between these predicted values and the ones used to fit the model are called “residuals” which, when replicating the data collection process, have properties of random variables with 0 means.

When the residual standard error is zero then the line fits the data perfectly. If the residual standard error can not be shown to be significantly different from the variability in the unconditional response, then there is little evidence to suggest the linear model has any predictive ability.

## Concrete examples

**Example:** Suppose you have three points: $(1,1)$, $(2,0.3)$, and $(3,2)$. Suppose we think the line of best fit is $y=0.4 + 0.4x$

``` r
> x <- c(1,2,3)
> y <- c(1,0.3,2)
> y1 <- c(0.8,1.2,1.6)
> plot(x, y, pch=20, xlim=c(0.5,3.5), ylim=c(0.2,2.5))
> points(x, y1, col="red", pch=20)
> abline(0.4,0.4, col="red")
```

![A guess at line of best fit, The red line is $y=0.4+0.4x$](../modules/module6/images/points-and-lines.png)

If we plug in the value $x=1$ into the equation $y=0.4+0.4x$ we get $y(1) = 0.4+0.4(1) = 0.8$. This means if you draw a line parallel to the $y$ axis from the the first point $(1,1)$ to the red line $y=0.4+0.4x$ then we hit the point $(1, 0.8)$. So now we can calculate the distance from the point $(1,1)$ to the line $y = 0.4+0.4x$ by subtracting the $y$ value of the line from the y value of the point: $1-0.8 = .2$. This is the distance from the point to the line. If we plug in the next $x$ value $x= 2$ into the equation for the line we get $y(2) = 0.4+0.4(2)
= 1.2$. The difference between the $y$-value of the second point and the red line is $.3 - 1.2 = -0.9$. Finaly, plug in the final $x$ value into our equation to get $y(3) = 0.4+0.4(3) = 1.6$. THe difference between the third $y$ value and the $y$-value on the red line corresponding to this point is $2 - 1.6 = 0.4$.

We have just calculated all the errors. What happens when we add them all up. We get $.2 + -0.9 + 0.4 = -0.3$. Notice this is a negative number and there is no minimum negative number. This is why we square the errors, so we can minimize the sum of squares.

Adding up the squares we get $0.2^2 + (-0.9)^2 + 0.4^2 = .04 + 0.77 +
0.16 = 0.97$. Now this number puts a quantity to how good a fit the red line $y=0.4+0.4x$ is to the three data points. There could be better lines which have a number smaller than 0.97 for the sum of squares of errors.

We can use R to actually find the line which minimizes the sum of squares. The `lm` function does this.

``` r
> fit <- lm(y~x)
> fit
Call:
lm(formula = y ~ x)

Coefficients:
(Intercept)            x
        0.1          0.5
```

This says that the line of best fit for the three points is $y = 0.1 +
0.5x$. We can plot the new line of best fit against the old line to compare the two.

``` r
> x <- c(1,2,3)
> y <- c(1,.3,2)
> y1 <- c(.8,1.2,1.6)
> plot(x, y, pch=20, xlim=c(.5,3.5), ylim=c(0.2,2.5))
> abline(.4,.4, col="red")
> abline(.1,.5, col="blue")
```

<img src="../modules/module6/images/points-and-two-lines.png" alt="We guessed that the line that modeled the three points shown above was the red line given by y=0.4+0.4x. Using R we got the line of best fit is actually the blue line given by y = 0.1+ 0.5x" width="453" />
