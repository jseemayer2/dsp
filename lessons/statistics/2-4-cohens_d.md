[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Using the code from ThinkStats2, Cohen's *d* was calculated to determine if "first-born's" were statisically significantly heavier or lighter than "other-born's":

```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
```

The code to solve the particular question is as follows:

```python
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
```

```python
-0.088672927072602
```

From this result we can conclude that first-born's are not statistically significantly heavier or lighter than their younger siblings, being less than 1/10th of 1 standard deviation different.
