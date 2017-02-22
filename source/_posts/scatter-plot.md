---
title: Seeing is Believing, Binned Scatter Plot
date: 2012-11-07 21:10:27
tags:
---
“Seeing is believing” is an idiom meaning “only physical or concrete evidence is convincing”. According to the Wikipedia, it leads to a sophistry that “seen evidence” can be easily and correctly interpreted, when in fact, interpretation may be difficult. It is in the same way when drawing scatter plots with your correlation data.

As a researcher, you design and carry out experiments for interesting questions. After data collecting and analyzing, you may fortunately find the interesting correlation between two variables. Now you can show your result to other people, for example, to publish you finding. Usually, we may draw a scatter plot with the raw data and show the relationship between two variables. This is a common practice. But it is not omnipotent, especially for studies with large sample size. In fact, scatterplots can get very hard to interpret when displaying large datasets, as points inevitably overplot and can’t be individually discerned. In addition, the readers’ belief about the relationship may be largely affected by some samples around most points in center.

So how can you show your results to make them easier to interpret for readers? A number of approaches have been crafted to help with these problems. One beautiful approach is using binning. One example is an article (Rand, 2012) published in Nature. The researcher showed a negative relationship between decision time and contribution with the binned scatter plot. Though the correlation r of the raw data is only ~0.15 (you could imagine how ugly the scatterplot with all points might be), the relationship between the two variables shown with a binned scatter plot, seems to be easier for people to interpret than a scatter plot. This is a great idea to show your correlation results to make your work easier to be published.

Of course, the method of show correlation is conditional. First, the raw correlation between the two variables must be significant. This is the premise. Second, it applies only to correlations based on large datasets. It is easy to think of this point.

As lately I have been focusing on correaltions between behaviral/neural data from a large dataset in my research, I have implemented a script in python to conveniently draw the binned scatter plot (I call it BSP).
