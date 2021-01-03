[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

import numpy as np 
import thinkstats2
import thinkplot
import random

rnd_last = [] 
i = 0  
for i in range(1000): 
  rnd_last.append(random.random())
  i+= 1    
#print(len(rnd_last))
#sample = random.random(0,100)
random_cdf = thinkstats2.Cdf(rnd_last, label='random_nos')
#thinkplot.Cdf(random_cdf)
#thinkplot.Show(xlabel='random_nos', ylabel='CDF')
#rnd_list_int = [int(x) for x in rnd_last]
rnd_list_int = rnd_last.copy()
#print (rnd_list_int)
random_pmf = thinkstats2.Pmf(rnd_list_int)
print(random_pmf)
thinkplot.Pmf(random_pmf)
thinkplot.Show()