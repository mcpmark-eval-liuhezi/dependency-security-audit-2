# npm Advisory Watchlist

Quarterly dependency security review — evidence gathered from GitHub's global security advisory database.
Scope: reviewed advisories affecting **npm** packages, critical and high severity, first page of results as of the review date.

## Watchlist

| # | GHSA ID | Severity | Affected package(s) | First patched version | Notes |
|---|---------|----------|----------------------|-----------------------|-------|
| 1 | **GHSA-qx66-fv34-fjm8** | **Critical** | `@tanstack/start-server-core`, `@tanstack/react-start`, `@tanstack/solid-start`, `@tanstack/vue-start` | `1.169.39` (`@tanstack/start-server-core@1.169.39`; also `1.168.60` / `1.168.57` / `1.168.56` for the react/solid/vue entries) | ⚠️ **MOST URGENT — FLAGGED.** CVE-2026-102989. Unauthenticated reflected XSS in TanStack Start server-function responses. CVSS 9.3. |
| 2 | GHSA-x34j-47hf-4xg7 | Critical | `tinacms`, `@tinacms/app` | `tinacms@3.14.0` / `@tinacms/app@2.5.14` (fix landed in PR #7522, released in the 3.14.0 / 2.5.14 patch line) | CVE-2026-108261. Admin preview iframe loads an attacker-controlled origin from the URL fragment. CVSS 9.3. |
| 3 | GHSA-pq7j-f95f-qfcv | High | `@anthropic-ai/claude-code` | `2.1.179` | CVE-2026-86063. Plugin hash pin bypass (supply-chain). |
| 4 | GHSA-x586-xvc8-g7q6 | High | `@builder.io/qwik`, `@qwik.dev/core` | `1.20.0` (`@builder.io/qwik@1.20.0`; `@qwik.dev/core@2.0.0-beta37`) | CVE-2026-84994. Remote unauthenticated server crash via Resource thenable. |
| 5 | GHSA-2vc4-c4r6-p6v6 | High | `@opennextjs/cloudflare` | `1.20.2` | CVE-2026-100409. Cache interception can bypass middleware protection for encoded paths. CVSS 7.5. |

### Most urgent advisory

**GHSA-qx66-fv34-fjm8 — TanStack Router (critical).**
- **GHSA ID:** GHSA-qx66-fv34-fjm8
- **CVE:** CVE-2026-102989
- **Affected packages:** `@tanstack/start-server-core`, `@tanstack/react-start`, `@tanstack/solid-start`, `@tanstack/vue-start` (vulnerable from `1.143.12`)
- **First patched version:** `@tanstack/start-server-core@1.169.39` (plus `@tanstack/react-start@1.168.60`, `@tanstack/solid-start@1.168.57`, `@tanstack/vue-start@1.168.56`)
- **CVSS:** 9.3 (`CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:H/I:H/A:N`), CWE-79
- **Impact:** An unauthenticated attacker can craft a URL to a server function in an affected TanStack Start app. If someone opens the link, the app returns attacker-controlled HTML from its own origin and runs attacker JavaScript there, able to access same-origin data and make requests with the visitor's authority.
- **Advisory:** https://github.com/advisories/GHSA-qx66-fv34-fjm8

## Maintainer

The affected package is maintained by the GitHub **organization** `TanStack` (https://github.com/TanStack, org ID 72518640), the maintainers of the TanStack router monorepo at https://github.com/TanStack/router. (The original fix commit in the advisory references is authored by Tanner Linsley, but the repository is owned and maintained by the TanStack org.)

## Fix tag

The maintainers publish git tags on the `TanStack/router` repository. The release that first contains the fix for GHSA-qx66-fv34-fjm8 is referenced directly in the advisory references:

- **Tag name:** `release-2026-09-30-1747`
- **Commit SHA it points to:** `57e126e99dbd86f735ead2ba98ba5e98ef0cc668`
  - (annotated tag object SHA: `fbc09f257689a6586aea0094ab3f5f228c54f635`, dated 2026-09-30T17:47:25Z, tagged by `github-actions[bot]`)
  - The pointed-to commit is the changesets "Version Packages (#8531)" release commit from 2026-09-30T17:41:29Z, which consumes the fix changeset from PR #8573 (`d521abd71c69f1ff010bb3def4d417cb5fa058cb`, "fix(start): align server function transport behavior", merged 2026-09-30T17:29:54Z)

## Remediation tracking

An issue titled `Bump @tanstack/start-server-core past 1.169.39` has been opened in this repository for the most urgent advisory and assigned to Copilot for remediation.
