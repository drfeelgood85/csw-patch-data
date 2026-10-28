# Changelog

All notable changes to `patch_data.json` are documented here.

Format: `YYYY-MM-DD` — short summary of what changed and why.

## 2026-10-28 — October 2026 Patch Tuesday refresh

- **Scope:** Windows Server 2012 R2 / 2016 / 2019 / 2022 / 2025, SQL Server 2016 / 2017 / 2019 / 2022 / 2025 and .NET Framework. The Internet Explorer entry is unchanged.
- **Release data:** MSRC CVRF `2026-Oct` — status Final, initial release 2026-10-13, current release 2026-10-28. Every KB refreshed below is dated **October 13, 2026** (Patch Tuesday) per its support.microsoft.com page (the one exception is SQL Server 2016, for which no newer update was listed as of October 28, 2026 — see below); the CVRF `CurrentReleaseDate` (2026-10-28) is a later revision and is not used for the human-readable `date`. No September 2026 refresh was recorded in this repo, so the Windows entries move directly from the August 11, 2026 baseline and the SQL entries from the July 14, 2026 baseline.
- Windows Server 2019: KB5120238 → **KB5126651** (build 17763.9376, target `1809-17763.9376`). The KB lists a prerequisite: the latest Windows update released on or after July 8, 2025 (for example KB5062557).
- Windows Server 2016: KB5120418 → **KB5126868** (build 14393.9612).
- Windows Server 2022: KB5120242 → **KB5126655** (build 20348.5761).
- Windows Server 2025: KB5120233 → **KB5126646** (build 26100.33650).
- Windows Server 2012 R2 (ESU): KB5120385 → **KB5126836** (Monthly Rollup; SSU KB5127356), documented as the final ESU update. **Build number intentionally omitted:** no new 6.3.9600.x build was verified, so `target` is the digit-free string `Monthly Rollup (ESU; build not verified)` rather than a stale or guessed build; the real KB stays in `kb`, `action` and `url`. The target is deliberately digit-free because the dashboard's fix-scenario parser (`parseVerParts` in `static/js/patches.js`) reads the first number in a target as a version, so a KB number in the target would be compared against fleet builds; with no digits the parser returns null and the dashboard shows "Could not parse…" instead of a fake comparison.
- Windows Server 2012 R2 "Security-Only" alternative — **slot preserved, unverified suggestion replaced by an explicit caveat:** the previous entry pointed operators to an August 2026 Update Catalog search for a Security-Only update that had not been verified. No October 2026 Security-Only KB was verified, so the slot and its label are kept (alternatives count and order are unchanged) and its content now says exactly that: `target` "No verified Security-Only package" (digit-free for the same parser reason; the October 2026 date stays in `date` and `action`), `kb` "N/A — use verified Monthly Rollup", `date` "Reviewed October 28, 2026", `url` = the verified KB5126836 Monthly Rollup page, with an action that points to the Monthly Rollup and a warning that this entry is not an installable patch. This is a statement about what was verified, not a conclusion about whether a Security-Only package exists for this ESU cycle. The Microsoft ESU FAQ (linked under sources) is cited only because it is silent about update packaging; that silence is not evidence either way. No KB was invented.
- SQL Server 2019: KB5102335 → **KB5128494** (CU32 + GDR, build 15.0.4500.2); GDR-only alternative KB5102336 → **KB5128495** (build 15.0.2200.2). The previous primary `url` (`/help/5096773`) did not match its listed KB number and is replaced by the KB5128494 article URL.
- SQL Server 2017: KB5102337 → **KB5128496** (CU31 + GDR, build 14.0.3560.2); GDR-only alternative KB5102338 → **KB5128497** (build 14.0.2140.2).
- SQL Server 2022: KB5101347 → **KB5126934** (CU27 + GDR, build 16.0.4305.5); GDR-only alternative KB5102334 → **KB5128493** (build 16.0.1210.3). The primary action no longer states the CU25 release date (May 20, 2026), which does not apply to CU27 and was not re-verified.
- SQL Server 2025: KB5101346 → **KB5126967** (CU9 + GDR, build 17.0.5015.4); GDR-only alternative KB5102333 → **KB5128492** (build 17.0.1145.4). **Security baseline decision:** the recommended primary is the CU9 + GDR security update, not CU10.
- SQL Server 2016: **no newer SQL Server 2016 security update was listed in Microsoft's official latest-updates table as of October 28, 2026**, so the primary stays on KB5102340 (July 14, 2026). Updates to this entry: build 13.0.6505.1 → **13.0.6500.1**, the primary link now points to the SQL Server 2016 GDR article for KB5102340 (previously a bare `/help/5102340` link), and the primary warning now carries the MSDASQL known-issue caution (see below). The "Azure Connect FP" alternative (KB5102339, July 14, 2026, build 13.0.7095.1; applies only where the Azure Connect Feature Pack is installed) previously linked to `/help/5096777`, which did not match KB5102339; it now links to the KB5102339 article.
- On SQL Server 2017 / 2019 / 2022 / 2025 the CU + GDR primary vs GDR-only alternative distinction is preserved, and each GDR-only alternative `target` now also carries its verified GDR build. SQL Server 2016 is on the SP3 GDR branch with no CU primary, so that distinction does not apply to it.
- **.NET Framework:** refreshed to the **October 13, 2026** cumulative update. The main `url` is now the canonical release notes page (`https://learn.microsoft.com/en-us/dotnet/framework/release-notes/2026/10-13-october-cumulative-update`, which gives a release date of October 13, 2026) instead of the MSRC `2026-Aug` release note. Per-OS KBs: Server 2025 **KB5127690** (3.5 + 4.8.1), Server 2022 **KB5127693** (3.5 + 4.8.1), Server 2019 **KB5127685** (3.5 + 4.8), Server 2016 **KB5127684** (4.8), Server 2012 R2 **KB5127668 / KB5127688** (.NET 4.6.2 / 4.7.x and .NET 4.8). The Server 2012 R2 alternative lists both KBs and links the .NET 4.8 package (KB5127688), following the existing convention; the KB5127668 page (.NET 4.6.2 / 4.7 / 4.7.1 / 4.7.2) is cited under sources. The .NET pages list no known issues, so no known-issue caution was added.
- WSUS Catalog alternatives: Server 2016 / 2022 / 2025 are updated to the October KB, date and Update Catalog search URL. The Server 2019 alternative intentionally keeps its generic `target` / `kb` / `date` ("Latest approved in WSUS" / "Via WSUS approval" / "Per approval cycle"); only its search URL changed (to KB5126651).
- **Alternatives count and order are unchanged** on every entry.
- **Historic rollback alternatives ("Jul 2026 CU" on Server 2019 / 2016 / 2022; "May 2026 CU + GDR" on SQL Server 2022 / 2025):** label, target, KB, date and URL are deliberately left at their July 14, 2026 / May 12, 2026 values and were **not re-verified in this refresh**. Only their action and warning text changed: the action now says to use the older update as a temporary rollback if the October 2026 update causes issues, and the warning states that pinning to the older update leaves newer security fixes, including October 2026 (and July 2026 for the SQL May targets), unpatched. They are kept only as stale, temporary rollback options, not as current recommendations.
- **Curator-only text (`warning` / `action`) changed on explicit curator approval**, to correct stale or inaccurate statements:
  - Exchange known-issue caution added to the Server 2016 / 2019 / 2022 / 2025 primary warnings: the October KBs document OWA/mail problems on Exchange Server hosts. The text only tells operators to check the KB known issues before deploying on Exchange hosts (no workaround or registry steps).
  - Server 2012 R2 primary warning: the October 13, 2026 final EOL date has been reached and KB5126836 is the final ESU update (icon changed to 🚫; the `EOL` wording is kept so the dashboard still renders it as critical). Its "Migrate → 2022" alternative is reworded to "Plan migration to Windows Server 2022 …" (drops the past-deadline "before October 2026 EOL") and its warning now reads "Final EOL reached".
  - Server 2016 "Migrate → 2022" alternative: removed the incorrect "mainstream support until Oct 2031" claim. Windows Server 2022 moved from mainstream to extended support in October 2026, and security updates continue through October 2031 (month/year only).
  - Server 2022 primary warning: the same approved lifecycle correction now also appears on the Server 2022 card itself — "Mainstream support ended October 2026; extended support security updates continue through October 2031." (month/year only), per the Windows Server 2022 lifecycle page.
  - Server 2016 lifecycle warnings (primary and "Migrate → 2022"): "mainstream support ends January 2027" is corrected to "mainstream support ended January 2022; extended support ends January 2027", per the Windows Server 2016 lifecycle page (month/year only, which avoids UTC day offsets).
  - Windows Server 2012 R2 "Security-Only" alternative: all fields rewritten as described above (explicit caveat only; its warning no longer contains `EOL`, so the dashboard now renders it as a standard warning instead of critical).
  - Windows primary actions: the per-KB "(supersedes KB…)" clauses are replaced by a generic "cumulative; supersedes earlier monthly updates" note, because naming a single superseded KB would be unverified (this repo skipped September 2026).
  - SQL Server 2016 / 2017 / 2019 / 2022 / 2025 warnings: added the known issues documented on the KB pages (the October pages for 2017 / 2019 / 2022 / 2025, and the July 14, 2026 KB5102340 page for SQL Server 2016, whose "Known issues in this update" section lists the same item). Linked-server queries through MSDASQL can fail with error 7416 (the primary on all five versions; the GDR-only alternative on 2017 / 2019 / 2022 / 2025). An access violation can occur when querying `sys.dm_exec_requests` during database recovery (SQL Server 2022 CU27 and SQL Server 2025 CU9 primaries only; the GDR pages do not list it, so the GDR-only alternatives do not carry it). Each caution tells operators to review the KB and test before deploying; no mitigations are embedded. The SQL Server 2016 Azure Connect Feature Pack alternative (KB5102339) is not assumed to be affected and carries no caution.
  - SQL Server 2025 primary action: the inherited "Apply CU9 first if not yet on CU9, then layer the October 2026 GDR" requirement is removed because the KB does not support it — its prerequisite reads "you must have SQL Server 2025 or any SQL Server 2025 CU release through this SQL Server 2025 CU9 GDR installed." The action now says to install CU9 + October 2026 GDR (KB5126967), review the KB prerequisites, and not to mix CU and GDR branches.
  - SQL Server 2019 / 2017 / 2016 "Migrate → 2022" actions: the incorrect "mainstream support until Jan 2033" is corrected to mainstream support until Jan 2028 and extended support until Jan 2033, per the SQL Server 2022 lifecycle page (month/year only) and matching the SQL Server 2022 entry's own lifecycle warning.
  - SQL Server 2016 primary warning: "Extended Support ended July 11, 2026" is now "Extended Support ended July 2026" (month/year only; the exact day was not verified, and July 11, 2026 is a Saturday).
  - SQL Server 2016 "Azure Connect FP" action: now says it applies only if the Azure Connect Feature Pack is installed.
  - .NET Framework main action and warning: month and CVRF date moved from August to October 2026 (structure unchanged). The Server 2012 R2 alternative warning now says the Final EOL was reached in October 2026 (it still contains `EOL`, so the dashboard keeps rendering it as critical).
  - .NET Framework "Migrate → .NET 8" alternative: the option is unchanged; only a caution was added that .NET 8 LTS support ends in Nov 2026 (taken from the alternative's existing "LTS until Nov 2026" date), so operators verify the support window of their migration target.
- **Unchanged:** the Internet Explorer entry (permanently retired).
- **Primary official sources (support.microsoft.com / learn.microsoft.com):**
  - Server 2012 R2 KB5126836: https://support.microsoft.com/en-us/servicing/os/windows-8-1/2026/10/kb5126836-windows-8-1-mr
  - Server 2016 KB5126868: https://support.microsoft.com/en-us/servicing/os/windows-10/2026/10/kb5126868-windows-10-1607-security-update
  - Server 2019 KB5126651: https://support.microsoft.com/en-us/servicing/os/windows-10/2026/10/kb5126651-windows-10-1809-security-update
  - Server 2022 KB5126655: https://support.microsoft.com/en-us/servicing/os/windows-server/2026/10/kb5126655-windows-server-2022-security-update
  - Server 2025 KB5126646: https://support.microsoft.com/en-us/servicing/os/windows-server/2026/10/kb5126646-windows-server-2025-security-update
  - SQL Server 2019 KB5128494: https://support.microsoft.com/en-us/servicing/sql/sql-server-2019/cumulative-update/kb5128494-cu32-gdr-october-2026
  - SQL Server 2019 GDR KB5128495: https://support.microsoft.com/en-us/servicing/sql/sql-server-2019/general-distribution-release/kb5128495-october-2026
  - SQL Server 2017 KB5128496: https://support.microsoft.com/en-us/servicing/sql/sql-server-2017/cumulative-update/kb5128496-cu31-gdr-october-2026
  - SQL Server 2017 GDR KB5128497: https://support.microsoft.com/en-us/servicing/sql/sql-server-2017/general-distribution-release/kb5128497-october-2026
  - SQL Server 2022 KB5126934: https://support.microsoft.com/en-us/servicing/sql/sql-server-2022/cumulative-update/kb5126934-cu27-gdr-october-2026
  - SQL Server 2022 GDR KB5128493: https://support.microsoft.com/en-us/servicing/sql/sql-server-2022/general-distribution-release/kb5128493-october-2026
  - SQL Server 2025 KB5126967: https://support.microsoft.com/en-us/servicing/sql/sql-server-2025/cumulative-update/kb5126967-cu9-gdr-october-2026
  - SQL Server 2025 GDR KB5128492: https://support.microsoft.com/en-us/servicing/sql/sql-server-2025/general-distribution-release/kb5128492-october-2026
  - SQL Server 2016 KB5102340 (July 14, 2026; no newer update listed as of October 28, 2026): https://support.microsoft.com/en-us/servicing/sql/sql-server-2016/general-distribution-release/kb5102340-july-2026
  - SQL Server 2016 Azure Connect Feature Pack KB5102339 (July 14, 2026): https://support.microsoft.com/en-us/servicing/sql/sql-server-2016/general-distribution-release/kb5102339-july-2026
  - .NET Framework October 2026 cumulative update (release notes): https://learn.microsoft.com/en-us/dotnet/framework/release-notes/2026/10-13-october-cumulative-update
  - .NET Framework, Server 2025 KB5127690: https://support.microsoft.com/en-us/servicing/dotnetframework/windows-11/25h2/october-13-2026-5127690
  - .NET Framework, Server 2022 KB5127693: https://support.microsoft.com/en-us/servicing/dotnetframework/microsoft-server/2022/2026/10/october-13-2026-5127693
  - .NET Framework, Server 2019 KB5127685: https://support.microsoft.com/en-us/servicing/dotnetframework/windows-10/1809/2026/10/october-13-2026-5127685
  - .NET Framework, Server 2016 KB5127684: https://support.microsoft.com/en-us/servicing/dotnetframework/windows-10/1607/2026/10/october-13-2026-5127684
  - .NET Framework, Server 2012 R2 (.NET 4.8) KB5127688: https://support.microsoft.com/en-us/servicing/dotnetframework/2026/10/october-13-2026-5127688
  - .NET Framework, Server 2012 R2 (.NET 4.6.2 / 4.7 / 4.7.1 / 4.7.2) KB5127668: https://support.microsoft.com/en-us/servicing/dotnetframework/2026/10/october-13-2026-5127668
  - Windows Server 2016 lifecycle (mainstream ended January 2022, extended ends January 2027): https://learn.microsoft.com/en-us/lifecycle/products/windows-server-2016
  - Windows Server 2022 lifecycle (mainstream ended October 2026, extended support security updates through October 2031): https://learn.microsoft.com/en-us/lifecycle/products/windows-server-2022
  - SQL Server 2022 lifecycle (mainstream January 2028, extended January 2033): https://learn.microsoft.com/en-us/lifecycle/products/sql-server-2022
  - SQL Server latest updates (official table; basis for the SQL Server 2016 statement as of October 28, 2026): https://support.microsoft.com/en-us/servicing/sql/kb321185-download-and-install-latest-updates
  - Extended Security Updates FAQ (cited only because it is silent about update packaging; not evidence about Security-Only availability either way): https://learn.microsoft.com/en-us/lifecycle/faq/extended-security-updates

## 2026-09-03 — August 2026 Patch Tuesday refresh

- Refreshed all 5 Windows Server entries + .NET Framework to **August 11, 2026** KBs. All KB/build/date/URL values verified against support.microsoft.com.
- Windows Server 2019: KB5099538 → **KB5120238** (build 17763.9121).
- Windows Server 2016: KB5099535 → **KB5120418** (build 14393.9418).
- Windows Server 2022: KB5099540 → **KB5120242** (build 20348.5499). Standard Security-Update LCU chosen over the no-reboot Hotpatch variant (KB5120229).
- Windows Server 2025: KB5099536 → **KB5120233** (build 26100.33296). Standard LCU over Hotpatch (KB5120228).
- Windows Server 2012 R2 (ESU): KB5099444 → **KB5120385** (Monthly Rollup, build 6.3.9600.23338). 2 ESU rollups remaining before October 13, 2026 final EOL.
- Promoted previous "Jun 2026 CU" rollback alternatives to **"Jul 2026 CU"** rollbacks (KB5099538 / KB5099535 / KB5099540) on the 2019/2016/2022 entries; updated WSUS Catalog search URLs to the new August KBs.
- **.NET Framework**: refreshed per-OS security-and-quality rollups to August KBs — Server 2025 **KB5120708** (3.5+4.8.1), Server 2022 **KB5120714** (3.5+4.8.1), Server 2019 **KB5120703** (3.5+4.8), Server 2016 **KB5120702** (4.8), Server 2012 R2 **KB5120700 / KB5120706** (4.7.x + 4.8). Release-note URL → 2026-Aug.
- **SQL Server 2016 / 2017 / 2019 / 2022 / 2025**: unchanged. The August 2026 MSRC CVRF (`2026-Aug`) contains **zero SQL Server products** — no SQL Server security update shipped this cycle. July 2026 CU+GDR KBs remain current.
- IE entry unchanged (permanently retired).
- Sources: MSRC CVRF `2026-Aug` (`Vulnerability[].Remediations`, Type 2 Vendor Fix); support.microsoft.com KB/update-history pages for each KB (all confirmed August 11, 2026). Note: the CVRF `CurrentReleaseDate` field reads `2026-09-08`, but every support.microsoft.com page dates these KBs **August 11, 2026** (the actual Patch Tuesday) — the human-readable date follows the support pages.

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
