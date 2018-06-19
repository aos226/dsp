[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> The scatter plot shows a weak relationship between the birth weight and age of mother. Pearson's correlation is 0.069 and spearman's correlation is 0.095. The difference between these two indicates that there may be some influence of outliers or that the relationship is nonlinear. The plot of weight percentiles versus age indicates that the relationship is nonlinear. Between ages 17 and 27.5, birthweight increases more quickly. After that, the weights either stay relatively flat or increase at a slower rate.

![](https://github.com/aos226/dsp/blob/master/img/exercise7_1_scatter.jpg)

![](img/exercise7_1_percentiles.jpg?raw=true)

```python
import nsfg
import thinkstats2
import thinkplot
import numpy as np
import pandas as pd

df = nsfg.ReadFemPreg()
df = df.dropna(subset=['totalwgt_lb', 'agepreg'])
weights, ages = df.totalwgt_lb, df.agepreg

thinkplot.PrePlot(cols=2)
thinkplot.Scatter(ages, weights)
thinkplot.Show(xlabel='age',
               ylabel='weights')

thinkplot.SubPlot(2)
bins = np.arange(10, 45, 5)
indices = np.digitize(df.agepreg, bins)
groups = df.groupby(indices)

weights = [group.totalwgt_lb.mean() for i, group in groups]
cdfs = [thinkstats2.Cdf(group.agepreg) for i, group in groups]
for percent in [75, 50, 25]:
    ages = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    thinkplot.Plot(ages, weights, label=label)
thinkplot.Show(xlabel='weights',
               ylabel='age')

pearson = thinkstats2.Corr(ages, weights)
spearman = thinkstats2.SpearmanCorr(ages, weights)

print("Pearson's correlation is", pearson)
print("Spearman's correlation is", spearman)
```
