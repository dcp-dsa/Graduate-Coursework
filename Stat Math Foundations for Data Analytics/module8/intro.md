# Classification versus linear regression

## Topics covered

-   Logistic regressions (sections 4.1 - 4.3 of ISLR book)

-   An overview of classification

-   Why not linear regression

-   Logisitic regression

    -   Graphical explanation (figure 4.2 of ISLR book pg 131)

    -   The logisitic model (mathematical explanation)

    -   Estimating the regression coefficients

    -   making predictions

    -   multiple logistic regression

    -   Logistic regresion for &gt;2 response classes

Suppose now we have a data set with a qualitative variable instead of a quantitative variable. For example, take the data set `census` which gives census information for about 50,000 individuals. There is a variable in this data set named `earning.above.50k` which is either a 0 or a 1 depending on whether the individual earns below 50,000 dollars a year or above respectively. We can’t base a linear regression model on this information because it wouldn’t be a very good model. We have to do something different. This is where a logistic regression comes in handy.

For the `census` data, the logistic regression models the probability of earning above 50k given the data at hand. The probability of earning above 50k given a certain variable is written as Pr(`earning.above.50k` | `variable`). For example, in the census data we have variables like `age`, `workclass`, and `occupation`. So we could explore probabilities like Pr(`earning.above.50k` | `age`) or, more speicifcally, something like Pr(`earning.above.50k` | `age` &lt; 30) which finds the probability of earning about 50k given the person is below 30 years old.

The logistics model wants to find the relationship between $p(X) =
Pr(Y=1 | X)$ and $X$

We will use the *logistic function*: $$p(X) = \frac{e^{\beta_0+\beta_1X}}{1+e^{\beta_0+\beta_1X}}$$ If we do some algebra we get that $$\frac{p(X)}{1-p(X)} = e^{\beta_0+\beta_1 X}.$$ This expression is called the *odds function*. Taking the logarithm of both sides gives us this: $$\log\left( \frac{p(X)}{1-p(X)} \right) = \beta_0 + \beta_1 X.$$ Notice that the log of this function in parenthesis is a linear function. This is important.
