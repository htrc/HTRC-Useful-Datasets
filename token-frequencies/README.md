Token Frequency Datasets
--------------------------

## Sorted Term Frequencies for Each Language in the HathiTrust
**token-frequencies-by-language.h5**

A PyTables file where each table is a language shortcode (e.g. `/eng/`, `/fre`). The contents of each table are sorted term frequencies for that language.

**Sample data**:
 - Top 50k English: 'samples/token-frequencies-by-language_eng50k.txt'
 - Top 50k French: 'samples/token-frequencies-by-language_fre50k.txt'

**Provenance**: Crunched on EF 2.0 in early 2017.

**Example Read in Python**

```python
import pandas as pd
with pd.HDFStore('./token-frequencies-by-language.h5', mode='r') as store:
   # Zulu token data
   data = store['/zul']
```

`store.keys() will list all the language tables.


## A Good General Purpose Vocabulary List
**wordlist.h5** or **wordlist.tsv.gz**

The vocabulary used in HT+Bookworm, with 3.5 million words selected in order to include the top frequency words from all languages in the Hathitrust, with a longer tail for the most represented languages.

The H5 version of the dataset has a '/final' table and a '/fixes' table, the latter remapping words that should be counted as being the same. This is due to an issue in the EF 2.0 files where zero-width (effectively invisible) characters were saved with some words in Chinese, Japanese, Chinese.
