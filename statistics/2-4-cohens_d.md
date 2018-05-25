[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> Cohen's d between the total weight of first babies and other babies is about -0.089. This means that the two means are about 0.089 standard deviations away from each other. This is a little bigger than the Cohen's d between the pregnancy length of first babies and other babies, which was 0.029. My code is below.



    import first
    import math

    def WeightDiff(live, firsts, others):
        total_mean = live.totalwgt_lb.mean()
        firsts_mean = firsts.totalwgt_lb.mean()
        others_mean = others.totalwgt_lb.mean()

        print('Means')
        print('First babies', firsts_mean)
        print('Other babies', others_mean)

        firsts_var = firsts.totalwgt_lb.var()
        others_var = others.totalwgt_lb.var()

        print('Variance')
        print('First babies', firsts_var)
        print('Other babies', others_var)

        print('Difference in lbs', firsts_mean - others_mean)
        print('Difference in oz', (firsts_mean - others_mean) * 16)

        print('Difference relative to overall mean (%)', 
              (firsts_mean - others_mean) / total_mean * 100)

        n1 = len(firsts)
        n2 = len(others)

        pooled_var = (n1*firsts_var + n2*others_var) / (n1 + n2)

        d = (firsts_mean - others_mean) / math.sqrt(pooled_var)
        print("Cohen's d", d)


    def main(script):
        """Tests the functions in this module.

        script: string script name
        """
        live, firsts, others = first.MakeFrames()

        WeightDiff(live, firsts, others)


    if __name__ == '__main__':
        main(*sys.argv)
