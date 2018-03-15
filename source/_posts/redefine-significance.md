---
title: Redefine statistical significance? Let's just do science in a scientific way.
date: 2017-09-21 07:07:35
tags: [open science, p value]
category: OpenScience
---
Lack of reproducibility of scientific studies has caused growing concern among researchers. Causes of this issue may include multiple testing, p-hacking, publication bias and under-powered studies. Another potential cause has been raised recently. That is, “statistical standards of evidence for claiming new discoveries in many fields of science are simply too low” (Benjamin et al., 2017). The paper on redefining statistical significance has been published in Nature Human Behaviour. The authors included leaders in the push for greater reproducibility. They claimed that the traditional significance (i.e., 0.05) threshold resulted in unexpected high ‘false positive’, and that reducing the p value threshold would “immediately improve reproducibility”.

I agree that using a smaller p threshold (e.g., 0.005) reduces false positives. But I am just wondering what the **false positive rate** really looks like (using traditional p threshold 0.05) if null hypothesis is actually true (Notes: Actually, the false positive rate should theoretically be very close to the p threshold one chooses. Using of the term ‘false positive rate’ in Benjamin et al., 2017 makes me doubt myself about this point. So I decided to conduct a simulation below make sure that my understanding of false positive rate is correct).

It seems that this question can be more directly answered with data simulation. Specifically, we can generate large-sample simulated data (N = 1,000,000) with zero correlation. To simulate one traditional experiment, we can randomly select a subset (n = 50) from the large population, and then correlation can be calculated. By repeating the random selection, we can get many correlation values. Then, we can calculate the false positive rate using some p threshold (e.g., 0.05).

If the false positive rate is just around 5%, the lack of reproducibility issue would have nothing with the significance threshold itself. And moreover, if the false positive rate is very close to 5%, should we still need to redefine statistical significance?

Here are more details for the simulation.

- Simulate two variables (A, B) while controlling the correlation between them (r = 0.0; N = 100,000 or larger).
- Select n (n << N) samples from the simulated population, so we get x and y for A and B, respectively.
- Calculate the correlation between x and y. If the p value of this correlation is less than 0.05, we take it as a false positive.
- Repeat step 2 and 3 for multiple time. Then a false positive rate was calculated for this sample size n.
- Select a different n, and repeat step 2, 3, and 4.

N = 1,000,000

![False positive rate with p threshold of 0.05](/images/post_images/fpr.png "False positive rate with p threshold of 0.05")

As shown in the figure above (and as expected mathematically), the false positive rates are very close to 5% for all sample sizes used. That is, for data with no effect, the false positive rate is just very close to the p threshold used (i.e., 0.05).

The results showed that the significance threshold 0.05 does not result in unexpected false positives, suggesting that the significance threshold itself is not responsible for the lask of reproducibility of research results. The reproducibility issue is not directly caused by the traditional significance threshold, but more related to researchers’ improper behaviours, including p-hacking, and publication bias. Moreover, from the formula for the probability of false positives in published resuts below, you can see another factors contributing to the final results: prior odds and power (1-beta). As we don’t know about the real prior odds, low power would be the major problem for lask of reproducibility of published results (even if there is no p-hacking). In sum, it is these improper behaviours (e.g., p-hacking and power failure) that cause reproducibility issues of published results, rather than the standard significance threshold itself.

Thus I would say that what researchers need to do for solving the reproducibility issue is to conduct studies scientifically. **No p-hacking, Enough sample size** (for high statistical power). For example, one should justify your choice for a significance level and a good sample size before collecting the data. Otherwise, if one insists on improper behaviours, and doesn’t do science in a scientific way, any statistical significance redefinition or fancy method will be in vain (e.g., researchers may use p-hacking with any inferential threshold).

In addition, causes of lack of reproducibility are complex and sometimes uneasy to control perfectly. For example, for some situations, one can not determine the sample size before collecting the data. In this case, he/she still has an alternative solution: simply replicate your results with an independent sample.

With either solution, let’s say: **Do science in a open, transparent and reproducible way!**

References:
Benjamin, Daniel J., et al. “Redefine statistical significance.” Nature Human Behaviour (2017).
Lakens, D. et al. https://psyarxiv.com/9s3y6 (2017).

Notes:
![False positive report probability definition
](/images/post_images/fpr2.png "False positive report probability definition")

In Benjamin et al., 2017, ‘False positive rate’ was defined like this. This seems somehow misleading. The formula actually means the probability that a significant finding is a false positive. A better name would be False Positive Report Probability, as used in Lakens et al., 2017. Note that this formula is not the typical definition of false positive rate.

A similar formula was used in Power failure: why small sample size undermines the reliability of neuroscience.