.. _part1_:

******
Part 1
******
Suppose :math:`\{ X_i \}_{i=1}^n` are i.i.d :math:`Bernoulli(p)`

1. Show that :math:`\hat{p} = \sum_{i=1}^n X_i/n` is asymptotically
   normal with mean :math:`p` and variance :math:`p(1-p)/n`.

   Solution:
   
   :math:`\mathbb{E} \sum_{i=1}^n X_i/n = p`
	 
   :math:`var(\sum_{i=1}^n X_i/n) = var(X_1)/n = p(1-p)/n`
	 
   By CLT, it follows that :math:`\sqrt{n}(\hat{p} - p)\overset{d}{\rightarrow} \mathcal{N}(0, p(1-p))`

   

2. Use :math:`\delta`-method to derive the asymptotic distribution of :math:`arcsin(\sqrt{\hat{p}})`.
   How does the variance of this distribution depend on :math:`p`?

   Solution:
   
   Notice that :math:`h(x) = arscin(x)` has the derivative :math:`h'(x) = 1/\sqrt{1 - x^2}`.

   Let :math:`g(x) = h(\sqrt{x})`. Then :math:`g'(x)=\frac{1}{2\sqrt{x - x^2}}`. By :math:`\delta`-method,

   :math:`\sqrt{n}(arcsin(\sqrt{\hat{p}}) - arcsin(\sqrt{p})) \overset{d}{\rightarrow} \mathcal{N}(0, (g'(p))^2 \cdot p(1-p))=\mathcal{N}(0, \frac{p(1-p)}{4(p - p^2)})=\mathcal{N}(0, 1/4)`
   
3. For :math:`n = 10, 20, 50, 100, 1000` and :math:`p = .05, .25, .5`, create histogram
   of :math:`\hat{p}` to investigate the sampling distribution of :math:`\hat{p}`. Use
   :math:`B = 10000` repetitions for each estimator. How normal do the sampling distributions
   look like.
   
   .. hidden-code-block:: R
      :label: Solution
      :linenos:
	 
      n <- 1000
      p <- 0.25
      B <- 10000

      ## repeat the estimators for B times
      p_hat <- replicate(B, {X <- rbinom(n, 1, p); mean(X)})

      # summary
      summary(p_hat)

      # plot the histogram
      hist(p_hat)

      # the difference between sample variance and the theoretical one
      var(p_hat) - p * (1 - p)/n

4. Use the previous simulations to plot histograms of :math:`\tilde{p} = arcsin(\sqrt{\hat{p}})`.
   How normal does the sampling distribuiton look? Compare the varinace of the sampling
   distribution of the estimator. How well does it match the theoretical predictions?

   .. hidden-code-block:: R
      :label: Solution
      :linenos:

      p_tilde <- asin(sqrt(p_hat))

      # summary
      summary(p_tilde)

      # plot the histogram
      hist(p_tilde)

      # the difference between sample variance and the theoretical one
      var(p_tilde) - 1/(4*n)

5. For :math:`n = 10, 20, 50, 100, 1000` and :math:`p = .05, .25, .5`, build bootstrap
   confidence intervals for :math:`p` (using the 3 methods described in the slides: percentil,
   normal and pivotal). Repeat :math:`1000` times. Report the coverage probability. Based on this,
   which method would you favor?
   
   .. hidden-code-block:: R
      :label: Solution
      :linenos:

      alpha <- 0.05
      p <- 0.25
      n <- 100
      B <- 1000

      result_Q5 <- replicate(1000, {

	 X <- rbinom(n, 1, p)
	 p_hat <- mean(X)

	 ## bootstrap
	 p_hat_star <- replicate(B, {X_star <- sample(x = X, size = n, replace = TRUE);
	                             mean(X_star)})

	 ## percentile confidence interval
	 CI_percentile <- quantile(p_hat_star, c(alpha/2, 1-alpha/2))
      
	 ## normal confidence interval
	 CI_normal <- p_hat - qnorm(c(1 - alpha/2, alpha/2)) * sd(p_hat_star)

	 ## pivotal confidence interval
	 CI_pivotal <- 2 * p_hat - quantile(p_hat_star, c(1 - alpha/2, alpha/2))

	 ## coverage
	 c((CI_percentile[1] <= p & CI_percentile[2] >= p),
	   (CI_normal[1] <= p & CI_normal[2] >= p),
	   (CI_pivotal[1] <= p & CI_pivotal[2] >= p))
      })

      rowMeans(result_Q5)

6. For :math:`n = 10, 20, 50, 100, 1000` and :math:`p = .05, .25, .5`, build normal-limit
   theory confidence intervals as we've seen befoe. Repeat :math:`1000` times. Report
   the coverage probability. Based on this, which method would you favor: the theoretical version of the
   bootstrap?

   .. hidden-code-block:: R
      :label: Solution
      :linenos:

      result_Q6 <- replicate(1000, {
        X <- rbinom(n, 1, p)
	p_hat <- mean(X)

	## normal-limit theory confidence interval
	CI_theory <- p_hat + qnorm(c(alpha/2, 1 - alpha/2)) * sqrt(p_hat * (1 - p_hat))/sqrt(n)

	## coverage
	(CI_theory[1] <= p & CI_theory[2] >= p)
      })

      mean(result_Q6)

7. Repeat the previous 2 items for the parameter :math:`\theta = arcsin(\sqrt{p})`.

   .. hidden-code-block:: R
      :label: Solution
      :linenos:

      theta <- asin(sqrt(p))

      result_Q7 <- replicate(1000, {

	 X <- rbinom(n, 1, p)
	 p_hat <- mean(X)
	 p_tilde <- asin(sqrt(p_hat))

	 ## bootstrap
	 p_tilde_star <- replicate(B, {X_star <- sample(x = X, size = n, replace = TRUE);
	 asin(sqrt(mean(X_star)))})
	 
	 ## percentile confidence interval
	 CI_percentile <- quantile(p_tilde_star, c(alpha/2, 1-alpha/2))

	 ## normal confidence interval
	 CI_normal <- p_tilde + qnorm(c(alpha/2, 1 - alpha/2)) * sd(p_tilde_star)
	 
	 ## pivotal confidence interval
	 CI_pivotal <- 2 * p_tilde - quantile(p_tilde_star, c(1 - alpha/2, alpha/2))

	 ## normal-limit theory confidence interval
	 CI_theory <- p_tilde + qnorm(c(alpha/2, 1 - alpha/2))/(2 * sqrt(n))

	 ## coverage
	 c((CI_percentile[1] <= theta & CI_percentile[2] >= theta),
	   (CI_normal[1] <= theta & CI_normal[2] >= theta),
	   (CI_pivotal[1] <= theta & CI_pivotal[2] >= theta),
	   (CI_theory[1] <= theta & CI_theory[2] >= theta))
	 })

      rowMeans(result_Q7)
						  
		  
