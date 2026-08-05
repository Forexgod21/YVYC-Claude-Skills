---
name: google-sheets
category: productivity
description: >
  Use for any task involving Google Sheets or Google Apps Script (.gs
  files): reading, writing, formatting, or analyzing sheet data; Apps Script
  automations, triggers, custom menus, sidebars, and custom functions;
  integrating Sheets with Gmail, Drive, Calendar, or external APIs;
  import/export; debugging; and batch performance. Trigger on any mention of
  Sheets, Apps Script, SpreadsheetApp, HtmlService, onEdit, or sheet-level
  automation — even when the request sounds simple.
---

# Google Sheets & Apps Script — Elite Reference

## Table of Contents

1. [Architecture Decisions](#1-architecture-decisions)
2. [SpreadsheetApp Core API](#2-spreadsheetapp-core-api)
3. [Batch Read / Write — The #1 Performance Rule](#3-batch-read--write)
4. [Apps Script Triggers](#4-apps-script-triggers)
5. [HtmlService — Sidebars & Modals](#5-htmlservice--sidebars--modals)
6. [Custom Menus](#6-custom-menus)
7. [Data Validation](#7-data-validation)
8. [Conditional Formatting](#8-conditional-formatting)
9. [Named Ranges & Protected Ranges](#9-named-ranges--protected-ranges)
10. [Custom Functions](#10-custom-functions)
11. [Charts & Sparklines](#11-charts--sparklines)
12. [Pivot Tables via Script](#12-pivot-tables-via-script)
13. [Google Drive Integration](#13-google-drive-integration)
14. [Gmail Integration](#14-gmail-integration)
15. [Calendar Integration](#15-calendar-integration)
16. [Forms Integration](#16-forms-integration)
17. [Docs & Slides Integration](#17-docs--slides-integration)
18. [External API Calls (UrlFetchApp)](#18-external-api-calls-urlfetchapp)
19. [PropertiesService — Persistent State](#19-propertiesservice--persistent-state)
20. [LockService — Concurrency](#20-lockservice--concurrency)
21. [CacheService — Performance](#21-cacheservice--performance)
22. [Utilities — Dates, Formatting, Encoding](#22-utilities)
23. [Error Handling & Logging](#23-error-handling--logging)
24. [Import / Export — CSV, XLSX, PDF, JSON](#24-import--export)
25. [Advanced Formatting Patterns](#25-advanced-formatting-patterns)
26. [Performance Optimization Checklist](#26-performance-optimization-checklist)
27. [Security Patterns](#27-security-patterns)
28. [Deployment — Clasp & Version Control](#28-deployment--clasp--version-control)
29. [Common Bugs & Fixes](#29-common-bugs--fixes)
30. [TEMPO OS / Blast Plan Patterns](#30-tempo-os--blast-plan-patterns)

---

## 1. Architecture Decisions

### When to use Apps Script vs. other tools

| Need | Tool |
|------|------|
| Automate Sheets natively | Apps Script (.gs) |
| Heavy data transformation | Apps Script + batch API |
| Real-time collaboration UI | HtmlService sidebar |
| Expose Sheet as REST API | Apps Script Web App (`doGet`/`doPost`) |
| Large data pipelines | Sheets API v4 via external service |
| Version control | Clasp (CLI sync to local) |

### File structure for complex projects

```
project/
├── Code.gs          — onOpen, onEdit, menu, main entry points
├── Engine.gs        — pure data logic, no UI calls
├── Views.gs         — tab builders, formatters
├── Sidebar.html     — HtmlService UI
├── Dashboard.html   — secondary UI
└── appsscript.json  — manifest (timeZone, oauthScopes)
```

**Rule:** Never mix data logic and UI rendering in the same function. Keep `Engine.gs` pure — testable without a spreadsheet open.

---

## 2. SpreadsheetApp Core API

### Getting sheets

```javascript
var ss     = SpreadsheetApp.getActiveSpreadsheet();
var sheet  = ss.getSheetByName("Sheet1");           // by name — preferred
var sheet2 = ss.getSheets()[0];                      // by index
var sheet3 = ss.getActiveSheet();                    // currently selected
var id     = ss.getId();                             // spreadsheet ID string
```

### Range access

```javascript
// By notation
var r1 = sheet.getRange("A1");
var r2 = sheet.getRange("A1:C10");
var r3 = sheet.getRange("A:A");           // entire column
var r4 = sheet.getRange("1:1");           // entire row

// By row/col (1-based)
var r5 = sheet.getRange(1, 1);            // A1
var r6 = sheet.getRange(1, 1, 10, 3);    // 10 rows × 3 cols from A1

// Dynamic last row / col
var lastRow = sheet.getLastRow();
var lastCol = sheet.getLastColumn();
var dataRange = sheet.getDataRange();     // entire used range
```

### Reading values

```javascript
var val    = sheet.getRange("A1").getValue();         // single cell
var vals   = sheet.getRange("A1:C10").getValues();    // 2D array — ALWAYS use this for bulk
var disp   = sheet.getRange("A1").getDisplayValue();  // formatted string (dates, currency)
var disps  = sheet.getRange("A1:C5").getDisplayValues();
var form   = sheet.getRange("A1").getFormula();
var forms  = sheet.getRange("A1:C5").getFormulas();
```

### Writing values

```javascript
sheet.getRange("A1").setValue("Hello");
sheet.getRange("A1:C1").setValues([["A", "B", "C"]]);  // 2D array required
sheet.getRange("A1").setFormula("=SUM(B1:B10)");
sheet.getRange("A1").setFormulaR1C1("=R[0]C[1]+R[0]C[2]");

// Clear
sheet.getRange("A1:C10").clearContent();
sheet.getRange("A1:C10").clear();         // content + format
sheet.getRange("A1:C10").clearFormat();
```

### Sheet manipulation

```javascript
ss.insertSheet("New Tab");
ss.insertSheet("New Tab", 0);             // insert at position 0
ss.deleteSheet(sheet);
ss.duplicateActiveSheet();
sheet.setName("Renamed");
sheet.setTabColor("#FF0000");
sheet.hideSheet();
sheet.showSheet();
ss.setActiveSheet(sheet);
ss.moveActiveSheet(2);                    // move to position 2

// Freeze
sheet.setFrozenRows(1);
sheet.setFrozenColumns(2);
sheet.setHiddenGridlines(true);

// Row / col sizing
sheet.setRowHeight(1, 48);
sheet.setColumnWidth(1, 200);
sheet.setRowHeights(1, 10, 30);           // rows 1-10 all height 30
sheet.hideRow(sheet.getRange("A5"));
sheet.showRows(5, 1);
```

---

## 3. Batch Read / Write

> **This is the single most important performance rule in Apps Script.**
> Every `getValue()` / `setValue()` inside a loop kills performance.
> Read once → process in memory → write once.

### ❌ WRONG — O(n) API calls

```javascript
for (var i = 1; i <= 100; i++) {
  var val = sheet.getRange(i, 1).getValue();   // 100 API calls
  sheet.getRange(i, 2).setValue(val * 2);      // 100 more
}
```

### ✅ CORRECT — O(1) API calls

```javascript
var data    = sheet.getRange(1, 1, 100, 1).getValues();   // 1 read
var output  = [];
for (var i = 0; i < data.length; i++) {
  output.push([data[i][0] * 2]);
}
sheet.getRange(1, 2, output.length, 1).setValues(output); // 1 write
```

### Flush when needed

```javascript
SpreadsheetApp.flush();   // force pending writes to apply before continuing
```

### Column index reference (getValues() is 0-based in the array, 1-based in getRange)

```javascript
// If ENG_STATE_COL = 6 (1-based column 6)
var state = row[6 - 1];   // index 5 in the array
```

---

## 4. Apps Script Triggers

### Simple triggers (no authorization required)

```javascript
function onOpen(e) { /* fires when spreadsheet opens */ }
function onEdit(e) { /* fires on any cell edit */ }
function onSelectionChange(e) { /* fires on selection change */ }
function onChange(e) { /* fires on structural changes — add sheet, etc. */ }
```

### Event object — onEdit

```javascript
function onEdit(e) {
  var range    = e.range;
  var sheet    = range.getSheet();
  var row      = range.getRow();
  var col      = range.getColumn();
  var newVal   = e.value;          // new value (single cell)
  var oldVal   = e.oldValue;       // previous value
  var user     = e.user;           // User object (installable only)
}
```

### Guard pattern — always guard onEdit

```javascript
function onEdit(e) {
  if (!e || !e.range) return;
  var sheet = e.range.getSheet();
  var name  = sheet.getName();
  if (name !== "Target Sheet") return;
  if (e.range.getColumn() !== 5) return;
  if (e.range.getRow() < 2) return;
  // safe to proceed
}
```

### Installable triggers (full authorization)

```javascript
// Install programmatically
ScriptApp.newTrigger("myFunction")
  .forSpreadsheet(SpreadsheetApp.getActive())
  .onEdit()
  .create();

ScriptApp.newTrigger("dailyReport")
  .timeBased()
  .everyDays(1)
  .atHour(7)
  .create();

// List and delete
var triggers = ScriptApp.getProjectTriggers();
for (var i = 0; i < triggers.length; i++) {
  ScriptApp.deleteTrigger(triggers[i]);
}
```

### onChange trigger (structural changes)

```javascript
function onChange(e) {
  Logger.log(e.changeType);   // INSERT_ROW, REMOVE_ROW, INSERT_COLUMN, etc.
}
```

---

## 5. HtmlService — Sidebars & Modals

### Show sidebar

```javascript
function showSidebar() {
  var html = HtmlService.createHtmlOutputFromFile("Sidebar")
    .setTitle("My Sidebar")
    .setWidth(380);
  SpreadsheetApp.getUi().showSidebar(html);
}
```

### Show modal dialog

```javascript
function showModal() {
  var html = HtmlService.createHtmlOutputFromFile("Modal")
    .setWidth(600)
    .setHeight(400);
  SpreadsheetApp.getUi().showModalDialog(html, "Dialog Title");
}
```

### Show modeless dialog

```javascript
SpreadsheetApp.getUi().showModelessDialog(html, "Title");
```

### HTML → Apps Script (client calls server)

```html
<!-- In Sidebar.html -->
<script>
  // Call a server function
  google.script.run
    .withSuccessHandler(function(result) { console.log(result); })
    .withFailureHandler(function(err)    { console.error(err.message); })
    .myServerFunction("arg1", 42);

  // Close the sidebar/dialog
  google.script.host.close();
</script>
```

### Apps Script → HTML (server returns data to HTML)

```javascript
// Server-side: pass data into template
function showSidebarWithData() {
  var tmpl = HtmlService.createTemplateFromFile("Sidebar");
  tmpl.data = getMyData();   // available as <?= data ?> in HTML
  var html = tmpl.evaluate().setTitle("Sidebar").setWidth(380);
  SpreadsheetApp.getUi().showSidebar(html);
}
```

```html
<!-- In Sidebar.html template -->
<div><?= JSON.stringify(data) ?></div>
```

### Include CSS/JS from separate files

```html
<?!= HtmlService.createHtmlOutputFromFile("styles").getContent() ?>
<?!= HtmlService.createHtmlOutputFromFile("scripts").getContent() ?>
```

### Sidebar communication pattern (full round-trip)

```javascript
// Server
function getDashboardData() {
  var ss   = SpreadsheetApp.getActiveSpreadsheet();
  var data = buildDataObject_(ss);
  return data;   // must be JSON-serializable
}

function updateStateFromDashboard(code, newState) {
  // write to sheet, return result
  return { success: true };
}
```

```html
<!-- Client -->
<script>
function loadDashboard() {
  google.script.run
    .withSuccessHandler(renderDashboard)
    .withFailureHandler(renderError)
    .getDashboardData();
}

function updateState(code, state) {
  google.script.run
    .withSuccessHandler(function() { loadDashboard(); })
    .withFailureHandler(function(e) { alert(e.message); })
    .updateStateFromDashboard(code, state);
}

loadDashboard();
</script>
```

---

## 6. Custom Menus

```javascript
function onOpen() {
  SpreadsheetApp.getUi()
    .createMenu("My App")
    .addItem("Open Dashboard",    "showDashboard")
    .addSeparator()
    .addItem("Refresh All",       "refreshAll")
    .addItem("Health Check",      "runHealthCheck")
    .addSeparator()
    .addSubMenu(
      SpreadsheetApp.getUi().createMenu("Settings")
        .addItem("Toggle Notifications", "toggleNotifications")
        .addItem("Send Report",          "sendProgressReport")
    )
    .addToUi();
}
```

---

## 7. Data Validation

### Dropdown from list

```javascript
var rule = SpreadsheetApp.newDataValidation()
  .requireValueInList(["Option A", "Option B", "Option C"], true)
  .setAllowInvalid(false)
  .setHelpText("Pick one.")
  .build();

sheet.getRange("E2:E100").setDataValidation(rule);
```

### Dropdown from range

```javascript
var rule = SpreadsheetApp.newDataValidation()
  .requireValueInRange(sheet.getRange("Lists!A1:A10"), true)
  .build();
```

### Number constraints

```javascript
var rule = SpreadsheetApp.newDataValidation()
  .requireNumberBetween(1, 100)
  .build();
```

### Date constraints

```javascript
var rule = SpreadsheetApp.newDataValidation()
  .requireDateOnOrAfter(new Date("2024-01-01"))
  .build();
```

### Checkbox

```javascript
var rule = SpreadsheetApp.newDataValidation()
  .requireCheckbox()
  .build();
// Or with custom values:
SpreadsheetApp.newDataValidation()
  .requireCheckbox("YES", "NO")
  .build();
```

### Remove validation

```javascript
sheet.getRange("E2:E100").clearDataValidations();
```

---

## 8. Conditional Formatting

```javascript
var sheet = ss.getSheetByName("Data");
var range = sheet.getRange("F2:F100");
var rules = sheet.getConditionalFormatRules();

// Color scale
var colorScaleRule = SpreadsheetApp.newConditionalFormatRule()
  .setGradientMaxpointWithValue("#00ff00", SpreadsheetApp.InterpolationType.NUMBER, "100")
  .setGradientMidpointWithValue("#ffff00", SpreadsheetApp.InterpolationType.NUMBER, "50")
  .setGradientMinpointWithValue("#ff0000", SpreadsheetApp.InterpolationType.NUMBER, "0")
  .setRanges([range])
  .build();

// Text contains
var textRule = SpreadsheetApp.newConditionalFormatRule()
  .whenTextContains("MET STANDARD")
  .setBackground("#052e16")
  .setFontColor("#4ade80")
  .setBold(true)
  .setRanges([range])
  .build();

// Formula-based (most powerful)
var formulaRule = SpreadsheetApp.newConditionalFormatRule()
  .whenFormulaSatisfied('=$F2="IN PROGRESS"')
  .setBackground("#0a2e0a")
  .setRanges([sheet.getRange("A2:G100")])
  .build();

rules.push(colorScaleRule);
rules.push(textRule);
rules.push(formulaRule);
sheet.setConditionalFormatRules(rules);

// Clear all rules
sheet.clearConditionalFormatRules();
```

---

## 9. Named Ranges & Protected Ranges

### Named ranges

```javascript
// Create
ss.setNamedRange("DataRange", sheet.getRange("A2:G100"));

// Get
var nr = ss.getRangeByName("DataRange");

// List all
var namedRanges = ss.getNamedRanges();
namedRanges.forEach(function(nr) {
  Logger.log(nr.getName() + " → " + nr.getRange().getA1Notation());
});

// Delete
ss.getNamedRanges().forEach(function(nr) {
  if (nr.getName() === "DataRange") nr.remove();
});
```

### Protected ranges

```javascript
// Protect a range — allow only current user
var protection = sheet.getRange("A1:Z1").protect();
protection.setDescription("Header — do not edit");
protection.removeEditors(protection.getEditors());
protection.addEditor(Session.getEffectiveUser());

// Protect entire sheet except specific range
var sheetProtection = sheet.protect();
sheetProtection.setUnprotectedRanges([sheet.getRange("E2:E100")]);

// Remove protection
var protections = sheet.getProtections(SpreadsheetApp.ProtectionType.RANGE);
protections.forEach(function(p) { p.remove(); });
```

---

## 10. Custom Functions

```javascript
/**
 * Calculates completion percentage.
 * @param {number} done Number of completed items.
 * @param {number} total Total items.
 * @return {string} Formatted percentage.
 * @customfunction
 */
function COMPLETION_PCT(done, total) {
  if (!total || total === 0) return "0%";
  return Math.round((done / total) * 100) + "%";
}

/**
 * Returns the state color code for a given status string.
 * @param {string} state The competency state.
 * @return {string} Hex color.
 * @customfunction
 */
function STATE_COLOR(state) {
  var map = {
    "MET STANDARD":         "#FFD700",
    "ASSESSMENT SUBMITTED": "#93c5fd",
    "IN PROGRESS":          "#22c55e",
    "DID NOT MEET":         "#c4a882",
    "NOT STARTED":          "#ef4444"
  };
  return map[String(state).trim().toUpperCase()] || "#ffffff";
}
```

**Custom function rules:**
- Must be deterministic (no `Date.now()`, no random)
- Cannot call `SpreadsheetApp.getUi()`, send email, or modify sheets
- Results are cached — add a dummy param if you need to force recalc
- Max execution: 30 seconds

---

## 11. Charts & Sparklines

### Create a chart via script

```javascript
var chart = sheet.newChart()
  .setChartType(Charts.ChartType.LINE)
  .addRange(sheet.getRange("A1:B20"))
  .setPosition(5, 5, 0, 0)
  .setOption("title", "Progress Over Time")
  .setOption("legend", { position: "bottom" })
  .setOption("backgroundColor", "#0d1117")
  .setOption("colors", ["#22d3ee", "#4ade80"])
  .setOption("hAxis", { textStyle: { color: "#94a3b8" } })
  .setOption("vAxis", { textStyle: { color: "#94a3b8" } })
  .build();

sheet.insertChart(chart);
```

### Chart types

```javascript
Charts.ChartType.BAR
Charts.ChartType.COLUMN
Charts.ChartType.LINE
Charts.ChartType.AREA
Charts.ChartType.PIE
Charts.ChartType.SCATTER
Charts.ChartType.COMBO
Charts.ChartType.STEPPED_AREA
Charts.ChartType.GAUGE
```

### Sparklines (formula — fastest)

```
=SPARKLINE(B2:B20, {"charttype","line";"color","#22d3ee";"linewidth",2})
=SPARKLINE(B2:B20, {"charttype","bar";"color1","#4ade80";"color2","#ef4444"})
=SPARKLINE(B2:B20, {"charttype","column";"color","#fbbf24"})
=SPARKLINE(B2:B20, {"charttype","winloss";"firstcolor","#22d3ee";"lastcolor","#c084fc"})
```

### Modify existing chart

```javascript
var charts = sheet.getCharts();
var chart  = charts[0];
var updated = chart.modify()
  .setOption("title", "Updated Title")
  .build();
sheet.updateChart(updated);
sheet.removeChart(chart);
```

---

## 12. Pivot Tables via Script

Pivot tables cannot be fully created via Apps Script — use formulas instead:

```
=QUERY(Data!A:G, "SELECT A, COUNT(B) GROUP BY A ORDER BY COUNT(B) DESC", 1)
=PIVOTBY(Data!C2:C, Data!F2:F, Data!D2:D, COUNTA)
=GROUPBY(Data!C2:C, Data!D2:D, SUM)
```

### QUERY — the most powerful Sheets formula

```
=QUERY(range, "SELECT col, COUNT(col2) WHERE col3 = 'MET STANDARD' GROUP BY col ORDER BY COUNT(col2) DESC LIMIT 10", headers)
```

---

## 13. Google Drive Integration

```javascript
// Get file by ID
var file = DriveApp.getFileById("FILE_ID");

// Get file name, URL
Logger.log(file.getName());
Logger.log(file.getUrl());

// List files in folder
var folder = DriveApp.getFolderById("FOLDER_ID");
var files  = folder.getFiles();
while (files.hasNext()) {
  var f = files.next();
  Logger.log(f.getName());
}

// Create file in folder
var blob    = Utilities.newBlob("Hello World", "text/plain", "output.txt");
var newFile = folder.createFile(blob);

// Spreadsheet from Drive
var newSS = SpreadsheetApp.create("New Spreadsheet");
DriveApp.getFileById(newSS.getId()).moveTo(folder);

// Share file
file.addEditor("user@example.com");
file.addViewer("viewer@example.com");
file.setSharing(DriveApp.Access.ANYONE_WITH_LINK, DriveApp.Permission.VIEW);
```

---

## 14. Gmail Integration

```javascript
// Send simple email
MailApp.sendEmail("recipient@example.com", "Subject", "Body text");

// Send rich HTML email
GmailApp.sendEmail(
  "recipient@example.com",
  "Subject",
  "Plain text fallback",
  {
    htmlBody: "<h1>Hello</h1><p>Rich content</p>",
    name:     "Blast Plan Brain",
    replyTo:  "noreply@yourdomain.com",
    cc:       "cc@example.com"
  }
);

// Send to current user
var email = Session.getActiveUser().getEmail();
MailApp.sendEmail(email, "Your Report", buildReportBody_());

// Check quota remaining
var quota = MailApp.getRemainingDailyQuota();

// Read inbox (installable trigger required)
var threads = GmailApp.search("subject:Blast Plan", 0, 10);
threads.forEach(function(thread) {
  Logger.log(thread.getFirstMessageSubject());
});
```

---

## 15. Calendar Integration

```javascript
// Get default calendar
var cal = CalendarApp.getDefaultCalendar();

// Create event
var event = cal.createEvent(
  "Submit PSYC-8230",
  new Date("2026-04-15T09:00:00"),
  new Date("2026-04-15T10:00:00"),
  { description: "Blast Plan deadline", location: "Remote" }
);

// Create all-day event
cal.createAllDayEvent("Deadline", new Date("2026-04-15"));

// Get events in range
var events = cal.getEvents(new Date("2026-04-01"), new Date("2026-04-30"));
events.forEach(function(ev) {
  Logger.log(ev.getTitle() + " — " + ev.getStartTime());
});

// Delete event
event.deleteEvent();

// Get by ID
var specificCal = CalendarApp.getCalendarById("calendar_id@group.calendar.google.com");
```

---

## 16. Forms Integration

```javascript
// Open linked form
var form = FormApp.openByUrl("https://docs.google.com/forms/d/FORM_ID/edit");

// Get form responses
var responses = form.getResponses();
responses.forEach(function(r) {
  Logger.log(r.getRespondentEmail() + " — " + r.getTimestamp());
  var itemResponses = r.getItemResponses();
  itemResponses.forEach(function(ir) {
    Logger.log(ir.getItem().getTitle() + ": " + ir.getResponse());
  });
});

// onFormSubmit trigger
function onFormSubmit(e) {
  var response = e.response;
  var values   = e.values;   // array matching sheet columns
  Logger.log(values.join(", "));
}
```

---

## 17. Docs & Slides Integration

### Docs

```javascript
// Create doc
var doc = DocumentApp.create("My Report");
var body = doc.getBody();
body.appendParagraph("BLAST PLAN REPORT").setHeading(DocumentApp.ParagraphHeading.HEADING1);
body.appendParagraph("Generated: " + new Date().toLocaleDateString());
body.appendTable([["Code", "Title", "State"], ["PSYC-8230", "Comp Title", "MET"]]);
doc.saveAndClose();

// Open existing
var doc2 = DocumentApp.openById("DOC_ID");

// Export to PDF
var pdf = DriveApp.getFileById(doc.getId()).getAs("application/pdf");
DriveApp.getRootFolder().createFile(pdf);
```

### Slides

```javascript
var deck = SlidesApp.create("Blast Plan Deck");
var slide = deck.getSlides()[0];
slide.insertTextBox("MISSION OVERVIEW").setLeft(100).setTop(50);

var newSlide = deck.appendSlide(SlidesApp.PredefinedLayout.TITLE_AND_BODY);
newSlide.getPlaceholders()[0].asShape().getText().setText("Progress Report");
```

---

## 18. External API Calls (UrlFetchApp)

### GET request

```javascript
var response = UrlFetchApp.fetch("https://api.example.com/data", {
  method:  "get",
  headers: { "Authorization": "Bearer " + getToken_() },
  muteHttpExceptions: true
});

if (response.getResponseCode() !== 200) {
  Logger.log("Error: " + response.getContentText());
  return null;
}

var json = JSON.parse(response.getContentText());
```

### POST request

```javascript
var payload = { key: "value", count: 42 };
var options = {
  method:      "post",
  contentType: "application/json",
  payload:     JSON.stringify(payload),
  headers:     { "Authorization": "Bearer " + getToken_() },
  muteHttpExceptions: true
};
var resp = UrlFetchApp.fetch("https://api.example.com/submit", options);
```

### Sheets API v4 (when SpreadsheetApp isn't enough)

```javascript
var ssId   = SpreadsheetApp.getActiveSpreadsheet().getId();
var token  = ScriptApp.getOAuthToken();
var url    = "https://sheets.googleapis.com/v4/spreadsheets/" + ssId + "/values/Sheet1!A1:C10";
var resp   = UrlFetchApp.fetch(url, {
  headers: { "Authorization": "Bearer " + token }
});
var data = JSON.parse(resp.getContentText());
Logger.log(data.values);
```

### Webhook — POST to Slack / Discord / Zapier

```javascript
function postToSlack(message) {
  var webhookUrl = PropertiesService.getScriptProperties().getProperty("SLACK_WEBHOOK");
  UrlFetchApp.fetch(webhookUrl, {
    method:      "post",
    contentType: "application/json",
    payload:     JSON.stringify({ text: message })
  });
}
```

---

## 19. PropertiesService — Persistent State

```javascript
// Script-level (shared, permanent)
var scriptProps = PropertiesService.getScriptProperties();
scriptProps.setProperty("API_KEY", "abc123");
scriptProps.setProperty("LAST_RUN", new Date().toISOString());
var key = scriptProps.getProperty("API_KEY");
scriptProps.deleteProperty("API_KEY");
scriptProps.getProperties();   // returns all as object

// User-level (per user, permanent)
var userProps = PropertiesService.getUserProperties();
userProps.setProperty("NOTIFY_ENABLED", "true");

// Document-level (tied to this spreadsheet)
var docProps = PropertiesService.getDocumentProperties();
docProps.setProperty("VERSION", "3.0");

// Batch set
scriptProps.setProperties({ "KEY1": "val1", "KEY2": "val2" });

// Delete all
scriptProps.deleteAllProperties();
```

---

## 20. LockService — Concurrency

```javascript
// Prevent simultaneous edits in multi-user sheets
function safeWrite_(data) {
  var lock = LockService.getScriptLock();
  try {
    lock.waitLock(10000);   // wait up to 10 seconds
    // do the critical write here
    writeToSheet_(data);
    SpreadsheetApp.flush();
  } catch(e) {
    Logger.log("Could not obtain lock: " + e.message);
  } finally {
    lock.releaseLock();
  }
}
```

---

## 21. CacheService — Performance

```javascript
// Cache expensive computations (max 6 hours, max 100KB value)
var cache = CacheService.getScriptCache();

function getExpensiveData_() {
  var cached = cache.get("engine_data");
  if (cached) return JSON.parse(cached);

  var data = computeExpensiveData_();   // slow call
  cache.put("engine_data", JSON.stringify(data), 300);  // cache 5 min
  return data;
}

// Invalidate on write
function onEdit(e) {
  cache.remove("engine_data");
  // ... rest of handler
}

// User-scoped cache
var userCache = CacheService.getUserCache();
```

---

## 22. Utilities

### Dates

```javascript
var now     = new Date();
var ms      = now.getTime();
var iso     = now.toISOString();
var local   = Utilities.formatDate(now, Session.getScriptTimeZone(), "MM/dd/yyyy");
var local2  = Utilities.formatDate(now, "America/Chicago", "MMMM d, yyyy 'at' h:mm a");

// Days between
function daysBetween(d1, d2) {
  return Math.ceil((d2 - d1) / 86400000);
}

// Add days
function addDays(date, n) {
  return new Date(date.getTime() + n * 86400000);
}
```

### Encoding

```javascript
var base64  = Utilities.base64Encode("Hello");
var decoded = Utilities.base64Decode(base64);
var str     = Utilities.newBlob(decoded).getDataAsString();

var md5     = Utilities.computeDigest(Utilities.DigestAlgorithm.MD5, "data");
var sha256  = Utilities.computeDigest(Utilities.DigestAlgorithm.SHA_256, "data");
```

### Blob / File

```javascript
// Create blob from string
var blob = Utilities.newBlob("CSV content", "text/csv", "export.csv");

// Create blob from byte array
var bytes = Utilities.base64Decode(base64String);
var blob2 = Utilities.newBlob(bytes, "application/pdf", "report.pdf");

// Sleep (use sparingly — counts against execution time)
Utilities.sleep(1000);  // 1 second
```

### JSON

```javascript
var str = JSON.stringify({ key: "val" }, null, 2);
var obj = JSON.parse(str);
```

---

## 23. Error Handling & Logging

### Try/catch pattern

```javascript
function safeOperation_(fn, context) {
  try {
    return fn();
  } catch(err) {
    Logger.log("[ERROR] " + context + ": " + err.message + "\n" + err.stack);
    return null;
  }
}
```

### Logger

```javascript
Logger.log("Message");
Logger.log("Value: %s, Count: %d", myVar, count);
var logs = Logger.getLog();    // retrieve all logs as string
Logger.clear();
```

### Console (newer — shows in Stackdriver)

```javascript
console.log("Info");
console.warn("Warning");
console.error("Error");
console.time("label");
console.timeEnd("label");
```

### Toast notifications

```javascript
SpreadsheetApp.getActive().toast("Operation complete.", "Blast Plan Brain", 4);  // 4 sec
SpreadsheetApp.getActive().toast("Loading...", "", -1);   // infinite until dismissed
```

### Alert / Prompt

```javascript
var ui = SpreadsheetApp.getUi();
ui.alert("Title", "Message", ui.ButtonSet.OK);
ui.alert("Confirm?", "Are you sure?", ui.ButtonSet.YES_NO);

var result = ui.prompt("Input", "Enter value:", ui.ButtonSet.OK_CANCEL);
if (result.getSelectedButton() === ui.Button.OK) {
  var text = result.getResponseText();
}
```

---

## 24. Import / Export

### Export sheet to CSV

```javascript
function exportToCsv(sheetName) {
  var sheet = SpreadsheetApp.getActive().getSheetByName(sheetName);
  var data  = sheet.getDataRange().getValues();
  var csv   = data.map(function(row) {
    return row.map(function(cell) {
      var s = String(cell);
      if (s.indexOf(",") > -1 || s.indexOf('"') > -1 || s.indexOf("\n") > -1) {
        s = '"' + s.replace(/"/g, '""') + '"';
      }
      return s;
    }).join(",");
  }).join("\n");

  var blob   = Utilities.newBlob(csv, "text/csv", sheetName + ".csv");
  var file   = DriveApp.getRootFolder().createFile(blob);
  Logger.log("CSV URL: " + file.getUrl());
  return file.getUrl();
}
```

### Export spreadsheet as XLSX

```javascript
function exportAsXlsx() {
  var ssId = SpreadsheetApp.getActiveSpreadsheet().getId();
  var url  = "https://docs.google.com/spreadsheets/d/" + ssId + "/export?format=xlsx";
  var resp = UrlFetchApp.fetch(url, {
    headers: { "Authorization": "Bearer " + ScriptApp.getOAuthToken() }
  });
  var blob = resp.getBlob().setName("Export.xlsx");
  DriveApp.getRootFolder().createFile(blob);
}
```

### Export as PDF

```javascript
function exportAsPdf() {
  var ssId = SpreadsheetApp.getActiveSpreadsheet().getId();
  var url  = "https://docs.google.com/spreadsheets/d/" + ssId +
             "/export?format=pdf&size=A4&portrait=true&fitw=true&gridlines=false";
  var resp = UrlFetchApp.fetch(url, {
    headers: { "Authorization": "Bearer " + ScriptApp.getOAuthToken() }
  });
  DriveApp.getRootFolder().createFile(resp.getBlob().setName("Report.pdf"));
}
```

### Import CSV from Drive

```javascript
function importCsvFromDrive(fileId) {
  var file    = DriveApp.getFileById(fileId);
  var content = file.getBlob().getDataAsString();
  var rows    = Utilities.parseCsv(content);
  var sheet   = SpreadsheetApp.getActiveSheet();
  sheet.getRange(1, 1, rows.length, rows[0].length).setValues(rows);
}
```

### Import JSON from URL

```javascript
function importJson(url) {
  var resp = UrlFetchApp.fetch(url);
  var data = JSON.parse(resp.getContentText());
  // flatten and write to sheet
}
```

---

## 25. Advanced Formatting Patterns

### Border styles

```javascript
var range = sheet.getRange("A1:G10");
range.setBorder(
  true, true, true, true,   // top, left, bottom, right
  true, true,                // vertical, horizontal (inner)
  "#223047",
  SpreadsheetApp.BorderStyle.SOLID
);
// Border styles: SOLID, SOLID_MEDIUM, SOLID_THICK, DASHED, DOTTED, DOUBLE
```

### Number formats

```javascript
range.setNumberFormat("0.00");
range.setNumberFormat("$#,##0.00");
range.setNumberFormat("0%");
range.setNumberFormat("MM/dd/yyyy");
range.setNumberFormat("@");              // plain text
range.setNumberFormat("[>0]+0;[<0]-0;0"); // signed numbers
```

### Text rotation

```javascript
range.setTextRotation(45);
range.setTextRotation(-45);
range.setVerticalText(true);
```

### Merge cells

```javascript
sheet.getRange("A1:D1").merge();                  // merge all
sheet.getRange("A1:D4").mergeHorizontally();      // merge each row
sheet.getRange("A1:D4").mergeVertically();        // merge each column
sheet.getRange("A1:D1").breakApart();             // unmerge
```

### Wrap strategy

```javascript
range.setWrapStrategy(SpreadsheetApp.WrapStrategy.WRAP);
range.setWrapStrategy(SpreadsheetApp.WrapStrategy.CLIP);
range.setWrapStrategy(SpreadsheetApp.WrapStrategy.OVERFLOW);
```

### Full cell style in one pass (best practice)

```javascript
function styleCell_(range, opts) {
  if (opts.bg)     range.setBackground(opts.bg);
  if (opts.color)  range.setFontColor(opts.color);
  if (opts.size)   range.setFontSize(opts.size);
  if (opts.bold !== undefined) range.setFontWeight(opts.bold ? "bold" : "normal");
  if (opts.halign) range.setHorizontalAlignment(opts.halign);
  if (opts.valign) range.setVerticalAlignment(opts.valign);
  if (opts.font)   range.setFontFamily(opts.font);
  if (opts.wrap)   range.setWrapStrategy(opts.wrap);
  if (opts.italic) range.setFontStyle("italic");
}
```

---

## 26. Performance Optimization Checklist

| Rule | Why |
|------|-----|
| ✅ Batch all reads with `getValues()` | Each `getValue()` = 1 API call |
| ✅ Batch all writes with `setValues()` | Each `setValue()` = 1 API call |
| ✅ Call `SpreadsheetApp.flush()` once at end | Forces all pending writes |
| ✅ Use `CacheService` for repeated reads | Avoids re-reading unchanged data |
| ✅ Read only the columns you need | Don't read 20 cols when you need 3 |
| ✅ Use `getDisplayValues()` only when needed | `getValues()` is faster |
| ✅ Guard `onEdit` immediately | Prevents running on every cell |
| ✅ Avoid `Utilities.sleep()` in loops | Counts against 6-minute limit |
| ✅ Use `LockService` for multi-user writes | Prevents race conditions |
| ✅ Keep sidebar HTML lightweight | Reduces sidebar load time |
| ✅ Use `muteHttpExceptions: true` on fetch | Prevents script crash on API error |

### Execution limits

| Limit | Value |
|-------|-------|
| Script execution time | 6 minutes |
| Trigger execution time | 6 minutes |
| Email per day (MailApp) | 100 (consumer), 1500 (Workspace) |
| UrlFetchApp calls per day | 20,000 |
| Properties value size | 9 KB |
| Cache value size | 100 KB |
| SpreadsheetApp cells per write | 10M cells |

---

## 27. Security Patterns

### Never hardcode credentials

```javascript
// ❌ WRONG
var API_KEY = "sk-abc123";

// ✅ RIGHT — store in Script Properties
var API_KEY = PropertiesService.getScriptProperties().getProperty("API_KEY");
```

### Validate all inputs from sidebar

```javascript
function updateStateFromDashboard(code, newState) {
  // Validate — never trust client input
  if (typeof code !== "string" || code.trim().length === 0) return { error: "Invalid code" };
  if (!isValidState_(newState)) return { error: "Invalid state: " + newState };
  // safe to proceed
}
```

### Check authorization

```javascript
function checkOwner_() {
  var owner = SpreadsheetApp.getActiveSpreadsheet().getOwner();
  var user  = Session.getActiveUser();
  if (owner.getEmail() !== user.getEmail()) throw new Error("Unauthorized.");
}
```

### Sanitize HTML output

```javascript
function escHtml(s) {
  return String(s || "")
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;");
}
```

---

## 28. Deployment — Clasp & Version Control

### Setup clasp (local CLI)

```bash
npm install -g @google/clasp
clasp login
clasp clone <scriptId>     # pull existing project
clasp pull                 # sync remote → local
clasp push                 # sync local → remote
clasp open                 # open in browser editor
clasp deploy               # create new deployment version
clasp deployments          # list deployments
clasp logs                 # stream Stackdriver logs
```

### appsscript.json manifest

```json
{
  "timeZone": "America/Chicago",
  "dependencies": {},
  "exceptionLogging": "STACKDRIVER",
  "runtimeVersion": "V8",
  "oauthScopes": [
    "https://www.googleapis.com/auth/spreadsheets",
    "https://www.googleapis.com/auth/drive",
    "https://www.googleapis.com/auth/gmail.send",
    "https://www.googleapis.com/auth/calendar",
    "https://www.googleapis.com/auth/script.send_mail"
  ]
}
```

### Web App deployment

```javascript
function doGet(e) {
  var action = e.parameter.action;
  if (action === "getStatus") {
    var data = getEngineData_(SpreadsheetApp.openById("SS_ID"));
    return ContentService.createTextOutput(JSON.stringify(data))
      .setMimeType(ContentService.MimeType.JSON);
  }
  return ContentService.createTextOutput("OK");
}

function doPost(e) {
  var body = JSON.parse(e.postData.contents);
  // handle POST
  return ContentService.createTextOutput(JSON.stringify({ success: true }))
    .setMimeType(ContentService.MimeType.JSON);
}
```

---

## 29. Common Bugs & Fixes

| Bug | Cause | Fix |
|-----|-------|-----|
| `Cannot read property 'getValues' of null` | `getSheetByName()` returned null | Check sheet name spelling exactly |
| `TypeError: Cannot set property on undefined` | Range out of bounds | Check row/col indices are ≥ 1 |
| `Exceeded maximum execution time` | Loop with per-cell API calls | Switch to batch read/write |
| `You do not have permission` | Calling UI from time trigger | Time triggers can't call `getUi()` |
| `ReferenceError: google is not defined` | `google.script.run` used outside sidebar | Only works in HtmlService output |
| `Cannot call getValue on merged cell` | Reading merged range | Use the top-left cell of the merge |
| Old value shows after setValues | Flush not called | Add `SpreadsheetApp.flush()` |
| `onEdit` not firing | Editing via script, not user | Script edits don't fire simple `onEdit` |
| Dropdown not showing after setDataValidation | Need to flush | Call `SpreadsheetApp.flush()` |
| `getDisplayValue()` returns empty | Cell has no data | Use `getValue()` then format manually |
| Sidebar shows stale data | No refresh on re-open | Call `loadDashboard()` on every open |

---

## 30. TEMPO OS / Blast Plan Patterns

### Single active lane enforcement

```javascript
function enforceSingleActiveLane_(engine, keepRow) {
  var lastRow = engine.getLastRow();
  var keeper  = keepRow || firstInProgressRow_(engine);
  if (!keeper) return;
  var states  = engine.getRange(ENG_START_ROW, ENG_STATE_COL, lastRow - ENG_START_ROW + 1, 1).getValues();
  var changed = false;
  for (var i = 0; i < states.length; i++) {
    var row = i + ENG_START_ROW;
    if (row === keeper) continue;
    if (String(states[i][0] || "").trim().toUpperCase() === "IN PROGRESS") {
      states[i][0] = "NOT STARTED";
      changed = true;
    }
  }
  if (changed) engine.getRange(ENG_START_ROW, ENG_STATE_COL, states.length, 1).setValues(states);
}
```

### State cascade pattern (onEdit → trigger → engine → views)

```
onEdit(e)
  └── handleTriggerEdit_(e)        ← validates, finds engine row
        └── engine.setState()      ← writes to Blast Engine
              └── handleStateChangeNoNotify_()  ← side effects
                    └── refreshAllViews()       ← rebuilds all 3 tabs
```

### Health check pattern

```javascript
function getHealthIssues_(ss, data) {
  var issues = [];
  // 1. Check required sheets exist
  // 2. Check exactly 1 IN PROGRESS row
  // 3. Check no invalid states
  // 4. Check no overdue non-forward rows
  // 5. Check pace is ahead
  // 6. Check pending SME count
  return issues;   // empty = healthy
}
```

### State color convention (TEMPO)

| State | Color | Meaning |
|-------|-------|---------|
| MET STANDARD | `#FFD700` Gold | Class done |
| ASSESSMENT SUBMITTED | `#93c5fd` Light Blue | Pending SME |
| IN PROGRESS | `#22c55e` Green | Currently enrolled |
| DID NOT MEET | `#c4a882` Light Brown | Kicked back |
| NOT STARTED | `#ef4444` Red | Not yet begun |

### Pace calculation

```javascript
var elapsed  = Math.max((today - PROG_START) / (7 * 86400000), 0.1);  // weeks
var actPace  = (completedCredits / elapsed).toFixed(2);                 // credits/week actual
var weeksLeft = daysLeft / 7;
var reqPace  = weeksLeft > 0 ? (remainingCredits / weeksLeft).toFixed(2) : "—";
var paceGap  = (parseFloat(actPace) - parseFloat(reqPace)).toFixed(2);
```

### Projected finish

```javascript
function getProjectedFinish_(completedCredits, remainingCredits, today) {
  var elapsed     = Math.max((today - PROG_START) / (7 * 86400000), 0.1);
  var pace        = completedCredits / elapsed;
  if (pace <= 0) return null;
  var weeksNeeded = remainingCredits / pace;
  return new Date(today.getTime() + weeksNeeded * 7 * 86400000);
}
```

---

*YVYC · TEMPO OS · Google Sheets Elite Reference v1.0*
