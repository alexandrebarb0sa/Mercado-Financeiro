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

# yahoo_fin

`````{tab-set}

````{tab-item} API
```{code-block} python
import yahoo_fin as yfin
```
````

````{tab-item} Install
```{code-block} bash
pip install yahoo-fin
```
````

```{tab-item} Docs
<i class="fab fa-github fa-2x"></i> https://github.com/atreadw1492/yahoo_fin <br>
<i class="fa fa-home fa-2x"></i> http://theautomatic.net/yahoo_fin-documentation/
```

```{tab-item} Data Source
Yahoo Finance: https://finance.yahoo.com
```

`````

```{code-cell}
:tags: ['remove-input']
import yahoo_fin as yfin
```

[yahoo_fin](http://theautomatic.net/yahoo_fin-documentation/) é uma biblioteca independente que realiza buscas na base de dados do [Yahoo Finance](https://finance.yahoo.com/).

# Live Price