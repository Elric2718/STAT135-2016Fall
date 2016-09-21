.. _part2_:

======
Part 2
======

Suppose :math:`\{ X_i \}_{i=1}^n` are i.i.d :math:`\mathcal{N}(\mu, 1)`
where :math:`n=30` and :math:`\mu=log(\sqrt{2})` (Please
Download The Data *Sec4_Part2.Rda* from `bcourse <https://bcourses.berkeley.edu/courses/1453788/files/folder/Data>`_).
Use the bootstrap to build a confidence interval for :math:`\mu` with the 3 methods:
pivotal, normal and percentil. To assess the quality of the different bootstrap
intervals, re-simulate from the population distribution and assess the coverage
probability. Use :math:`N=1000` simulation.

.. hidden-code-block:: R                                          
   :label: Solution                                               
   :linenos:

   n = 30
   B <- 1000
   mu = log(sqrt(2))

   result <- replicate(1000, {
      X <- rnorm(n, mu, 1)
      
      ## using mean as the estimator for mu
      mu_hat <- mean(X)

      ## bootstrap
      mu_hat_star <- replicate(B, {X_star <- sample(x = X, size = n, replace = TRUE);
      mean(X_star)})

      ## percentile confidence interval
      CI_percentile <- quantile(mu_hat_star, c(alpha/2, 1-alpha/2))
      
      ## normal confidence interval
      CI_normal <- mu_hat + qnorm(c(alpha/2, 1 - alpha/2)) * sd(mu_hat_star)

      ## pivotal confidence interval
      CI_pivotal <- 2 * mu_hat - quantile(mu_hat_star, c(1 - alpha/2, alpha/2))

      ## coverage
      c((CI_percentile[1] <= mu & CI_percentile[2] >= mu),
        (CI_normal[1] <= mu & CI_normal[2] >= mu),
	(CI_pivotal[1] <= mu & CI_pivotal[2] >= mu))
   })

   rowMeans(result)
					  
