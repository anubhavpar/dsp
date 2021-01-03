[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

I have used the definition which is explained by the "rule of thumb" guidelines(https://stats.stackexchange.com/questions/469203/what-is-the-intuition-behind-cohens-d): 
* Small effect = 0.02 
* Medium effect = 0.5 
* Larget effect = 0.8 

def CohenEffectSize(group1, group2) :
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1,n2 = len(group1),len(group2)
    pooled_var = (n1* var1 + n2* var2)/(n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d 
    
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
diff_totalwgt = CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb)
diff_prglngth = CohenEffectSize(firsts.prglngth,others.prglngth)
diff_totalwgt

* Total Weight - The Cohen's d value is -0.088672927072602, which is small as per the definition stated above. This means that the means of the first born babies is not very far from the means of the others(Cohen's d indicates the number of standard deviations the two means differ from). The negative sign indicates that the mean of first borns < mean of the other kids.

* Pregnancy Length - 0.028879044654449883. As per the above definition, this difference is also small. 



