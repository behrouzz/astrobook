**Author:** [Behrouz Safari](https://behrouzz.github.io/)<br/>
**License:** [MIT](https://opensource.org/licenses/MIT)<br/>

# astrobook
*Educational tools for the astronomical book*


## Installation

Install the latest version:

    pip install astrobook

Requirements are *numpy*, *pandas*, and *requests*.


## Examples


```python
from astrobook import sql2df

# Retrieve data from SIMBAD
df = sql2df('SELECT TOP 10 main_id, ra, dec FROM basic', api='simbad')

# Retrieve data from VizieR
df = sql2df('SELECT objID, gmag, zsp FROM "V/154/sdss16"', api='vizier')

# Retrieve data from Gaia DR3
df = sql2df('SELECT TOP 10 source_id, ra, dec FROM gaiadr3.gaia_source', api='gaia')
```

### Get tables in a database

Here we get name, description and number of rows of tables from IRSA database


```python
from astrobook import sql2df

query = """
SELECT table_name, description, irsa_nrows
FROM TAP_SCHEMA.tables
WHERE irsa_nrows IS NOT NULL
ORDER BY irsa_nrows DESC
"""

df = sql2df(query, api='irsa')
```

### Get columns of a table

Let's get columns of the table *basic* from SIMBAD

```python
from astrobook import sql2df

query = """
SELECT column_name, description
FROM TAP_SCHEMA.columns
WHERE table_name='basic'
"""

df = sql2df(query, api='simbad')
```


See more at [behrouzz.github.io/astrodatascience](https://behrouzz.github.io/astrodatascience/)
