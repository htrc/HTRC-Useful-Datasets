Volume-level Frequency Tables
-------------------------------
**data/*.h5**

The data in this folder includes a dense representation of all books with words in the EF 2.0 release, presented as tables in the following format:

```
volume / token / count
```

Where
 - `volume` is a numeric id, mapped to a HathiTrust ID according to `./volume-id-key.gz`, and
 - `token` is a numeric id, mapped to words according to `../token-frequencies/wordlist.h5` and filtered to only include the 3.5m words in that list.

The integer ids are an extra step but worth it for fast book-level processing, where reading EF files would be slow. The dataset is only about 250GB, compressed with a fast-read/low-compression format called BLOSC.

**Provenance**: Crunched on EF 2.0 in 2017.

**Sample File**: `./sample/sample.h5`

**Example Read in Python**

The dataset is stored in PyTables HDF files, in a table called `/unigrams`. Here's one example of reading it using Pandas:

```python
import pandas as pd
df = pd.read_hdf('sample.h5', '/unigrams')
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
