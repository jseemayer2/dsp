[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```python
import scipy.stats
```

Using the problem statement to generate the normal distribution of the heights of men in the US:

```python
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
type(dist)
```
Using this distribution, we can find what amount of people lie between the required height restraint after converting the restraint to the compatible height of the distribution (cm):

```python
minht = (5 * 12 * 2.54) + (10 * 2.54)
maxht = (6 * 12 * 2.54) + (1 * 2.54)
print(minht, maxht)
```
```python
177.8 185.42
```
```python
#Take difference between cdf's of max and min to find portion inbetween
dist.cdf(maxht) - dist.cdf(minht)
```
```python
0.3427468376314737
```
**Roughly one-third of adult men in the US are elligible to try out for the Blue Men Group based on height.**
