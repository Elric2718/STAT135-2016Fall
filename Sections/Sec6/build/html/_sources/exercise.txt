.. _exercise_:

========
Exercise
========      
1. (Section 9.11 Problem 2) Which of the following hypothese are simple, and which are
   composite?

   a. :math:`X` follows a uniform distribution on :math:`[0, 1]`.
   b. A die is unbiased.
   c. :math:`X` follows a normal distribution with mean :math:`0` and variance :math:`\sigma^2>10`.
   d. :math:`X` follows a normal distribution with :math:`\mu = 0`.


2. (Section 9.11 Problem 3) Suppose that :math:`X\sim bin(100, p)`. Consider the test
   that reject :math:`H_0:p=.5` in favor of :math:`H_A: p\neq .5` for :math:`|X-50|>10`.
   Use the normal approximation to the binomial distribution to answer the following:
   
   a. What is :math:`\alpha`?
   b. Graph the power as a function of :math:`p`.
	 


3. Let :math:`X` have one of the following distributions:
   
   ===========  ===========  ===========
   :math:`X`    :math:`H_0`  :math:`H_1`
   ===========  ===========  ===========
   :math:`x_1`  .2           .1
   :math:`x_2`  .3           .4
   :math:`x_3`  .3           .1
   :math:`x_4`  .2           .4
   ===========  ===========  ===========

   a. Compare the likelihood ratio, :math:`\Lambda`, for each possible value :math:`X`
      and order the :math:`x_i` according to :math:`\Lambda`.
   b. What is the likelihood ratio test of :math:`H_0` versus :math:`H_A` at level
      :math:`\alpha = .2`? What is the test at level :math:`\alpha = .5`?


   

4. A trial had the following characteristics. Recent research suggests dogs could be
   helpful in detecting when a person has cancer. 6 dogs were enrolled in 9 trials. In
   each of the 54 trials, one urine sample from patient with bladder cancer was randomly
   placed among six control urine samples. In the 54 trails, the dogs made the correct
   selection 22 times. Does this study provide evidence that the dogs' predictions are
   better than random guessing? (Assume that it's OK to use the test we design for
   Binomial data for simple vs simple and say whether or not you would reject thenull. Please
   first formulate the null hypothesis and the alternative hypothesis).

5. (Section 9.11 Problem 6) Consider the coin tossing example of Section 9.1. Suppose that instead of tossing
   the coin 10 times, the coin was tossed until a head came up and the total number
   of tosses, :math:`X`, was recorded.

   c. What is the significance level of a test that rejects :math:`H_0` if :math:`X\geq 8`?
   d. What is the power of this test?

6. (Section 9.11 Problem 7) Let :math:`X_1, \dots, X_n` be a sample from a Poisson distribution.
   Finde the likelihood ratio for testing :math:`H_0: \lambda = \lambda_0` versus :math:`H_A: \lambda = \lambda_1`,
   where :math:`\lambda_1 > \lambda_0`. Use the fact that the sum of independnet Poisson random
   variables follows a Poisson distribution to explain how to determine a rejection region
   for a test at level :math:`\alpha`. And how to compute the power.
