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
   "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't becrunchy, now would it?"
   "Gannet Ripple", 1.99, "On a stick!"

Možnosti:

* align - "left", "center", or "right"

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
     - If we took the bones out, it wouldn't be crunchy, now would it?
   * - Gannet Ripple
     - 1.99
     - On a stick!

Možnosti:
