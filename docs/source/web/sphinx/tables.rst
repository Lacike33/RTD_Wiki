.. _doc_sphinx_tables:

Tabulky
============================

Su dostupne 3 moznosti :

Table
-----

.. table:: Truth table for "not"
   :widths: auto
   :align: center

   =====  =====
     A    not A
   =====  =====
   False  True
   True   False
   =====  =====

Rozpoznávajú sa nasledujúce možnosti:

* **align** - "left", "center", "right"
* **width** - length , percentage
* **widths** - "auto", "grid", list of integers

CSV table
---------

.. csv-table:: Frozen Delights!
   :header: "Treat", "Quantity", "Description"
   :widths: 15, 10, 30

   "Albatross", 2.99, "On a stick!"
   "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
   crunchy, now would it?"
   "Gannet Ripple", 1.99, "On a stick!"

Možnosti:

* align - "left", "center", or "right"
The horizontal alignment of the table. (New in Docutils 0.13)
* delim - char | "tab" | "space" [4]
A one-character string[5] used to separate fields. Defaults to , (comma). May be specified as a Unicode code point; see the unicode directive for syntax details.
* encoding - string
The text encoding of the external CSV data (file or URL). Defaults to the document's input_encoding.
escapechar
A one-character[5] string used to escape the delimiter or quote characters. May be specified as a Unicode code point; see the unicode directive for syntax details. Used when the delimiter is used in an unquoted field, or when quote characters are used within a field. The default is to double-up the character, e.g. "He said, ""Hi!"""
filestring (newlines removed)
The local filesystem path to a CSV data file.
headerCSV data
Supplemental data for the table header, added independently of and before any header-rows from the main CSV data. Must use the same CSV format as the main CSV data.
header-rowsinteger
The number of rows of CSV data to use in the table header. Defaults to 0.
keepspaceflag (empty)
Treat whitespace immediately following the delimiter as significant. The default is to ignore such whitespace.
quotechar
A one-character string[5] used to quote elements containing the delimiter or which start with the quote character. Defaults to " (quote). May be specified as a Unicode code point; see the unicode directive for syntax details.
stub-columnsinteger
The number of table columns to use as stubs (row titles, on the left). Defaults to 0.
urlstring (whitespace removed)
An Internet URL reference to a CSV data file.
* widths - integer [integer...] or "auto"
A list of relative column widths. The default is equal-width columns (100%/#columns).

"auto" delegates the determination of column widths to the backend (LaTeX, the HTML browser, ...).
* width - length or percentage
List table
----------

.. list-table:: Frozen Delights!
   :widths: 15 10 30
   :header-rows: 1

   * - Treat
     - Quantity
     - Description
   * - Albatross
     - 2.99
     - On a stick!
   * - Crunchy Frog
     - 1.49
     - If we took the bones out, it wouldn't be
       crunchy, now would it?
   * - Gannet Ripple
     - 1.99
     - On a stick!

Možnosti:
