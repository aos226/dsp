[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> About 34% of men in the US are in this range. My code is below.

```python
import scipy

bottom_cdf = scipy.stats.norm.cdf(177.8, loc=178, scale=7.7)
top_cdf = scipy.stats.norm.cdf(185.42, loc=178, scale=7.7)

top_cdf - bottom_cdf
```
