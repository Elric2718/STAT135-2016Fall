.. _exercise_:

====================
Solution to Exercise
====================      
1. (Section 9.11 Problem 2) Which of the following hypothese are simple, and which are
   composite?

   a. :math:`X` follows a uniform distribution on :math:`[0, 1]`.
   b. A die is unbiased.
   c. :math:`X` follows a normal distribution with mean :math:`0` and variance :math:`\sigma^2>10`.
   d. :math:`X` follows a normal distribution with :math:`\mu = 0`.

   Solution:
   
   a. simple
   b. simple
   c. composite
   d. composite

2. (Section 9.11 Problem 3) Suppose that :math:`X\sim bin(100, p)`. Consider the test
   that reject :math:`H_0:p=.5` in favor of :math:`H_A: p\neq .5` for :math:`|X-50|>10`.
   Use the normal approximation to the binomial distribution to answer the following:
   
   a. What is :math:`\alpha`?
   b. Graph the power as a function of :math:`p`.

   Solution:
   
   a. By CLT, we have
      :math:`\sqrt{100}\cdot \frac{(X/100 - p)}{\sqrt{p(1- p)}} \overset{d}{\rightarrow} N(0,1)`.
      Under the null hypothesis, we can approximately take :math:`\sqrt{100}\cdot \frac{(X/100-.5)}{.5\cdot(1-.5)}\approx Z\sim N(0,1)`.
      Thus :math:`|X - 50| \approx 5|Z|`. The rejection region :math:`|X - 50| > 10` is equivalent
      to :math:`|Z| > 2`. Then by definition, :math:`\alpha = \mathbb{P}(|Z|>2) \approx 0.0455`.

   b. Similary, we have the approximation :math:`\sqrt{100}\cdot \frac{X/100 - p}{\sqrt{p(1-p)}} \approx Z`,
      which implies :math:`|X - 50| \approx |10\sqrt{p(1-p)}Z) + 100p -50|`. The power function is
      :math:`\beta(p) = \mathbb{P}(|10\sqrt{p(1-p)}Z + 100p - 50|>10)=\mathbb{P}(Z>\frac{6-10p}{\sqrt{p(1-p}} ~or~ Z<\frac{4-10p}{\sqrt{p(1-p)}})`
      The graph is as below:

      .. image:: _static/power.png
	 


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

   Solution:

   a. :math:`\Lambda(x) = \frac{p(x|H_0)}{p(x|H_1)}`, thus we have :math:`\Lambda(x_4) = \frac{1}{2}<\Lambda(x_2) = \frac{3}{4} <\Lambda(x_1) = 2 <\Lambda(x_3) = 3`.
   b. The :math:`.2` level likelihood ratio test is

      :math:`\Lambda(X) \leq \frac{1}{2}` or :math:`X = x_4` since :math:`\mathbb{P}(X = x_4|H_0) = 0.2`.

      The :math:`.5` level likelihood ratio test is

      :math:`\Lambda(X) \leq \frac{3}{4}` or :math:`X = x_2~or~x_4` since :math:`\mathbb{P}(X = x_4~or~ X = x_2|H_0) = 0.5`.
      

   

4. A trial had the following characteristics. Recent research suggests dogs could be
   helpful in detecting when a person has cancer. 6 dogs were enrolled in 9 trials. In
   each of the 54 trials, one urine sample from patient with bladder cancer was randomly
   placed among six control urine samples. In the 54 trails, the dogs made the correct
   selection 22 times. Does this study provide evidence that the dogs' predictions are
   better than random guessing? (Assume that it's OK to use the test we design for
   Binomial data for simple vs simple and say whether or not you would reject thenull. Please
   first formulate the null hypothesis and the alternative hypothesis).

   Solution:

   We can use similar arguments in Problem 2, that is, the number of correct selections :math:`X`, follows :math:`Binom(54, p)`
   and our hypotheses are :math:`H_0: p = \frac{1}{7}` v.s. :math:`H_1: p \neq \frac{1}{7}`. By normal
   approximation, we have

   :math:`\sqrt{54}\cdot \frac{X/54 - p}{\sqrt{p(1-p)}} \approx Z \sim N(0,1)`

   Then we can provide an :math:`\alpha` level rejection region as

   :math:`|3\sqrt{6} \frac{X/54 - 1/7}{\sqrt{1/7\cdot(1 - 1/7)}}| > z_{1 - \alpha/2}`

   or

   :math:`X > \frac{54}{7} + \frac{18}{7}z_{1-\alpha/2}~or~ X < \frac{54}{7} - \frac{18}{7} z_{1-\alpha/2}`

   Set :math:`\alpha = 0.05`, which is a common standard, the rejection region is

   :math:`X \geq 10~or~ X\leq 5`

   Since :math:`X = 22`, it implies that the dogs' predictions are better than random guessing.

5. (Section 9.11 Problem 6) Consider the coin tossing example of Section 9.1. Suppose that instead of tossing
   the coin 10 times, the coin was tossed until a head came up and the total number
   of tosses, :math:`X`, was recorded.

   c. What is the significance level of a test that rejects :math:`H_0` if :math:`X\geq 8`?
   d. What is the power of this test?

   Solution:

   c. This is a geometric distribution with :math:`G(p)`. We have hypotheses as
      :math:`H_0: p = 0.5` v.s. :math:`H_1: p = 0.7`. The significance level is
      :math:`\mathbb{P}(X \geq 8|H_0) = 1 - \sum_{k=1}^8 (1-0.5)^{k-1}\cdot 0.5 = (0.5)^8 \approx 0.0039`.
   d. The power is :math:`\mathbb{P}(X \geq 8|H_1) = 1 - \sum{k = 1}^8 (1-0.7)^{k-1}\cdot 0.7 = 6.561e-05`
     

      

6. (Section 9.11 Problem 7) Let :math:`X_1, \dots, X_n` be a sample from a Poisson distribution.
   Finde the likelihood ratio for testing :math:`H_0: \lambda = \lambda_0` versus :math:`H_A: \lambda = \lambda_1`,
   where :math:`\lambda_1 > \lambda_0`. Use the fact that the sum of independnet Poisson random
   variables follows a Poisson distribution to explain how to determine a rejection region
   for a test at level :math:`\alpha`. And how to compute the power.

   Solution:

   The likelihood ratio is

   :math:`\Lambda_1(x) = \frac{f_0(x)}{f_1(x)} = (\frac{\lambda_0}{\lambda_1})^x e^{\lambda_1 - \lambda_0}`

   Denote :math:`Y = \sum_{i=1}^n X_n`, then :math:`Y\sim Poisson(n\lambda)`. The likelihood ratio test for :math:`Y` is

   :math:`\Lambda_n(Y) = (\frac{\lambda_0}{\lambda_1})^Y exp(n(\lambda_1 - \lambda_0)) \leq c(\alpha)` or :math:`Y \geq \tilde{c}(\alpha)`, where :math:`\tilde{c}(\alpha)
   is determined as

   :math:`\tilde{c}(\alpha):=arg\max_{c} \mathbb{P}(Y\geq c|H_0)\leq\alpha`

   As for the power, once we figure out :math:`\tilde{c}`, it can be computed as

   :math:`1 - \mathbb{P}(Y \geq \tilde{c}(\alpha))`

   (Note that :math:`\mathbb{P}(Y \geq c) = \sum_{k\geq c} \frac{(n \lambda)^k}{k !} e^{-n\lambda}`,
   where :math:`\lambda = \lambda_0` under :math:`H_0` or :math:`\lambda = \lambda_1` under :math:`H_1`).


   
