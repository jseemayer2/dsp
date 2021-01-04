[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

Here's the code used to solve the exercise:

```python
resp = nsfg.ReadFemResp()

pmf = thinkstats2.Pmf(resp.numkdhh, label='observed')

thinkplot.Pmf(pmf)
```
Which generates the following plot:

INSERT GRAPH

This PMF shows that most respondent's had no kids, which would have biased our results in the following way had the survey been taken from the children's perspective:

```python
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
```

```python
biased_pmf = BiasPmf(pmf, label='biased')

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Config(xlabel='Kids per Household', ylabel='PMF')
```

Generating the following plot:

INSERT GRAPH

Using these 2 different data sets yields the following means:

```python
print('Observed mean:', pmf.Mean())
print('Biased mean:', biased_pmf.Mean())
```
```python
Observed mean: 1.024205155043831
Biased mean: 2.403679100664282
```

This illustrates how keeping bias in mind when doing data analysis is critical to getting meaningful and real results.
