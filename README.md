<img src="http://hilpisch.com/tpq_logo.png" alt="The Python Quants" width="35%" align="right" border="0"><br>

# Case Study

## Mean-Variance Portfolio Package

Dr. Yves J. Hilpisch

The Python Quants GmbH

<a href='http://tpq.io'>http://tpq.io</a> | <a href='mailto:training@tpq.io'>training@tpq.io</a>

## `mvportfolio`

`mvportfolio` is a simple Python package to analyze and manage investment portfolios according to the Mean-Variance Portfolio (MVP) theory.

<img src="http://hilpisch.com/images/finaince_visual_low.png" width="300px"> 

## Installation

### From Source 

Open a terminal an execute

    git clone http://github.com/yhilpisch/mvportfolio
    cd mvportfolio
    python setup.py install

### Via `pip` (from Github)

Open a terminal and execute

    pip install git+https://github.com/yhilpisch/mvportfolio

### Via `pip` (from PyPi)

Open a terminal and execute

    pip install --index-url https://test.pypi.org/simple/ mvportfolio

## First Steps

Some imports first.


```python
from pylab import plt
import mvportfolio as mvp
```


```python
plt.style.use('seaborn')
%matplotlib inline
```

Second, an **instance** of the main class `MVPPortfolio`.


```python
p = mvp.MVPPortfolio(['.SPX', '.VIX'], '2017-1-1', '2018-6-30')
```

Third, some **statistics** for the equal weights portfolio.


```python
p.weights
```




    [0.5, 0.5]




```python
p.portfolio_return()
```




    0.13792208996374847




```python
p.portfolio_volatility()
```




    0.6462235282900843



Fourth, the **minimum risk portfolio weights**.


```python
opt = p.minimum_risk_portfolio()
```


```python
opt['x']
```




    array([0.93891629, 0.06108371])



Fifth, **visualization** of the data.


```python
p.data.plot(figsize=(10, 6), secondary_y='.VIX');
```


    
![png](time_series.png)
    



```python
p.returns.plot.hist(figsize=(10, 6), bins=50, subplots=True);
```


    
![png](histogram.png)
    



```python
p.returns.corr()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
    
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>.SPX</th>
      <th>.VIX</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>.SPX</th>
      <td>1.000000</td>
      <td>-0.786778</td>
    </tr>
    <tr>
      <th>.VIX</th>
      <td>-0.786778</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



## Copyright & License

&copy; The Python Quants GmbH | MIT License.
