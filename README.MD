# SDK ONHANDBI

[![Downloads](https://img.shields.io/npm/dt/@onhand-bi-dev/sdk.svg?style=flat&color=success)](https://www.npmjs.com/package/@onhand-bi-dev/sdk)
![Libraries.io dependency status for latest release](https://img.shields.io/librariesio/release/npm/@onhand-bi-dev/sdk)
[![Build Size](https://img.shields.io/bundlejs/size/@onhand-bi-dev/sdk)](https://pkg-size.dev/@onhand-bi-dev/sdk)
[![Version](https://img.shields.io/npm/v/@onhand-bi-dev/sdk?style=flat&color=success)](https://www.npmjs.com/package/@onhand-bi-dev/sdk)
<a href="https://pkg-size.dev/@onhand-bi-dev/sdk"><img src="https://pkg-size.dev/badge/install/103906" title="Install size for @onhand-bi-dev/sdk"></a>
<a href="https://pkg-size.dev/@onhand-bi-dev/sdk"><img src="https://pkg-size.dev/badge/bundle/24854" title="Bundle size for @onhand-bi-dev/sdk"></a>

## Installation

```bash
npm i @onhand-bi-dev/sdk
# or
# yarn add @onhand-bi-dev/sdk
```

## Import

```js
import OHBI from "@onhand-bi-dev/sdk";
```

## Examples

### Auth

```js
const accessToken = "<your access token>";
const OHBI_SDK = await OHBI.newClient(accessToken);
```

### Get List Report

This method retrieves a list of reports.

#### Parameters:

page (number, optional): The page number of the report list. Default is 1.
searchText (string, optional): The search text to filter reports. Default is an empty string.
Returns:

A Promise that resolves to an array of Report objects representing the reports.

#### Example:

```js
OHBI_SDK.getReports(1, "search text")
  .then((reports) => {
    // Process the list of reports
    console.log("Reports:", reports);
  })
  .catch((error) => {
    console.log("Error retrieving reports:", error);
  });
```

### Get Report

This method retrieves a specific report by its ID.

#### Parameters:

reportId (number): The ID of the report.
isOwner (boolean, optional): Indicates whether the client is the owner of the report. Default is false.
Returns:

A Promise that resolves to a Report object representing the report, or null if the report is not found.

#### Example:

```js
const reportId = 12345;

OHBI_SDK.getReport(reportId)
  .then((report) => {
    if (report) {
      // Process the report
      console.log("Report:", report);
    } else {
      console.log("Report not found");
    }
  })
  .catch((error) => {
    console.log("Error retrieving report:", error);
  });
```

### Load Report

This method loads a report into an HTML element identified by the specified tag ID.

#### Parameters:

reportId (number): The ID of the report to load.
tagId (string): The ID of the HTML element where the report should be loaded.
isOwner (boolean, optional): Indicates whether the client is the owner of the report. Default is false.
Example:

```js
const reportId = 12345;
const tagId = "report-container";

OHBI_SDK.loadReport(reportId, tagId, true);
```

### Load App

This method loads an app into an HTML element identified by the specified tag ID.

#### Parameters:

appId (number): The ID of the app to load.
tagId (string): The ID of the HTML element where the app should be loaded.
isOwner (boolean, optional): Indicates whether the client is the owner of the app. Default is false.

#### Example:

```js
const appId = 54321;
const tagId = "app-container";

client.loadApp(appId, tagId, false);
```

### Get App

This method retrieves a specific app by its ID.

#### Parameters:

appId (number): The ID of the app.
isOwner (boolean, optional): Indicates whether the client is the owner of the app. Default is false.

#### Returns:

A Promise that resolves to an AppModel object representing the app, or null if the app is not found.

#### Example:

```js
const appId = 54321;

OHBI_SDK.getApp(appId)
  .then((app) => {
    if (app) {
      // Process the app
      console.log("App:", app);
    } else {
      console.log("App not found");
    }
  })
  .catch((error) => {
    console.log("Error retrieving app:", error);
  });
```

### Get List App

This method retrieves a list of apps.

#### Parameters:

page (number, optional): The page number of the app list. Default is 1.
searchText (string, optional): The search text to filter apps. Default is an empty string.
isOwner (boolean, optional): Indicates whether the client is the owner of the app. Default is false.

#### Returns:

A Promise that resolves to an array of AppModel objects representing the apps.

#### Example:

```js
OHBI_SDK.getApps(1, "search text", false)
  .then((apps) => {
    // Process the list of apps
    console.log("Apps:", apps);
  })
  .catch((error) => {
    console.log("Error retrieving apps:", error);
  });
```
