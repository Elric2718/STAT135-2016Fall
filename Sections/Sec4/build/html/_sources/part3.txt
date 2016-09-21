.. _part3_:
======
Part 3
======

Use the data of Problem 44 (which you did in sections last week) and use the
bootstrap to answer the questions in this problem. How do the answers differ
from those you got last week?

.. hidden-code-block:: R
   :label: Solution
   :linenos:

   data <- read.csv("~/Desktop/temp/bodytemp.csv")
   B <- 1000
   alpha <- 0.05

   index_m <- which(data[, 2] == 1)
   index_fm <- which(data[, 2] == 2)

   n_m <- length(index_m)
   n_fm <- length(index_fm)

   bt_m <- data[index_m, 1]
   bt_fm <- data[index_fm, 1]

   mu_hat_m <- mean(bt_m)
   mu_hat_fm <- mean(bt_fm)

   ## bootstrap
   mu_hat_m_star <- replicate(B, {X_star <- sample(x = bt_m, size = n_m, replace = TRUE);
                                   mean(X_star)})
   mu_hat_fm_star <- replicate(B, {X_star <- sample(x = bt_fm, size = n_fm, replace = TRUE);
                                   mean(X_star)})

   ## percentile confidence interval
   CI_percentile_m <- quantile(mu_hat_m_star, c(alpha/2, 1-alpha/2))
   CI_percentile_fm <- quantile(mu_hat_fm_star, c(alpha/2, 1-alpha/2))
      
   ## normal confidence interval
   CI_normal_m <- mu_hat_m + qnorm(c(alpha/2, 1 - alpha/2)) * sd(mu_hat_m_star)
   CI_normal_fm <- mu_hat_fm + qnorm(c(alpha/2, 1 - alpha/2)) * sd(mu_hat_fm_star)

   ## pivotal confidence interval
   CI_pivotal_m <- 2 * mu_hat_m - quantile(mu_hat_m_star, c(1 - alpha/2, alpha/2))
   CI_pivotal_fm <- 2 * mu_hat_fm - quantile(mu_hat_fm_star, c(1 - alpha/2, alpha/2))
   
   CI_percentile_m
   CI_percentile_fm
   CI_normal_m
   CI_normal_fm
   CI_normal_m
   CI_normal_fm
