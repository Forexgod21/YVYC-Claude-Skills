# Google Sheets & Apps Script — How To Use

**Skill:** `google-sheets`
**Category:** Productivity
**Author:** YourVisionYourCreation LLC
**Version:** 1.0
**License:** CC BY 4.0

---

## What This Skill Does

This is a complete, elite-level reference for Google Sheets automation and
Google Apps Script — 30 sections covering everything from the SpreadsheetApp
core API to sidebars, triggers, custom functions, workspace integrations,
deployment with Clasp, and the tracker-system patterns behind YVYC's TEMPO OS
and Blast Plan builds.

Once installed, Claude stops writing slow, fragile, single-cell Apps Script
and starts producing batch-optimized, properly structured, production-grade
automation — every time, even for "simple" requests.

This is the first skill in the `productivity/` category.

---

## The Problem It Solves

Untrained AI output for Sheets automation has predictable failures:

- Cell-by-cell reads and writes that take minutes instead of seconds (the #1
  Apps Script performance mistake)
- Data logic and UI rendering tangled into one untestable function
- Triggers that fire recursively or die silently
- API keys hardcoded into scripts instead of PropertiesService
- No batching, no caching, no LockService — race conditions in shared sheets

This skill encodes the correct pattern for each, so they're applied by
default.

---

## What's Inside (30 Sections)

| Area | Coverage |
|---|---|
| **Core** | Architecture decisions, SpreadsheetApp API, batch read/write |
| **Automation** | Triggers (onEdit/onOpen/time-based), custom menus, custom functions |
| **UI** | HtmlService sidebars and modals, dashboards |
| **Data** | Validation, conditional formatting, named/protected ranges, pivot tables, charts |
| **Integrations** | Drive, Gmail, Calendar, Forms, Docs, Slides, external APIs via UrlFetchApp |
| **State & Perf** | PropertiesService, LockService, CacheService, optimization checklist |
| **Ops** | Error handling, logging, import/export (CSV/XLSX/PDF/JSON), Clasp deployment |
| **Patterns** | Security patterns, common bugs and fixes, TEMPO OS / Blast Plan tracker patterns |

---

## Example Prompts

```
Build an Apps Script that emails me a summary when any row's status changes to "Done".
```
```
This onEdit trigger is slow — optimize it with batch reads.
```
```
Create a sidebar dashboard for this tracker sheet: totals, streaks, and a refresh button.
```
```
Set up the file structure for a complex Sheets project with Clasp version control.
```

---

## When It Activates

Any mention of Google Sheets, Apps Script, `.gs` files, `SpreadsheetApp`,
`HtmlService`, sidebars, custom menus, `onEdit`, or sheet-level automation —
even when the request sounds simple.

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. It activates automatically on any Sheets or Apps Script task

---

*Part of the YVYC Claude Skills Library — Productivity Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
