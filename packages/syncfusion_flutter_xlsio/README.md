![syncfusion_flutter_xlsio_banner](https://cdn.syncfusion.com/content/images/FTControl/Flutter-XlsIO-Banner.png)

# Syncfusion Flutter XlsIO

Syncfusion Flutter XlsIO is a feature rich and high-performance non-UI Excel library written natively in Dart. It allows you to add robust Excel functionalities to Flutter applications.

## Overview

The Excel package is a non-UI and reusable Flutter library to create Excel documents programmatically with cell values, built-in styles, cell formatting, formulas, charts, and images. The creation of Excel file are in XLSX (Excel 2007 and above) format.

**Disclaimer:** This is a commercial package. To use this package, you need to have either a Syncfusion Commercial License or Syncfusion Community license. For more details, please check the [LICENSE](LICENSE) file.

**Note:** Our packages are now compatible with Flutter for Web. However, this will be in Beta until Flutter for Web becomes stable.

![XlsIO Overview](https://cdn.syncfusion.com/content/images/FTControl/Flutter-XlsIO-Overview.png)

## Table of contents
- [Key features](#key-features)
- [Get the demo application](#get-the-demo-application)
- [Other useful links](#other-useful-links)
- [Installation](#installation)
- [Getting started](#getting-started)
    - [Create a simple Excel document](#create-a-simple-excel-document)
    - [Add text, number, and datetime values](#add-text-number-and-datetime-values)
    - [Add formulas](#add-formulas)
    - [Apply formatting](#apply-formatting)
    - [Add images](#add-images)
    - [Add charts](#add-charts)
    - [Add hyperlinks](#add-hyperlinks)
    - [Manipulate rows and Columns](#manipulate-rows-and-columns)
    - [Protect workbook and worksheets](#Protect-workbook-and-worksheets)
- [Support and feedback](#support-and-feedback)
- [About Syncfusion](#about-syncfusion)

## Key Features

The following are the key features of Syncfusion Flutter XlsIO.

*	Create simple Excel document in Flutter
*	Apply Excel cell formatting
*	Add formulas to Excel worksheet cells
*	Add images to Excel worksheet
*	Add charts to Excel worksheet
* Add hyperlinks to Excel worksheet
* Manipulate rows and columns of Excel worksheet
* Add protection to Excel document.

## Get the demo application

Explore the full capability of our Flutter widgets on your device by installing our sample browser application from the following app stores, and view sample’ codes in GitHub.

<p align="center">
  <a href="https://play.google.com/store/apps/details?id=com.syncfusion.flutter.examples"><img src="https://cdn.syncfusion.com/content/images/FTControl/google-play.png"/></a>
  <a href="https://apps.apple.com/us/app/syncfusion-flutter-ui-widgets/id1475231341"><img src="https://cdn.syncfusion.com/content/images/FTControl/apple-button.png"/></a>
</p>
<p align="center">
  <a href="https://github.com/syncfusion/flutter-examples"><img src="https://cdn.syncfusion.com/content/images/FTControl/GitHub.png"/></a>
  <a href="https://flutter.syncfusion.com"><img src="https://cdn.syncfusion.com/content/images/FTControl/web_sample_browser.png"/></a>  
</p>

## Other useful links

Take a look at the following to learn more about Syncfusion Flutter XlsIO:

* [User guide documentation]()
* [Knowledge base](https://www.syncfusion.com/kb)

## Installation

Install the latest version from [pub](https://pub.dev/packages/syncfusion_flutter_xlsio/install)

## Getting started

Import the following package to your project to create a Excel document from scratch.

```dart
import 'package:syncfusion_flutter_xlsio/xlsio.dart';

```

### Create a simple Excel document

Add the following code to create a simple Excel document.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
workbook.worksheets[0];
// Save the document.
List<int> bytes = workbook.saveAsStream();
File('CreateExcel.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

### Add text, number, and datetime values

Use the following code to add text, number and datetime values to Excel worksheet.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];
//Add Text.
sheet.getRangeByName('A1').setText('Hello World');
//Add Number
sheet.getRangeByName('A3').setNumber(44);
//Add DateTime
sheet.getRangeByName('A5').setDateTime(DateTime(2020,12,12,1,10,20));
// Save the document.
List<int> bytes = workbook.saveAsStream();
File('AddingTextNumberDateTime.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

### Add formulas

Use the following code to add formulas to Excel worksheet cells.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];
//Setting value in the cell
sheet.getRangeByName('A1').setNumber(22);
sheet.getRangeByName('A2').setNumber(44);

//Formula calculation is enabled for the sheet
sheet.enableSheetCalculations();

//Setting formula in the cell
sheet.getRangeByName('A3').setFormula('=A1+A2');

// Save the document.
List<int> bytes = workbook.saveAsStream();
File('AddingFormula.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

### Apply formatting

This section covers the various formatting options in a cells.

**Apply GlobalStyle**

Use the following code to add and apply global style to the Excel worksheet cells.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Defining a global style with all properties.
final Style globalStyle = workbook.styles.add('style');
globalStyle.backColor = '#37D8E9';
globalStyle.fontName = 'Times New Roman';
globalStyle.fontSize = 20;
globalStyle.fontColor = '#C67878';
globalStyle.italic = true;
globalStyle.bold = true;
globalStyle.underline = true;
globalStyle.wrapText = true;
globalStyle.hAlign = HAlignType.left;
globalStyle.vAlign = VAlignType.bottom;
globalStyle.rotation = 90;
globalStyle.borders.all.lineStyle = LineStyle.Thick;
globalStyle.borders.all.color = '#9954CC';
globalStyle.setNumberFormat = '_(\$* #,##0_)';;

//Apply GlobalStyle
sheet.getRangeByName('A1').cellStyle = globalStyle;
// Save the document.
List<int> bytes = workbook.saveAsStream();
File('ApplyGlobalStyle.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

**Apply Build-in Formatting**

Use the following code to apply build-in style to to the Excel worksheet cells.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Applying Number format.
sheet.getRangeByName('A1').builtInStyle = BuiltInStyles.linkedCell;

// Save the document.
List<int> bytes = workbook.saveAsStream();
File('ApplyBuildInStyle.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

**Apply NumberFormat**

Use the following code to apply number format to to the Excel worksheet cells.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Applying Number format.
final Range range = sheet.getRangeByName('A1');
range.setNumber(100);
range.numberFormat = '\S#,##0.00';

// Save the document.
List<int> bytes = workbook.saveAsStream();
File('ApplyNumberFormat.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```


### Add images

Syncfusion Flutter XlsIO supports only PNG and JPEG images. Refer to the following code to add images to Excel worksheet.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Adding a picture
final List<int> bytes = File('image.png').readAsBytesSync();
final Picture picture = sheet.picutes.addStream(1, 1, bytes);

// Save the document.
List<int> bytes = workbook.saveAsStream();
File('AddingImage.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

### Add charts

Import the following package to your project to create charts in Excel document from scratch.

```dart
import 'package:syncfusion_officechart/officechart.dart';

```

Use the following code to add charts to Excel worksheet.

```dart
// Create a new Excel document.
final Workbook workbook = new Workbook();
//Accessing worksheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Setting value in the cell.
sheet.getRangeByName('A1').setText('John');
sheet.getRangeByName('A2').setText('Amy');
sheet.getRangeByName('A3').setText('Jack');
sheet.getRangeByName('A4').setText('Tiya');
sheet.getRangeByName('B1').setNumber(10);
sheet.getRangeByName('B2').setNumber(12);
sheet.getRangeByName('B3').setNumber(20);
sheet.getRangeByName('B4').setNumber(21);

// Create an instances of chart collection.
final ChartCollection charts = ChartCollection(sheet);

// Add a chart to the collection.
final Chart chart = charts.add();

//Set Chart Type.
chart.chartType = ExcelChartType.column;

//Set data range in the worksheet.
chart.dataRange = sheet.getRangeByName('A1:B4');

// Save the document.
List<int> bytes = workbook.saveAsStream();
File('ExcelCharts.xlsx').writeAsBytes(bytes);
//Dispose the workbook.
workbook.dispose();

```

### Add hyperlinks

Use the following code to add hyperlinks to Excel worksheet.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

//Creating a Hyperlink for a Website.
final Hyperlink hyperlink = sheet.hyperlinks.add(sheet.getRangeByName('A1'),
    HyperlinkType.url, 'https://www.syncfusion.com');
hyperlink.screenTip =
    'To know more about Syncfusion products, go through this link.';
hyperlink.textToDisplay = 'Syncfusion';

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('Hyperlinks.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

### Manipulate rows and Columns

This section covers how rows and columns are manipulated in Excel Worksheets.

**Apply Autofits**

Use the following code to apply autofits to single cells of the Excel worksheet.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

final Range range = sheet.getRangeByName('A1');
range.setText('WrapTextWrapTextWrapTextWrapText');
range.cellStyle.wrapText = true;

final Range range1 = sheet.getRangeByName('B1');
range1.setText('This is long text');

// AutoFit applied to a single row
sheet.autoFitRow(1);

// AutoFit applied to a single Column.
sheet.autoFitColumn(2);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFit.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

Use the following code to apply autofits to multiple cells of the Excel worksheet.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1:D1');
range.setText('This is Long Text');
final Range range1 = sheet.getRangeByName('A2:A5');
range1.setText('This is Long Text using AutoFit Columns and Rows');
range1.cellStyle.wrapText = true;

// Auto-Fit column the range
range.autoFitColumns();

// Auto-Fit row the range
range1.autoFitRows();

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('AutoFits.xlsx').writeAsBytes(bytes);
workbook.dispose();

```
**Insert/Delete Rows and Colums**

Use the following code to insert rows and columns to the Excel worksheet.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

Range range = sheet.getRangeByName('A1');
range.setText('Hello');

range = sheet.getRangeByName('B1');
range.setText('World');

// Insert a row
sheet.insertRow(1, 1, ExcelInsertOptions.formatAsAfter);

// Insert a column.
sheet.insertColumn(2, 1, ExcelInsertOptions.formatAsBefore);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('InsertRowandColumn.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

Use the following code to delete rows and columns of Excel worksheet.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

Range range = sheet.getRangeByName('A2');
range.setText('Hello');

range = sheet.getRangeByName('C2');
range.setText('World');

// Delete a row
sheet.deleteRow(1, 1);

// Delete a column.
sheet.deleteColumn(2, 1);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('DeleteRowandColumn.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

### Protect workbook and worksheets

This section covers the various protection options in the Excel document.

**Protect Workbook**

Use the following code to protect workbook of Excel document.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1');
range.setText('WorkBook Protected');

final bool isProtectWindow = true;
final bool isProtectContent = true;

// Protect Workbook
workbook.protect(isProtectWindow, isProtectContent, 'password');

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('WorkbookProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

**Protect Worksheets**

Use the following code to protect worksheets in the Excel document.

```dart
// Create a new Excel Document.
final Workbook workbook = Workbook();

// Accessing sheet via index.
final Worksheet sheet = workbook.worksheets[0];

// Assigning text to cells
final Range range = sheet.getRangeByName('A1');
range.setText('Worksheet Protected');

// ExcelSheetProtectionOption
final ExcelSheetProtectionOption options = ExcelSheetProtectionOption();
options.all = true;

// Protecting the Worksheet by using a Password
sheet.protect('Password', options);

// Save and dispose workbook.
final List<int> bytes = workbook.saveAsStream();
File('WorksheetProtect.xlsx').writeAsBytes(bytes);
workbook.dispose();

```

## Support and feedback

* For any other queries, contact our [Syncfusion support team](https://www.syncfusion.com/support/directtrac/incidents/newincident) or post the queries through the [Community forums](https://www.syncfusion.com/forums). You can also submit a feature request or a bug through our [Feedback portal](https://www.syncfusion.com/feedback/flutter).
* To renew the subscription, click [renew](https://www.syncfusion.com/sales/products) or contact our sales team at sales@syncfusion.com | Toll Free: 1-888-9 DOTNET.

## About Syncfusion

Founded in 2001 and headquartered in Research Triangle Park, N.C., Syncfusion has more than 20,000 customers and more than 1 million users, including large financial institutions, Fortune 500 companies, and global IT consultancies.

Today we provide 1,000+ controls and frameworks for web ([ASP.NET Core](https://www.syncfusion.com/aspnet-core-ui-controls), [ASP.NET MVC](https://www.syncfusion.com/aspnet-mvc-ui-controls), [ASP.NET WebForms](https://www.syncfusion.com/jquery/aspnet-web-forms-ui-controls), [JavaScript](https://www.syncfusion.com/javascript-ui-controls), [Angular](https://www.syncfusion.com/angular-ui-components), [React](https://www.syncfusion.com/react-ui-components), [Vue](https://www.syncfusion.com/vue-ui-components), and [Blazor](https://www.syncfusion.com/blazor-components)), mobile ([Xamarin](https://www.syncfusion.com/xamarin-ui-controls), [Flutter](https://www.syncfusion.com/flutter-widgets), [UWP](https://www.syncfusion.com/uwp-ui-controls), and [JavaScript](https://www.syncfusion.com/javascript-ui-controls)), and desktop development ([WinForms](https://www.syncfusion.com/winforms-ui-controls), [WPF](https://www.syncfusion.com/wpf-ui-controls), and [UWP](https://www.syncfusion.com/uwp-ui-controls)). We provide ready-to-deploy enterprise software for dashboards, reports, data integration, and big data processing. Many customers have saved millions in licensing fees by deploying our software.
