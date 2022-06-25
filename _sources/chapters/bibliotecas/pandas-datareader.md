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

# Pandas Datareader


`````{tab-set}

````{tab-item} API
```{code-block} python
import pandas_datareader as pdr
```
````

````{tab-item} Install
```{code-block} bash
pip install pandas-datareader
```
````

```{tab-item} Docs
Link: https://pandas-datareader.readthedocs.io/en/latest/
```

```{tab-item} Data Source
Link: https://pandas-datareader.readthedocs.io/en/latest/remote_data.html/
```

`````

```{code-cell}
:tags: ['remove-input']
import pandas_datareader as pdr
```


```{code-cell}
stocks = dict()

stocks['COGN3'] = pdr.DataReader('COGN3.SA', data_source='yahoo', start='2021-01-01')
print(stocks['COGN3'])

```

