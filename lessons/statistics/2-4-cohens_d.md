[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)


This functon computes the Cohen effect size (was given in the book):


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

Compute the Cohen effect size for the difference in pregnancy length for first babies and others.


```python
CohenEffectSize(firsts.prglngth, others.prglngth)
```




    0.028879044654449883



d = 0.029

Difference in pregnancy lenght for first babies and others are trivial because d(Cohen Effect Size) < 0.2

## Exercises

Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. 

Compute Cohen’s effect size to quantify the difference between the groups.  How does it compare to the difference in pregnancy length?


```python
CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
```




    -0.088672927072602



## Solution

d = -0.089


Cohen Effect is negative what means first babies are usually lighter than other. But because absolute value of d < 0.2, effect size is small.

Difference in weight between first and other babies is trivial
