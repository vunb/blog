---
title: Một số thư viện xử lý Excel - Dotnet Core
date: 2020-12-01T16:30:52+07:00
draft: false
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- TIL
categories:
- dotnetcore
---

# 1. ExcelDataReader

Lightweight and fast library written in C# for reading Microsoft Excel files

## Main Features

* Support Excel file format: OpenXml, BIFF8, BIFF5, BIFF4, BIFF3, BIFF2, CSV

## References

* https://github.com/ExcelDataReader/ExcelDataReader
* https://www.nuget.org/packages/ExcelDataReader

# 2. NPOI

This project is the .NET version of POI Java project. With NPOI, you can read/write Office 2003/2007 files very easily.

## Main Features

* It's totally free to use
* Cover most features of Excel (cell style, data format, formula and so on)
* Supported formats: xls, xlsx, docx.
* Designed to be interface-oriented (take a look at NPOI.SS namespace)
* Support not only export but also import
* Real successful cases all over the world
* huge amout of basic examples
* Works on both Windows and Linux How to use NPOI in Linux

## System Requirements

* .NET Standard 2.0 (.NET Core)
* .NET Framework 4.0 and above

## References

* https://github.com/tonyqus/npoi/wiki/Getting-Started-with-NPOI
* https://github.com/nissl-lab/npoi
* https://github.com/nissl-lab/npoi-examples


# 3. EPPlus

EPPlus 5-Excel spreadsheets for .NET

## Main Features

* Support all Excel 2019 chart types with the new, modern styling
* Insert/Delete ranges in worksheets and rows/cols in tables
* Extended support for Pivot tables - Filters, calculated columns and support for shared caches
* Pivot table- and table- slicers
* Improvements of the formula calculation engine and over 100 new supported functions
* Threaded comments with support for mentions
* Support for importing dynamic/ExpandoObject to worksheets
* Support for exporting data from worksheets to files and DataTable
* Async methods for I/O operations
* Themes, Filters, Ignore errors

## System Requirements

* N/A

## References

* https://github.com/EPPlusSoftware/EPPlus
* https://www.epplussoftware.com/Developers/Features
