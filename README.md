# Anaconda channel catalog: main vs main-x

**This is not a source of truth.** It is a dated, regenerable citation of Anaconda's own sources — every figure carries the Anaconda URL it came from and the moment it was true. The sources of truth are anaconda.org and repo.anaconda.com; when in doubt, they're authoritative.

| File | Contents |
|---|---|
| `anaconda_channel_catalog.ipynb` | Notebook that (re)builds the catalog: integrity-checked fetches, refuses on truncation/partial data |
| `anaconda_channel_catalog.xlsx` | `main` (5,463 rows) · `main-x` (14,234 rows) · `Summary` (figures with source+date). Header line on top of each sheet (count, generation date, browse URL); autofilter on; sorted by downloads desc. |
| `download_counts_cache.json` | anaconda.org `ndownloads` cache for main (resume-safe) |

Sources (all Anaconda-published):
- main contents/summaries: `repo.anaconda.com/pkgs/main/channeldata.json`; downloads: `api.anaconda.org/package/anaconda/<name>` (98.6% coverage).
- main-x contents/versions/licenses: `repo.anaconda.cloud/repo/main-x/` (Bearer token); summaries + download counts: anaconda.org repocore API (the .org front-end's own public API), 99.2% summary coverage; a PyPI description fallback (exception-only, counted+dated on Summary) covers 5 more. Note: anaconda.org reports download_count = 0 for every main-x package as of 2026-08-17 (telemetry not populated for this channel yet; not zero usage — see Summary sheet).

Refresh: `ANACONDA_REPO_TOKEN=<token> jupyter nbconvert --execute anaconda_channel_catalog.ipynb` (needs pandas, openpyxl). Re-running automatically picks up real main-x download counts once .org populates them.
