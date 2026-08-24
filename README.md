# paper-base

Canonical paper library as CSV, plus a weekly inbox so unreviewed alerts are not re-filtered.

## Files

| Path | Role |
|------|------|
| `paper-library.csv` | Reviewed library: `ID, Title, Topic(s), Summary, Link, DOI` |
| `inbox/pending.csv` | Current weekly proposal waiting for review |
| `inbox/snapshots/` | Dated copies of each weekly proposal (never overwritten) |
| `inbox/seen.csv` | Union of already proposed papers (DOI/title), so later runs skip them |

`paper-library.csv` is the source of truth after you edit and commit. Inbox files keep the last agent output even if you skip a week.

## Weekly flow

1. Monday 06:00 Europe/Madrid: read Gmail folder `Paper alerts`, rank against Zotero topics, append **new** papers only.
2. Write `inbox/pending.csv` and a snapshot; open a PR.
3. You edit `paper-library.csv` (merge keepers from pending) and commit.
4. After that commit on `main`, new rows are added to Zotero (DOI as duplicate key).
