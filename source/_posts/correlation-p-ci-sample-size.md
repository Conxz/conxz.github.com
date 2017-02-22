---
title: Correlation, p-value, CI, and Sampe Size
date: 2012-11-03 22:10:27
tags:
---
Lately in my research, I have been focusing on correlations between behavioral data from a large dataset. As is known, correlation is an expression of how well the linear relationship between two sets of data, that is to say, how they are related under the simple linear model. To give an example, for researchers, number of papers and their salary are well correlated. Thus, you can use a researcher’ number of papers to predict his/her salary. It is important to note that ‘correlation does NOT imply causation‘.

Since correlation statistics are based on samples, rather than the whole population, even when you have a large dataset, there is some uncertainty about the correlation value. In most published papers, we can see a p value following the correlation coefficient r. Similarly, researchers also use the confidence interval (CI) for a given correlation value. It seems that p and CI are two different ways to show the uncertainty, as researcher always get the p value of a given r by checking the r-p table. However, we can get p and CI in similar way. That is the Fisher’s Z transformation. You can check the detail from [link]. I just add here from this process, we can see that both p-value and CI of a given correlation only depend on the sample size. With increasing sample size, the p-value becomes smaller while CI become narrower, which means that you can be more certain about the relationship you found.

Of course, besides Fisher’s Z transformation, there are other methods for p or CI computation, e.g., the nonparametric bootstrapping testing.