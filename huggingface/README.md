---
license: cc-by-4.0
language:
- en
pretty_name: RajaHasil 4D Results Archive
size_categories:
- 10K<n<100K
tags:
- lottery
- lottery-results
- 4-digit
- time-series
- archive
- asia
- hong-kong
- singapore
- sydney
- macau
- cambodia
configs:
- config_name: default
  data_files:
  - split: train
    path: data/draws.csv
dataset_info:
  features:
  - name: market
    dtype: string
  - name: draw_type
    dtype: string
  - name: draw_date
    dtype: string
  - name: session
    dtype: string
  - name: session_timezone
    dtype: string
  - name: result
    dtype: string
---

# RajaHasil 4D Results Archive

Version 1.1.0, released 2026-10-28. 17,850 records across 5 markets, 2020-01-01 to 2026-10-28.

Unofficial compilation from public archives. It is not an operator's record.

## Reading `result` correctly

`result` is a four-character string. 1,883 values begin with a zero, so reading the column as a number silently corrupts them (`0678` becomes `678`). The `features` block in this card declares every column as `string` for exactly that reason; keep it if you re-upload.

```python
from datasets import load_dataset

ds = load_dataset("RajaHasil/Togel", split="train")
assert isinstance(ds[0]["result"], str)
```

## About `session`

`session` is a time label in WIB (Asia/Jakarta) as published by the source archives. It is not a verified timestamp and not the market's local time, and it is never converted. Per-market notes are in `data/index.json`.

## Coverage and gaps

| Market | Code | Records | First | Last |
|---|---|---|---|---|
| Singapore | `SG` | 1,723 | 2020-01-01 | 2026-10-26 |
| Hong Kong | `HK` | 2,492 | 2020-01-01 | 2026-10-27 |
| Sydney | `SDY` | 2,126 | 2021-01-01 | 2026-10-27 |
| Toto Macau | `MC` | 9,017 | 2021-01-01 | 2026-10-28 |
| Cambodia | `CAM` | 2,492 | 2020-01-01 | 2026-10-27 |

Known gaps are listed in `data/index.json`. One record is withheld because the source archives disagree on it; the reason travels with the data rather than being silently filled in.

## License and attribution

Creative Commons Attribution 4.0 International (https://creativecommons.org/licenses/by/4.0/).

> Data: RajaHasil 4D Results Archive, https://rajahasil.co/data/ (CC BY 4.0)

Documentation and canonical copy: https://rajahasil.co/data/
