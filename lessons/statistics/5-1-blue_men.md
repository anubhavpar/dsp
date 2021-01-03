[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)
import brfss as br
import scipy
import math
df_bfss = br.ReadBrfss()
df_height = df_bfss['htm3']
height_mean = df_height.mean()
height_mean = 178
print(height_mean)
height_var = df_height.var()
#height_var = 7.7
height_std = math.sqrt(height_var)
height_std = 7.7
print(height_std)
percentage_diff = scipy.stats.norm(height_mean, height_std).cdf(185.4) - scipy.stats.norm(height_mean,height_std).cdf(177.8)
percentage_diff
