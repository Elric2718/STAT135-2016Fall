.. _basic_testing_:

=================
Basics of Testing
=================

* Introduction:

  In previous lectures, we've encountered point estimation, that is, estimate a paramter in
  a distributio and confidence interval. The two problems are the two main estimation problems in statistics.
  Other than estimation, we're also interested in hypothesis testing. Literally, we have
  a hopothesis about the data, e.g., testing if the mean of the underlying distribution equal to 0,
  and then use some statistics tools to test if it's true or not.

* Basics:

  1. We first have the null hypothesis :math:`H_0` and the alternative hypothesis :math:`H_1`.
     If :math:`H_0` (:math:`H_1`) specifies a distribution, e.g., it specifies the
     mean of the normal distribution given a unit variance, it's called simple
     null (alternative) hypothesis.
  2. Once we have the hypotheses, we'll come up with the test statistics, based on which
     we make the decision (accept or reject :math:`H_0`).
  3. Then we need to set a standard to accept the null hypothesis (reject the alternative) or reject the null (accept the alternative).
     Our goal is to control the possibility of making wrong decisions. There are two
     types of errors: Type I (II) error is rejecting (accepting) the null hypothesis when the underlying
     truth is the null (alternative) hypothesis. The probability of Type I (II) error
     is :math:`\alpha` (:math:`\beta`). We cannot control both simultaneously. We always
     first control Type I error :math:`\alpha`, then try to maximize :math:`1 - \beta`, i.e., the power.
  4. Finally we find a rejection region. If our test statistics falls in the region,
     we reject :math:`H_0`, otherwise we accept it. The rejection region is determined
     so that the test statistics will fall in it with the probabilty at most :math:`\alpha`
     if the underlying truth is :math:`H_0`. In most cases, the rejection region looks like
     :math:`{T>t}` or :math:`{T<t}`, where :math:`T` is the test statistics and :math:`t` is
     called the critical value. The most cases we'll encounter are simples tests, of which,
     the rejection region can be computed by *likelihood ratio test*:
     
     Reject :math:`H_0` if :math:`\frac{f_0(X)}{f_1(X)}<c(\alpha)`

     where :math:`c(\alpha)` is an intermediate value (we may not figure out) which makes the rejection region satisfy
     our Type I error control level :math:`\alpha`. By Neyman-Pearson Lemma, *Likelihood ratio test* is 
     the optimal. We'll see many examples in today's sections about how to do such tests.

     





