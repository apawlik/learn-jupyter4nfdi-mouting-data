# Read-only and read-write storage

A mount can allow both read and write access.

1) A **read-only** mount lets you access files without changing them. This is a good choice for source data that should not be modified during analysis.

2) A **read-write** mount allows programs in the Jupyter environment to create, modify and delete files on the mounted storage.
That can be useful, but it also means mistakes have consequences.

Remember that deleting files may sometimes not look "explicit" in the code. For example, the following will create a Path object referring to shared-results/important.csv, then delete that file (if the storage permissions allow it):

```python
from pathlib import Path

Path("shared-results/important.csv").unlink()
```

If you are allowed to create files in the mounted location, you can test write access from a terminal:

```bash
touch data/test-file.txt
```

If it succeeds, remove the test file:

```bash
rm data/test-file.txt
```

Do not do this on storage where creating test files would be inappropriate.
