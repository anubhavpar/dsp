[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

log_sample = InterpolateSample(df_new, log_upper=6.0)
print(log_sample)
sample = np.power(10, log_sample)
print(sample)
mean = sample.mean()
std = sample.std()
median = thinkstats2.Median(sample)
print('mean',mean)
print('std',std)
print('median',median)
print('skewness', thinkstats2.Skewness(sample))
print('pearson skewness', 
          thinkstats2.PearsonMedianSkewness(sample))
cdf = thinkstats2.Cdf(sample)
print('cdf[mean]', cdf[mean])

mean 74278.7075311872
std 93946.92996347835
median 51226.45447894046
skewness 4.949920244429583
pearson skewness 0.7361258019141782
cdf[mean] 0.660005879566872

Hence 66% percent of households report taxable income below the mean. 

As we increase the value of the upper_bound, the fraction of households increase. The possible reason could be that as we increase the upper_bound, the interpolation for the given sample set increases and hence more household values are covered. 
