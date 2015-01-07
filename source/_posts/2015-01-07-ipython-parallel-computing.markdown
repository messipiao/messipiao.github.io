---
layout: post
title: "IPython parallel Computing"
date: 2015-01-07 16:12
comments: true
categories: Programming
---

# Basic concepts

* Clent is a lightweight handle on all the engines of a cluster.
* Views provide the fundamental ways of accessing the clients. There are two types of views: Direct view and      load balanced view.

```python
from IPython import parallel
clients = parallel.Client()
dview = clients.direct_view()
lview = clients.load_balanced_view()
```

# Direct View

In a DirectView interface, we can either use Blocking (synchronous) execution, in which all results must finish computing before any results are recorded, 

```python
## one way
dview.block = True
dview.apply(some function)
## another way
dview.apply_sync(some function)
```
or non-blocking (asynchronous) execution, where we receive results as they finish.

```python
## one way
dview.block = False
dview.apply(some function)
## another way
dview.apply_async(some function)
```

To get the result in a blocking mode (synchronous) is quite straitforward, while things get complicated in the non-blocking (asynchronous) mode. 

```python
dview.block = False
dview.apply(some_function)
## the result should be <AsyncResult: some_function>
## In order to get the result res = dview.apply(some_function)
res.get()
## To check whether the excutation is over or not
res.ready()
```

It is noted that when you import some modules which excepected to be used in all the engines, you should put it in the function. For example, if we want to import *numpy*, we should put *import numpy* in the function. Alternatives ways can be 

```python
dview.execute('import numpy')
```
and 

```python
with dview.sync_imports():
    import numpy
```
If we use the IPython notebook, there is more convinient way by using magic function **%px**(parallel execute) to achieve it. 


We have shown above that function **apply()** is used to excute functions in the direct view interface. There are two other useful functions, i.e., **run()** and **excute()**. **run()** can be used to run scripts

```python
dview.run("myscript.py")
```

and **excute()** can be used to execute code directly on the engine by passing strings to the engines.

```python
## Suppose after running code, we have two variables a and b, then we can use dview['a'] to get the value of a
print dview['a'] 
print dview['b']
## excute code c=a+b
dview.execute('c=a+b')
```
We can also push or pull data by using **scatter()** and **gather**, which is useful if you had a larger computation that could be done on partitions of the data.

```python
dview.scatter('a', np.arange(24))
dview.gather('a')
```

# Load-balanced Views

A load-balanced view is a fault-tolerant way to distribute tasks among the engines. While there is no direct access to individual engines, it provides a simple and powerful interface.

```python
lview.block = True
lview.apply(some_function,par)
## We can use the map function to execute multiple inputs. We'll use block=False to make sure the results come asynchronously.
lview.block = False
res = lview.map(some_function,list_of_pars)
## check how many of the jobs have been completed
res.progress
## get the result
res.result
## another way to get the result
for result in lview.map(sleep_and_return, range(10)):
    print result
```

# Example: Monte Carlo $\pi$

* Without parallel

```python
from random import random
from math import pi

def mcpi(nsamples):
    s = 0
    for i in range(nsamples):
        x = random()
        y = random()
        if x*x + y*y <= 1:
            s+=1
    return 4.*s/nsamples
```

* Parallel

```python
def mcpi(nsamples):
    from random import random
    s = 0
    for i in xrange(nsamples):
        x = random()
        y = random()
        if x*x + y*y <= 1:
            s+=1
    return 4.*s/nsamples
    
def multi_mcpi(view, nsamples):
    p = len(view.targets)
    if nsamples % p:
        # ensure even divisibility
        nsamples += p - (nsamples%p)
    subsamples = nsamples/p
    ar = view.apply_async(mcpi, subsamples)
    return sum(ar)/p
```

We test the running time and found that it is almost 4 times fast with parallel computing.

