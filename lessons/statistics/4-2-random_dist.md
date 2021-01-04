[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```python
%matplotlib inline

import numpy as np


import thinkstats2
import thinkplot
```
```python
random = np.random.random(1000)

pmf = thinkstats2.Pmf(random)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Config(xlabel='Number', ylabel='PMF')
```
![Graph of random.random PMF](https://github.com/jseemayer2/dsp/blob/master/lessons/statistics/images/Ch4-1_RandomPMF.png)

This illsutrates how the random number generator is good, but not perfect as shown by gaps and darker lines within the distribution,

```python
thinkplot.Cdf(thinkstats2.Cdf(random, label='random'))
thinkplot.Config(xlabel='Number', ylabel='CDF')
```
![Graph of random.random CDF](https://github.com/jseemayer2/dsp/blob/master/lessons/statistics/images/Ch4-1_RandomCDF.png)

This graphs also shows how the random number generator is good, but not perfect as shown by the slight deviations from the y=x line.
