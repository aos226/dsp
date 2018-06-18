[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

>> Assuming the income is on a log10 scale and that the upper bound is 6.0, the mean is 4.66, the median is 4.71, the skewness is -0.64, and the pearson's skewness is -0.34. About 45% of the households have an income below the mean. If the upper bound is increased, the percentage of households with an income below the mean increases. If the upper bound is decreased, the percentage of households with an income below the mean decreases. Below is my code.

```python
import hinc
import hinc2
import thinkstats2
import math

data = hinc.ReadData()
log_data = hinc2.InterpolateSample(data, log_upper=6.0)

def Median(xs):
    cdf = thinkstats2.Cdf(xs)
    return cdf.Value(0.5)

def RawMoment(xs, k):
    return sum(x**k for x in xs) / len(xs)

def CentralMoment(xs, k):
    mean = RawMoment(xs, 1)
    return sum((x - mean)**k for x in xs) / len(xs)

def StandardizedMoment(xs, k):
    var = CentralMoment(xs, 2)
    std = math.sqrt(var)
    return CentralMoment(xs, k) / std**k

def Skewness(xs):
    return StandardizedMoment(xs, 3)

def PearsonMedianSkewness(xs):
    median = Median(xs)
    mean = RawMoment(xs, 1)
    var = CentralMoment(xs, 2)
    std = math.sqrt(var)
    return 3 * (mean - median) / std

median = Median(log_data)
mean = RawMoment(log_data, 1)
skewness = Skewness(log_data)
pearson_skewness = PearsonMedianSkewness(log_data)

print('mean is', mean)
print('median is', median)
print('skewness is', skewness)
print("Pearson's skewness is", pearson_skewness)

cdf = thinkstats2.Cdf(log_data)
print('% of households below the mean is', cdf.Prob(mean))
```
