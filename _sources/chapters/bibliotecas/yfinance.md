---
jupytext:
  cell_metadata_filter: -all
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

{{ toc_libs }}

# yfinance

`````{tab-set}

````{tab-item} API
```{code-block} python
import yfinance as yf
```
````

````{tab-item} Install
```{code-block} bash
pip install yfinance --upgrade --no-cache-dir
```
````

```{tab-item} Docs
<i class="fab fa-github fa-2x"></i> https://github.com/ranaroussi/yfinance
```

```{tab-item} Data Source
Yahoo Finance: https://finance.yahoo.com
```

`````

```{code-cell}
:tags: ['remove-input']
import yfinance as yf
```

[yfinance](https://pypi.org/project/yfinance/) é uma biblioteca independente que realiza buscas na base de dados do [Yahoo Finance](https://finance.yahoo.com/).

## Yahoo URL Query

Esta seção mostra explicitamente a URL que a api da <font color='purple'> yahoo finance </font> faz a *query*.

```{code-cell} 
:tags: ['remove-input']
    from datetime import datetime
    import urllib.request
    from io import StringIO
    import pandas as pd
```

<font size=2>

```{code-cell}
    def yahoo_query(ticker,start,end='',interval="1d"):
        if end=='': end = datetime.now().strftime("%d/%m/%Y")
        date = {
            'format':"%d/%m/%Y, %H:%M:%S",
            'start':"{}, 04:00:00".format(start),
            'end':"{}, 04:00:00".format(end)
        }
        date['start'] = int(datetime.strptime(date['start'],date['format']).timestamp())
        date['end'] = int(datetime.strptime(date['end'],date['format']).timestamp())
        
        query = "https://query1.finance.yahoo.com/v7/finance/download/"
        period = "period1={}&period2={}&interval={}&events=history&includeAdjustedClose=true".format(date['start'],date['end'],interval)
        url = "{}{}?{}".format(query,ticker,period)
        
        with urllib.request.urlopen(url) as f:
            return pd.read_csv(StringIO(f.read().decode('utf-8')),sep=",")    
```

```{code-cell}
    magalu = yahoo_query("MGLU3.SA",start='02/05/2011')
    magalu.set_index('Date',inplace=True)
    print(magalu.head())
    magalu['Adj Close'].plot(rot=45);
```

</font>

## Métodos 

#### Ticker(*args, **kwargs)

O método `.Ticker()` reúne as principais informações da empresa sendo buscada.

```{code-cell}
    ticker = {'Coca-Cola':'KO'}
    stocks = dict()
```
