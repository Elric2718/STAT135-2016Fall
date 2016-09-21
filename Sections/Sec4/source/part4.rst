.. _part4_:
======
Part 4
======

For :math:`n = 10,~100,~1000`, generate samples from the distribution with
density :math:`f(x) = \frac{1}{2}exp(-|x - \theta|)`, where the true :math:`\theta = 0`.
It's the laplace distribution. Compute the sampling distribution of the median of a sample from that distribution
by simulations. How does it compare to the theoretical predictions? Hint: It can
be assumed that the median is MLE.

From HW1, we know that the hint is correct. To understand the theoretical predictions,
we need to calculate the Fisher Information. Note that

:math:`(\frac{\partial}{\partial \theta} \log f(x))^2 = 1` except for :math:`x = \theta`.

But the probability of a continuous random varaible taking one value is 0, which means
we can ignore the singular phenomenon when calculating the expectation. It's easy to see
that :math:`I(\theta) = 1`. So the theoretical predictions is

:math:`\sqrt{n}\cdot Median(\{X_i\}_{i=1}^n)\overset{d}{\rightarrow}\mathcal{N}(0, 1)`

.. hidden-code-block:: R
   :label: Solution
   :linenos:

   ## install package
   install.packages("distr")
   library("distr")

   n <- 1000
   B <- 1000
   D <- DExp(rate = 1)

   theta_hat <- replicate(B, {X <- r(D)(n); median(X)})

   summary(theta_hat)

   hist(theta_hat)

   var(theta_hat) - 1/n

   ## sampling distribution
   sampling_cdf <- function(x){
     sum(theta_hat <= x)/B
   }

   for(i in seq(-1, 1, by = 0.1)){
      print(sampling_cdf(i) - pnorm(i, mean = 0, sd = 1/sqrt(n)))
   }

       


