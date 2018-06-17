[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

>> The model difference doesn't have much of an effect for this example. Using a random seed of 1, the p-values for the prglngth are 0.177 and 0.178 using permutation and resampling respectively. The p-values for the totalwgt_lb are 0.0 and 0.0. Below is my code.

```python
import first
import hypothesis
import numpy as np
import thinkstats2

thinkstats2.RandomSeed(1)

class DiffMeansResample(hypothesis.DiffMeansPermute):
    
    def RunModel(self):
        sample1 = np.random.choice(self.pool, self.n, replace=True)
        sample2 = np.random.choice(self.pool, self.m, replace=True)
        return sample1, sample2

live, firsts, others = first.MakeFrames()
data = firsts.prglngth.values, others.prglngth.values
ht = hypothesis.DiffMeansPermute(data)
pvalue = ht.PValue()
ht2 = DiffMeansResample(data)
pvalue2 = ht2.PValue()
print('P-value for preglength by permute is', pvalue)
print('P-value for preglength by resample is', pvalue2)

data = firsts.totalwgt_lb.values, others.totalwgt_lb.values
ht = hypothesis.DiffMeansPermute(data)
pvalue = ht.PValue()
ht2 = DiffMeansResample(data)
pvalue2 = ht2.PValue()
print('P-value for birthweight by permute is', pvalue)
print('P-value for birthweight by resample is', pvalue2)
```
