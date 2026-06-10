# Changelog

All notable changes to `patch_data.json` are documented here.

Format: `YYYY-MM-DD` — short summary of what changed and why.

## 2026-06-10 — Add SQL Server 2022 / 2025; June 2026 no-update notes

- **Added SQL Server 2022** entry: primary CU24 + GDR (KB5089900, build 16.0.4252.3, May 12, 2026); GDR-only alternative KB5091158 (build 16.0.1180.1); April 2026 CU24+GDR (KB5083252) rollback. Mainstream support until Jan 11, 2028.
- **Added SQL Server 2025** entry: primary CU4 + GDR (KB5089899, build 17.0.4040.1, May 12, 2026); GDR-only alternative KB5091223 (build 17.0.1115.1); April 2026 CU3+GDR (KB5083245) rollback. GA Nov 2025 — young product on monthly CU cadence.
- Added "Reviewed Jun 10, 2026: no June 2026 update from Microsoft this cycle — May KBs remain current." note to **.NET Framework**, **SQL Server 2019**, **SQL Server 2017**, **SQL Server 2016** entries to make the verification explicit for operators.
- Total entries: 9 → **11**.
- Sources for SQL 2022/2025: learn.microsoft.com SQL Server build-versions tables, individual support.microsoft.com KB articles for KB5089900 / KB5091158 / KB5089899 / KB5091223 (all verified against authoritative MS sources).
- Confirmation that no .NET Framework June 2026 update exists: devblogs.microsoft.com .NET June 2026 servicing post explicitly states "no new security or non-security updates available this month"; June CVEs apply to modern .NET (10/9/8), not .NET Framework 4.x.
- Confirmation that no SQL Server June 2026 update exists: learn.microsoft.com "latest updates" page shows May 12, 2026 as most recent for all versions; Microsoft Update Catalog `2026-06 SQL Server` returns zero results; only "SQL"-adjacent June CVE was CVE-2026-47292 (VS Code MSSQL extension, not engine).

## 2026-06-10 — June 2026 Patch Tuesday refresh

- Refreshed 4 Windows Server entries to **June 9, 2026** KBs.
- Windows Server 2019: KB5087538 → **KB5094123** (build 17763.8880).
- Windows Server 2016: KB5087537 → **KB5094122** (build 14393.9234).
- Windows Server 2022: KB5087545 → **KB5094128** (build 20348.5256).
- Windows Server 2012 R2 (ESU): KB5087471 → **KB5094041** (Monthly Rollup). 4 ESU rollups remaining before October 13, 2026 final EOL.
- Promoted previous "Apr 2026 CU" rollback alternatives to **"May 2026 CU"** rollbacks on each updated entry.
- Updated WSUS Catalog search URLs to point to new June KBs.
- **.NET Framework**: unchanged. June 2026 .NET cumulative update not yet indexed in Microsoft Update Catalog as of 2026-06-10 morning; CVEs (CVE-2026-45491 / -45490 / -45591) per Tenable bulletin likely delivered inside OS LCUs. Will refresh once standalone .NET KBs are published.
- **SQL Server**: unchanged. June 2026 SQL Server GDR/CU KBs not yet indexed in Microsoft Update Catalog; Talos bulletin flags SQL Server RCEs but no standalone KB has appeared yet. Will refresh once published.
- IE entry unchanged (permanently retired).
- Sources: Microsoft Support KB articles for KB5094123 / KB5094128 / KB5094125 / KB5094041; BigFix MS26-JUN content release; Tenable June 2026 Patch Tuesday bulletin.

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
