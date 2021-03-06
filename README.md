# PHP library for read data of spreadsheet files
PHP library to read spreadsheet files.
Exported from code.google.com/p/php-spreadsheetreader

License: [GNU LGPL](http://www.gnu.org/licenses/lgpl.html)


It supports OpenDocument Spreadsheet (.ods), Microsoft Excel 97/2000 (.xls), and CSV (.csv), and Text with tab-separated or patterns (.txt).

It's very simple.

```php
require_once 'SpreadsheetReaderFactory.php';

$spreadsheetsFilePath = 'test.ods'; //or test.xls, test.csv, etc.
$reader = SpreadsheetReaderFactory::reader($spreadsheetsFilePath);

$sheets = $reader->read($spreadsheetsFilePath);

echo $sheets[0][0][0];
```

Use this command to anonymously check out the latest project source code:

`svn checkout http://php-spreadsheetreader.googlecode.com/svn/ php-spreadsheetreader`

### Revision 26

IMPORTANT!

I rewrite my Excel reader by pure PHP code. Instead of invoking the external reader, jxl.

See also Issue 1.

### Revision 24

Add method: asXml(). This return $sheets as Xml string (Excel XML format). Therefor you can save it or put into a download stream.

### Revision 21

It can return sheets as associative array.

### Revision 16

Support MS Excel 2000/XP's XML file. Note: Excel 2000/XP's XML file format is a single XML file, and different from Office OpenXML.

### Bug fixed

* Let factory detect file-type case-insensitive.

* bug of SpreadsheetReader_Excel: Sometimes, data will contain non-readable chars (I put in $ignoreChar). XML parser will occur a parse error. So we need to strip those non-readable chars.

* It only output tables which have content in their first cell. Now fix it.

* When read with READ_ASSOC, it forgets to skip the first Row(fields header) after 2nd sheet. 
