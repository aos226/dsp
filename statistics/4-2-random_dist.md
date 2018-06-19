[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> The distribution is not quite uniform. It looks pretty close but the CDF is not a perfectly straight line and the PMF has some gaps that are bigger than others. Below are the two plots.


![](https://github.com/aos226/dsp/blob/master/img/exercise4_2_pmf.jpg)


![](https://github.com/aos226/dsp/blob/master/img/exercise4_2_cdf.jpg)

Below is the code.

```python
import numpy

import thinkstats2
import thinkplot

random_nums = numpy.random.random(1000)

pmf = thinkstats2.Pmf(random_nums)

thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Save(root='exercise4_2_pmf',
               formats=['jpg'],
               xlabel='numbers', ylabel='PMF')

cdf = thinkstats2.Cdf(random_nums)
thinkplot.Cdf(cdf)
thinkplot.Save(root='exercise4_2_cdf',
               formats=['jpg'],
               xlabel='numbers', ylabel='CDF')
```
