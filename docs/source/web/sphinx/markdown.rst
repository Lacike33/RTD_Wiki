.. _doc_sphinx_markdown:

Markdown
========

**Markdown** je ľahký značkovací jazyk so zjednodušenou syntaxou formátovania obyčajného textu.
Existuje v mnohých syntakticky odlišných príchutiach. Na podporu dokumentácie založenej na Markdown môže Sphinx použiť **MyST-Parser**.

Instalacia
----------

Pre pouzitie markdownu vo vlastnom projekte postupujte nasledovne :

1. Nainstaluj Markdown parser **MyST-Parser**

.. code-block:: console

	$ pip install --upgrade myst-parser

1. Pridaj **MyST-Parser** do extension v konfiguracii projektu ``conf.py``

.. code-block:: ini

	extensions = ['myst_parser']

.. note::

	MyST-Parser vyzaduje Sphinx 2.1 alebo novsi.
