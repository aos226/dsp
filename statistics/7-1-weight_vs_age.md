[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> Pearson's correlation is 0.20 and spearman's correlation is 0.14.

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
