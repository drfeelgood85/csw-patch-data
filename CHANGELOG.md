# Changelog

All notable changes to `patch_data.json` are documented here.

Format: `YYYY-MM-DD` — short summary of what changed and why.

## 2026-06-02 — May 2026 Patch Tuesday refresh

- Refreshed all 8 Windows / .NET / SQL entries to **May 12, 2026** KBs.
- Windows Server 2019: KB5082123 → **KB5087538** (build 17763.8755).
- Windows Server 2016: KB5082198 → **KB5087537** (build 14393.9140).
- Windows Server 2022: KB5082142 → **KB5087545** (build 20348.5139).
- Windows Server 2012 R2 (ESU): KB5082126 → **KB5087471** (Monthly Rollup).
- SQL Server 2019: KB5084816 → **KB5090407** (CU32 + GDR, build 15.0.4470.1) / GDR-only **KB5090408** (build 15.0.2170.1).
- SQL Server 2017: KB5084818 → **KB5090354** (CU31 + GDR, build 14.0.3530.2) / GDR-only **KB5090347** (build 14.0.2110.2).
- SQL Server 2016: KB5084821 → **KB5089271** (SP3 GDR, build 13.0.6490.1).
- .NET Framework: April Servicing Update → **May 2026 Cumulative Update** (per-OS KB; KB5087059 for Server 2022, KB5088861 for Server 2012 R2). Addresses CVE-2026-32177 (Elevation of Privilege).
- IE entry unchanged (permanently retired).
- Removed April 19, 2026 OOB alternatives (LSASS/PAM fix) — they are now superseded by May 12 cumulatives.
- Added "Apr 2026 CU" rollback alternatives on Windows Server entries.
- Sources: Microsoft Support KB articles, Microsoft Update Catalog, .NET release notes for May 2026.

## 2026-06-02 — Initial seed

- Seeded from CSW-Vulnerability-Scanner repo (commit baseline).
- Covers:
  - Windows Server 2012 R2 / 2016 / 2019 / 2022
  - .NET Framework
  - SQL Server 2016 / 2017 / 2019
  - Internet Explorer (EOL guidance)
- Reflects April 14, 2026 Patch Tuesday + April 19, 2026 OOB updates.
- **Pending refresh:** May 12, 2026 and June 9, 2026 Patch Tuesdays.
