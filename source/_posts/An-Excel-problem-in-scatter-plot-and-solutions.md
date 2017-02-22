---
title: An Excel problem in scatter plot and solutions
date: 2016-11-17 09:48:39
tags:
---
Can you imagine using Excel without plot or formulas? Recently I came this kind of problem when using the Excel 2016 on my office PC: Excel functions like SUM() did not work, and I could not get any plot as expected. A bunch of questions flash across my mind. Is it a bug of the new version of Excel? Is my Excel corrupt or is this due to some malicious virus? This might also be caused by the different language using in the system. After a few days' worry and search, here is the solutions to the problem I had, which might be helpful for others. 

First, make sure that your new system uses the same language. For example, in Dutch, people usually use comma(,) as the decimal point, rather than dot. For fixing this problem, you can change some setting options within Excel or directly at the system level. 

- Within Excel, you can find the place to make the change at File-->Options-->Advanced-->Editing options;
- At the system level, you can find the place at Language preferences-->Additional date, time, & regional settings-->Region (Change date, time, or number formats)-->Additional settings-->Customize Format. 

Second, if the problem is still there, you may need to make sure numbers in you data are not formatted as text values. In this case, numbers look like normal numbers, but Excel perceives them as text strings. That's another common reason for Excel formulas or plot not working. 

A potential visual indicator of text-numbers would be that numbers formatted as text are left-aligned by default, while normal numbers are right-aligned. There may be warning signs or green triangles appear in the top-left corner of the cells. 

- To fix this, select all problematic cells, click the warning sign, and then click "Convert to Number". Mostly this would work, but in some cases, you can not see any warning signs or green triangles. 
- In this situation, you can multiply the values in the problematic cells by 1 to convert the text to numbers. A useful fomula looks like this: = A1*1. Then you can paste the new values as values in a new place. 

The following link largely helps for fixing the issue:
[https://www.ablebits.com/office-addins-blog/2016/02/03/excel-formulas-not-working/](https://www.ablebits.com/office-addins-blog/2016/02/03/excel-formulas-not-working/)
