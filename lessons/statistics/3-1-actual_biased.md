[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

import nsfg
import thinkstats2
import thinkplot
def BiasPmf(pmf,label):
    new_pmf = pmf.Copy(label = label)
    for x, p in pmf.Items():
        new_pmf.Mult(x,x)
    new_pmf.Normalize()
    return new_pmf 
df = nsfg.ReadFemResp()
d = {}
d = df.numkdhh.value_counts()
d = d.to_dict()
d
pmf = thinkstats2.Pmf(d,label = 'actual') 
biased_pmf = BiasPmf(pmf, label = 'observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf,biased_pmf])
thinkplot.Show(xlabel = 'class size', ylabel = 'PMF')
print('Unbiased mean',pmf.Mean()) # calculate the Mean
print('Biased mean',biased_pmf.Mean()) # calculate the Mean 
