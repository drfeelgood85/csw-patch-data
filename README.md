# csw-patch-data

Curator-maintained Microsoft patch recommendations consumed by
[CSW-Vulnerability-Scanner](https://github.com/drfeelgood85/CSW-Vulnerability-Scanner).

## What this repo is

A single source of truth for the `patch_data.json` file the scanner uses to
render its **Recommended Patches** dashboard. Every deployed scanner can be
configured to auto-fetch the latest version of this file from GitHub on a
schedule (default: every 7 days), so customers always see current patch
guidance without needing an application release.

## Files

| File | Purpose |
|------|---------|
| `patch_data.json` | The data. Hand-curated each Patch Tuesday week. |
| `patch_data.schema.json` | JSON Schema for validation. CI enforces this on every push. |
| `CHANGELOG.md` | Human-readable record of every refresh. |

## Consuming this data

Direct (always-latest):

```
https://raw.githubusercontent.com/drfeelgood85/csw-patch-data/main/patch_data.json
```

Pinned to a release tag (recommended for change-controlled environments):

```
https://raw.githubusercontent.com/drfeelgood85/csw-patch-data/<TAG>/patch_data.json
```

The scanner supports both modes via the `PATCH_DATA_URL` and
`PATCH_DATA_VERSION` environment variables.

## Curation workflow

Updates are produced by running the curator script in the
CSW-Vulnerability-Scanner repo:

```bash
python scripts/refresh_patch_data.py
```

The script fetches the latest MSRC CVRF documents, proposes updates while
preserving curator-only fields (custom warnings, alternatives, action text),
shows a diff, and on approval commits + pushes to this repo.

## Schema rules

- Top-level keys are product identifiers (free-form, but kept stable across
  refreshes — e.g. `msserver2019standard`).
- Each recommendation must include: `label`, `target`, `kb`, `date`, `url`,
  `action`. `warning` is optional (`null` allowed).
- `alternatives` is an optional array of related recommendations (OOB
  updates, security-only patches, WSUS catalog links, migration targets).
- See `patch_data.schema.json` for the formal contract.

## Release tags

Tagged after each refresh: `YYYY.MM.DD` (e.g. `2026.06.10` for the day after
the June 2026 Patch Tuesday).

## License

Data is distilled from publicly available Microsoft sources (MSRC, support.microsoft.com,
Update Catalog). No proprietary content.
