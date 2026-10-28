# Changelog

Notable changes to this dataset. Versions follow MAJOR.MINOR.PATCH: MAJOR for schema changes,
MINOR for appended data, PATCH for corrections.

## 1.1.0 — 2026-10-28

First published release. Adds 116 draws recorded since the 1.0.0 snapshot.

- 17,850 records, 5 markets, 2020-01-01 to 2026-10-28.
- Coverage end per market: SG 2026-10-26 (no draw on Tuesdays), HK 2026-10-27,
  SDY 2026-10-27, MC 2026-10-28 (partial day: only the 00:01 session present),
  CAM 2026-10-27.
- 1,883 results begin with a zero. `result` remains a string in every file.
- No new gaps. The four known gaps are unchanged.
- 1 record still withheld: SG 2023-10-23 17:45 (archives disagree).
- Schema unchanged, so existing readers keep working.

## 1.0.0 — 2026-10-22

Built but never published; superseded by 1.1.0 before any release was made public.
Recorded here because other documents cite these figures.

- 17,734 records, 5 markets, 2020-01-01 to 2026-10-16.
- 1 record withheld: SG 2023-10-23 17:45 (sources disagree).
