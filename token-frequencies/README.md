Token Frequency Datasets
--------------------------

## token-frequencies-by-language.h5

A PyTables file where each table is a language shortcode (e.g. `/eng/`, `/fre`). The contents of each table are sorted term frequencies for that language.

**Sample data**:
 - Top 50k English: 'samples/token-frequencies-by-language_eng50k.txt'
 - Top 50k French: 'samples/token-frequencies-by-language_fre50k.txt'

**Example Read in Python**

```python
import pandas as pd
with pd.HDFStore('./token-frequencies-by-language.h5', mode='r') as store:
   # Zulu token data
   data = store['/zul']
```

`store.keys() will list all the language tables.
