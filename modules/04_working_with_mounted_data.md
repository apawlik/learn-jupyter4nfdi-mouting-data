# Working with mounted data

Once storage is mounted, applications running inside the Jupyter environment can normally access it through the filesystem.
This means you can work with the data from Python, R, shell commands and other tools.

Suppose your storage is mounted under `data`.

```bash
ls data
```

If  you connect to an unfamiliar dataset for the first time, this is how you can explore it:

To see file sizes:

```bash
ls -lh data
```

To inspect files in subdirectories:

```bash
find data -maxdepth 2 -type f
```

Python does not need special syntax just because the file is on mounted storage.

If the mounted directory contains:

```text
data/example.csv
```

You can read the data as you would if it was stored in the same location:

```python
import pandas as pd

df = pd.read_csv("data/example.csv")
df.head()
```
You can inspect a directory with `pathlib`:

```python
from pathlib import Path

data_dir = Path("data")

for item in data_dir.iterdir():
    print(item)
```

**Note: Remote storage is still remote**

A mounted filesystem can look local, but it may still be accessed over a network. This matters for speed and performance.
Reading one moderate-sized file may be quick. Reading thousands of tiny files or repeatedly loading the same large file can be much slower.

Avoid code such as:

```python
for i in range(100):
    df = pd.read_csv("data/very-large-file.csv")
```

when the file can be loaded once:

```python
df = pd.read_csv("data/very-large-file.csv")

for i in range(100):
    # work with df
    pass
```

