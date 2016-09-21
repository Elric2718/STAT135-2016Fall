.. _exercise:


Section 8.10, Problem 44
========================

The file bodytemp contains normal body temperature
readings (degrees Fahrenheit) and heart rates (beats
per minute) of 65 males (coded by 1) and 65 females
(coded by 2) from Shoemaker (1996). Assuming that the
population distributions are normal (an assumption that
will be investigated in a later chapter), estimate the
body temperature means and standard deviations of the males and females.
Form 95% confidence intervals for the means. Standard folklore is
that the average body temperature is 98.6 degrees Fahenheit.
Does this appear to be the case.


Solution
--------

We first load the data and extract a basic information::

  data <- read.csv("~/Desktop/temp/bodytemp.csv")

  n_m <- length(data[data[, 2] == 1, 1])
  n_fm <- length(data[data[, 2] == 2, 1])

Then we calculate the means and standard deviations respectively::

  ## means
  mean_temp_m <- mean(data[data[,2] == 1,1])
  mean_temp_fm <- mean(data[data[,2] == 2,1])

  ## standard deviations

  sd_temp_m <- sd(data[data[,2] ==1, 1])
  sd_temp_fm <- sd(data[data[,2] ==2, 1])

Recall that if

    :math:`X_i \overset{iid}{\sim} N(\mu, \sigma^2), i = 1, \dots, n`

then we have

    :math:`\sqrt{n} \frac{\bar{X} - \mu}{S_n} \sim t_{n-1}`

where

    :math:`\bar{X} = \frac{1}{n} \sum_{i=1}^n X_i,~S_n^2 = \frac{1}{n-1}\sum_{i=1}^n(X_i - \bar{X})^2`.

This conclusion is important. You may use them as well in HW3.

Let's form the confidence interval now::

  > interval_temp_m <- c(mean_temp_m - sd_temp_m * qt(0.975, n-1)/sqrt(n),
  +                      mean_temp_m + sd_temp_m * qt(0.975, n-1)/sqrt(n))
  > interval_temp_m
  [1] 97.93147 98.27776
  >
  > interval_temp_fm <- c(mean_temp_fm - sd_temp_fm * qt(0.975, n-1)/sqrt(n),
  +                      mean_temp_fm + sd_temp_fm * qt(0.975, n-1)/sqrt(n))
  > interval_temp_fm
  [1] 98.20962 98.57807
					      
The result seems not the case for standard folklore.
  
