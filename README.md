# test_files

Test files supporting [SheetJS projects](https://github.com/SheetJS/sheetjs)

Instead of polluting those repos with large binary files, they are stored here.

All files contained in root directory are covered under the Apache 2.0 license.
The `Makefile` can pull files from other projects, which are covered under
separate licenses (see below).

The files in the 201\* / biff\* subdirectories are derivative outputs generated
using the specified version of Microsoft Excel.  Each derivative file of an
external file is clearly marked with a prefix associated with the source
(followed by an underscore), and original files do not have any of the source
prefixes.  Each derivative file is released under the same terms as the original
file (and all derivatives of original files are released under the Apache 2.0
License).

# Excel 2016 for Mac Automation

In previous versions of Excel for Mac, the app could write to any user-writable
directory.  In 2016, the output fiile must be contained in the quarantine
`~/Library/Containers/com.microsoft.excel`.  As a result, the AppleScript has
been changed to write to the aforementioned directory and the accompanying shell
script copies from the quarantine.

# Manifest

`formula_stress_test` uses every single function available in Excel 2011 in some
formula.  It includes a pivot table as well as array formulae, inline arrays,
errors, booleans, and other cell types and formula elements.

`comments_stress_test` tests various types of comments and functions.  The XLS
version uses VBA to extract comments.

`number_format` tests every implied format from ECMA-376 as well as every format
available within the Excel 2011 UI.  Ultimately there will be international
versions to test certain features (some require an east-Asian version -- if you
are reading this and can generate test files, please contribute!)

`number_format_entities` tests number formats with XML entities. There are known
issues with Google Sheets exporting tricky formats (Excel refuses to open these
files).

`number_format_*` tests the number_format files in various locales (the original
files were opened in Excel 2013 with the given locale and saved). In Excel 2013,
only the BIFF5 workbooks are written with the specific codepages.  For example,
`number_format_estonian` uses code page 1257.

`large_strings` tests large strings and a large shared string table.  Larger
strings are programmatically generated using `CONCATENATE` while the shared
string table was pulled from <http://longwords.org/longwordslist.html>

`RkNumber` tests all styles of RkNumber records.  Records were verified by hand.

`merge_cells` tests vertical, horizontal, and rectangular merged cells.

`LONumbers` tests LO number format deviations from Excel.  The `LONumbers.xls*`
files are directly from LibreOffice 4.1.4.2.  These files were opened in Excel,
"repaired", and saved as `LONumbers-EXCELVERSION.xls*`.

`rich_text_stress` tests various types of rich text, applying formatting to the
entire cell as well as parts of the cell.

`named_ranges` tests named ranges (including valid and invalid expressions).

`custom_properties` tests custom properties

`xlsx-stream-d-date-cell` tests the ECMA-376 `d` date type

`pivot_table_test` tests different types of pivot tables

`pivot_table_named_range` tests pivot tables with named ranges

`AutoFilter` tests different uses of AutoFilter

`BlankSheetTypes` tests different types of blank sheets

`ErrorTypes` tests different types of errors

`NumberFormatCondition` tests different conditions in number formats

`protect_stress_test_xml` tests the different sheet protection modes

`calendar_stress_test` tests the different calendars (B1/B2) and years (b/e/y).
Due to size and format constraints, XLSB contains the full record while the
other formats are truncated to 65536 rows.

`hyperlink_stress_test_2011` tests different types of external hyperlinks

`internal_link` tests different types of internal hyperlinks

`hyperlink_no_rels` tests a non-relationship hyperlink (h/t @keemy)

`text_and_numbers` considers text and numbers (generated from a Hebrew version
of Excel h/t @elad).

`cell_style_simple` tests simple cell styles

`formulae_test_simple` tests simple shared and array formulae

`password_*` tests different password modes in different versions. Name format:
`password_<ExcelVersion>_<Bits>_<Desc>`.

`sushi` tests the sushi character U+1F363 (h/t @uzulla for identifying issue)

`defined_names_simple` tests sheet-level and workbook-level defined names

`smart_tags_2007` tests some basic smart tag functionality (from Excel 2007)

`A4X_*` tests Dimensions in various XLS writers.  Initially created for gnumeric
bug 733771: <https://bugzilla.gnome.org/show_bug.cgi?id=733771>

`numfmt_*` tests various number formatting features (h/t @sysarchitect et al)

`write` represents the original array of arrays writing example, as well as
output in various plaintext formats as generated by Excel 2011.

`phonetic_text` uses phonetic text (h/t @tgfjt, <http://git.io/phonetic-text>)

`row_height` includes rows of varying heights.

`column_width` includes columns of varying widths.

`sized_boxen` combines row heights and column widths.

`sheet_visibility` demonstrates visible + hidden + very hidden sheets.

`page_margins_2016` uses standard and custom page margins (from Excel 2016)

`outline` tests the various row and column outline levels (from Excel 2013)

`author_snowman` demonstrates a unicode snowman (U+2603) author.

`wtf_path` uses internal paths with `wtf/` prefix rather than `xl/`.

`defined_names_unicode` uses unicode defined names (h/t @feuxfollets1013)

`freeze` tests different freeze panes configurations

# Getting External Test Files

Note: releases from <https://github.com/sheetjs/test_files/releases> include all
external test files.  These are made available for systems where the build
scripts do not run (including bare Windows installations).

All external test files are pulled using the Makefile and fall under separate
licensing terms (as described below).  None of the files directly contained in
this repo are encumbered by external licenses.  They are acquired by cloning:

- Github repos are cloned using SVN access (just pulls the relevant directory)
- Bitbucket repos are cloned using HG access

`apachepoi` pulls only the spreadsheet test battery from the Apache POI project:
<https://poi.apache.org/spreadsheet/index.html>.
At the time of this writing, it is covered under Apache License, version 2.0:
<http://www.apache.org/licenses/LICENSE-2.0>

`xlrd` pulls the test battery from xlrd project: <http://www.python-excel.org/>
At the time of this writing, it is covered under BSD License.

`excel-reader-xlsx` pulls the test battery from the excel-reader-xlsx project:
<https://github.com/jmcnamara/excel-reader-xlsx/>
At the time of this writing, it is covered under Perl Artistic License.

`openpyxl` pulls the test battery from the openpyxl project:
<http://openpyxl.readthedocs.org/>
At the time of this writing, it is covered under the MIT License

`spout` pulls the test battery from the spout project:
<https://packagist.org/packages/box/spout>
At the time of this writing, it is covered under the Apache License, version 2.0

`pyExcelerator` pulls the test battery from the pyExcelerator project:
<https://pypi.python.org/pypi/pyExcelerator>
At the time of this writing, it is covered under the BSD 4-clause License

`jxls-*` pulls the test battery from the jxls project:
<http://jxls.sourceforge.net/>
At the time of this writing, it is covered under the GNU Lesser GPL License

`roo` pulls the test battery from the roo project: <http://roo.rubyforge.org/>
At the time of this writing, the test files are covered under the MIT License

`spreadsheet-parsexlsx` pulls the test battery from the ParseXLSX project:
<https://metacpan.org/release/Spreadsheet-ParseXLSX>
At the time of this writing, it is covered under the MIT (X11) License

`oo34xml` pulls the XML test battery from the OpenOffice project:
<http://www.openoffice.org/>
At the time of this writing, it is covered under Apache License, version 2.0

`libreoffice` pulls the test files from the LibreOffice project:
<http://cgit.freedesktop.org/libreoffice/contrib/test-files/>
At the time of this writing, it is covered under the GNU Lesser GPL License v3
Note: due to flakiness with the original LibreOffice source code repository host
(bug tracker https://bugs.freedesktop.org/show_bug.cgi?id=85756), the tree is
manually mirrored at <https://github.com/SheetJS/libreoffice_test-files>

`ootest` pulls test files at <http://www.openoffice.org/sc/testdocs/index.html>
Since the license terms are unclear, they are not pulled in the default targets.
To pull these files, you must explicitly run `make ootest`.

`phpexcel_bad_cfb_dir.xls` exhibits broken CFB structure.

# Requests for Removal

This repo includes derivatives of files from external sources.  According to the
respective license terms, the authors of the external sources allege that the
artifacts are indeed covered under the same terms.  This project uses files
according to those terms.

External sources are expected to ensure that they are not violating license
terms.  However, from time to time, they may add test files from contributors
that did not create the files or obtain permission.  We are not actively
monitoring discussions pertaining to removal requests from other sources, but if
you find your content and would like to see it removed, we will investigate.

To submit a request, first reach out to the original source and give some time
for them to respond. If they remove the content, file an issue in this repo's
issue tracker and email <sheetjs@gmail.com> (subject "removal request"). In the
email, forward the original communications and link to the issue in the
original project issue tracker. Unless the original project recognizes that the
content is yours (admitting that the content cannot be released according to
their license terms), no action will be taken.

If you have reached out to the original source and have not received a reply in
30 days, raise an issue in this repo tracker and send an email with subject
"external license violation", forwarding proof of initial attempt to contact.
We will reach out to the external source.  If we do not receive a reply in 30
days, the content will be removed in future commits.

# License

All files contained in this repository are licensed under the Apache 2 License.
Files external to this repo (acquired via `make`) are licensed under separate
terms (as indicated in the External Test Files section)

[![ghit.me](https://ghit.me/badge.svg?repo=sheetjs/js-xlsx)](https://ghit.me/repo/sheetjs/js-xlsx)

[![Analytics](https://ga-beacon.appspot.com/UA-36810333-1/SheetJS/js-xlsx?pixel)](https://github.com/SheetJS/js-xlsx)
