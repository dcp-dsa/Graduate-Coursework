## Hypothesis testing

-   Logic of hypothesis testing (ch 11 of ItS book)

    -   Intro

    -   Significance testing

    -   Type I and Type II errors

    -   One- and two- tail tests (still needs to be done)

    -   Interpreting significant/non-significant results

    -   Steps in hypothesis testing

    -   Significance testing and confidence intervals

    -   Misconceptions

### Lady tasting tea

#### Lady tasting tea

The original example given by Ronald Fisher in the early 20th century goes like this: A lady says she has the ability to taste a cup of tea and decide if milk was added to the cup frst or tea was added first. A blind taste test was set up. The lady was given 8 cups of tea all at onece without knowing whether milk or tea was added first each time. In 4 of the cups of tea, milk was added first and in the other 4, tea was added first. She correctly guess all 4 cups of the same type of tea. The question is whether this lady was able to actually tell the different cups apart or if she was just guessing. We start off with something called the *null hypothesis*, denoted $H_0$. This is the statement that the lady does not have the ability to discern the different cups and she was just guessing. The complimentary but opposite statement is called the *alternative hypothesis*, denoted $H_1$, which says the the lady does, in fact, have the ability to tell the cups apart.

Usually when someone does this sort of test, called a hypothesis test, they start off with an acceptable percentage, called a significance level and denoted by alpha. Most times alpha is 5 percent. If the lady correctly identifies the correct cup classifications then the chance of her doing that by random guessing would be 1 in 70 since there are 70 ways to choose 4 cups out of 8 cups up to permutation. 1/70 is .014 or 1.4 percent. 1.4 percent is less then 5 percent so we say that we can reject the null hypothesis because 1.4 percent is less than 5 percent. If we had chosen a smalled significance level like 1 percent then we could not reject the null hypothesis.

Notice that we have not proved whether the lady actually did have the ability to tell whether milk or tea was added first. That might be impossible. We have only shown that her trials were statistically significant enough to reject the null hypothesis which says she does not have that ability.

#### Generalization

Notice that if we think of the tea tests as a random variable (say $X$) and the lady’s choice “milk first” or “tea first” as a random variable (say $Y$) then what we’re really asking is whether the two variables are related. We can then see the parameters of the hypothesis as

$\alpha = .05$
$H_0$: null hypothesis: $X$ does not correspond to $Y$
$H_1$: alternative hypothesis: $X$ corresponds to $Y$

#### Another example

Suppose an animal trainer says that her parrot can tell whether a number is even or odd. You decide to test this. You set up a test where you will show the parrot 16 numbers, one after another, and the parrot will say yes or no depending on whether the number is in fact divisible by 7. The numbers are chosen so that there is a 50 percent chance that the number is divisible by 7. The null hypothesis, $H_0$, is that there is no correlation between the bird saying yes or no and the fact that the numbers are divisible by 7 or not, i.e. that the bird does not have this arithmetic ability. The alternative hypothesis, $H_1$, is that there is a correlation and that the bird does have the ability.

We choose a significance level of 5 percent i.e. $\alpha = 0.05$ before the process begins. The bird ends up correctly identify correctly 13 out of the 16 numbers shown. He got 3 wrong. Does this meet our 5 percent significance level? The chance of getting 13 out of 16 choices correct where each choice has a 50 percent chance of being correct, purely by guessing, is 0.0106 i.e. 1.06 percent. So we sa ythe results of this test are statisitcally significant ot reject the null hypothesis and accept the alternative hypothesis.

#### Court ruling

We can think of hypothesis testing as a courtroom trial. We start off assuming the defendant is not guilty. This corresponds to the null hypothesis $H_0$. Only when there is enough evidence can we reject the null hypothesis and charge the defendant as guilty. This is the alternative hypothesis.

#### Types of errors

The following is a table about the null hypothesis of a hypothesis testing. The top cells are about whether the null hypothesis is true or false. The left hand cells tell whether we reject or accept the null hypothesis.

[]<span>l|l|l</span> & valid/true & invalid/false
reject & Type I error & Correct inference
accept & Correct inference & Type II error

