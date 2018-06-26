Volume-level Frequency Tables
-------------------------------

The data in this folder includes a dense representation of all books with words in the EF 2.0 release, presented as tables in the following format:

```
volume / token / count
```

Where
 - `volume` is a numeric id, mapped to a HathiTrust ID according to `./volume-id-key.gz`, and
 - `token` is a numeric id, mapped to words according to `../token-frequencies/wordlist.h5` and filtered to only include the 3.5m words in that list.

The integer ids are large but worth it, as the dataset is very small, despite using a fast-read/low-compression format called BLOSC.

The dataset is stored in PyTables HDF files, in a table called `/unigrams`. Here's one example of reading it using Pandas, with the `stop` argument used to only read the first 10k lines:

```python
import pandas as pd
df = pd.read_hdf('./counts.100.h5', '/unigrams', stop=10000)
df.head()
```

```
         token  count
id
8373841      0   1522
8373841      1   1072
8373841      2      4
8373841      3      2
8373841      5      1
```
