[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This functon computes the Cohen effect size (was given in the book):"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 44,
   "metadata": {},
   "outputs": [],
   "source": [
    "def CohenEffectSize(group1, group2):\n",
    "    \"\"\"Computes Cohen's effect size for two groups.\n",
    "    \n",
    "    group1: Series or DataFrame\n",
    "    group2: Series or DataFrame\n",
    "    \n",
    "    returns: float if the arguments are Series;\n",
    "             Series if the arguments are DataFrames\n",
    "    \"\"\"\n",
    "    diff = group1.mean() - group2.mean()\n",
    "\n",
    "    var1 = group1.var()\n",
    "    var2 = group2.var()\n",
    "    n1, n2 = len(group1), len(group2)\n",
    "\n",
    "    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)\n",
    "    d = diff / np.sqrt(pooled_var)\n",
    "    return d"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Compute the Cohen effect size for the difference in pregnancy length for first babies and others."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 56,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.028879044654449883"
      ]
     },
     "execution_count": 56,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "CohenEffectSize(firsts.prglngth, others.prglngth)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "d = 0.029\n",
    "\n",
    "Difference in pregnancy lenght for first babies and others are trivial because d(Cohen Effect Size) < 0.2"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "collapsed": true
   },
   "source": [
    "## Exercises"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. \n",
    "\n",
    "Compute Cohen’s effect size to quantify the difference between the groups.  How does it compare to the difference in pregnancy length?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "-0.088672927072602"
      ]
     },
     "execution_count": 46,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Solution"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "d = -0.089\n",
    "\n",
    "\n",
    "Cohen Effect is negative what means first babies are usually lighter than other. But because absolute value of d < 0.2, effect size is small.\n",
    "\n",
    "Difference in weight between first and other babies is trivial"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 1
}
