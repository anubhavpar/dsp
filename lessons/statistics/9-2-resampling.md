[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

from __future__ import print_function, division

import first
import hypothesis
import scatter
import thinkstats2

import numpy as np

class DiffMeansResample(hypothesis.DiffMeansPermute):
    """Tests a difference in means using resampling."""
    
    def RunModel(self):
        """Run the model of the null hypothesis.

        returns: simulated data
        """
        group1 = np.random.choice(self.pool, self.n, replace=True)
        group2 = np.random.choice(self.pool, self.m, replace=True)
        return group1, group2

def RunResampleTest(firsts, others):
    """Tests differences in means by resampling.

    firsts: DataFrame
    others: DataFrame
    """
    data = firsts.prglngth.values, others.prglngth.values
    ht = DiffMeansResample(data)
    p_value = ht.PValue(iters=10000)
    print('\nmeans permute preglength')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())

    data = (firsts.totalwgt_lb.dropna().values,
            others.totalwgt_lb.dropna().values)
    ht = hypothesis.DiffMeansPermute(data)
    p_value = ht.PValue(iters=10000)
    print('\nmeans permute birthweight')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())

def main():
    thinkstats2.RandomSeed(18)

    live, firsts, others = first.MakeFrames()
    RunResampleTest(firsts, others)
    
if __name__ == '__main__':
    main()
    
Results:

means permute preglength p-value = 0.1674 actual = 0.0780372667775 ts max = 0.226752436104

means permute birthweight p-value = 0.0 actual = 0.124761184535 ts max = 0.112243501197

Conclusions: Using resampling instead of permutation has very little effect on the results.