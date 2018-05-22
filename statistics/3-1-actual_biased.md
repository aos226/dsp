[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> Below is my code for the exercise. The biased mean is 2.4 and the actual mean is 1.0, a rather large difference.


    import nsfg
    import thinkplot
    import thinkstats2

    resp = nsfg.ReadFemResp()

    pmf_actual = thinkstats2.Pmf(resp.numkdhh, label='actual')

    thinkplot.PrePlot(2, cols=2)
    thinkplot.Pmf(pmf_actual)
    thinkplot.Config(xlabel='number of childen', ylabel='PMF')

    pmf_biased = pmf_actual.Copy(label='observed (biased)')

    for x, p in pmf_actual.Items():
        pmf_biased.Mult(x, x)

    pmf_biased.Normalize()


    thinkplot.PrePlot(2)
    thinkplot.SubPlot(2)
    thinkplot.Pmfs([pmf_actual, pmf_biased])
    thinkplot.Config(xlabel='number of childen', ylabel='PMF')

    print('Actual mean number of children is', pmf_actual.Mean())
    print('Observed (biased) mean number of children is', pmf_biased.Mean())
