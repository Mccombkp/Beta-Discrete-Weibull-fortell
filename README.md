# Fortell in Python
A python function that is based off the streamlined R library[ Foretell](https://cran.r-project.org/web/packages/foretell/foretell.pdf). Included is a [bdw function](https://rdrr.io/cran/foretell/src/R/BdW.R) & [bg Function](https://rdrr.io/cran/foretell/man/BG.html) to project customer retention using [Fader and Hardie's method](http://brucehardie.com/papers/037/BdW_JIM_2018-01-10_rev.pdf) with Scipy.

# Beta Discrete Weibull Example:
```python
import pandas as pd
import numpy as np
import io


data_string = """
Day,Retention
0,     1.000000
1,     0.915227
2,     0.905325
3,     0.895019
4,     0.882389
5,     0.872285
6,     0.861069
7,     0.853087
8,     0.848237
9,     0.843387
10,    0.838537
11,    0.835708
12,    0.832070
13,    0.829039
14,    0.825099
15,    0.822572
16,    0.819440
17,    0.817217
18,    0.815298
"""

data = io.StringIO(data_string)
data = pd.read_csv(data, sep=",")
data['Retention'] = data['Retention'] *100

fortell_bdw(surv_value=round(data['Retention'][0:5]),h=18)
```

```
[100.0,
 92.193944554874,
 90.31175201855368,
 89.0225485516031,
 88.01390928844319,
 87.17405973206644,
 86.44868571718936,
 85.80684085120794,
 85.22904189196329,
 84.70214590181364,
 84.2168251270027,
 83.76619620410683,
 83.34501999389707,
 82.94920723304807,
 82.57549884659653,
 82.22125128571703,
 81.88428776811061,
 81.56279238315445,
 81.2552329457299,
 80.96030364954679]
 ```
