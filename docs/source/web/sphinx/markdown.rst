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

2. Pridaj **MyST-Parser** do extension v konfiguracii projektu ``conf.py``

.. code-block:: ini

	extensions = ['myst_parser']

.. note::

	MyST-Parser vyzaduje Sphinx 2.1 alebo novsi.

3. Ak chcete použiť súbory Markdown s inými príponami ako .md, upravte premennú **source_suffix**.Nasledujúci príklad konfiguruje Sphinx na analýzu všetkých súborov s príponami .md a .txt ako Markdown:

.. code-block:: python

	source_suffix = {
		'.rst': 'restructuredtext',
		'.txt': 'markdown',
		'.md': 'markdown',
	}

4. MyST-Parser môžete ďalej nakonfigurovať tak, aby umožňoval vlastnú syntax, ktorú štandardná CommonMark nepodporuje.
Viac v dokumentácii `MyST-Parser <https://myst-parser.readthedocs.io/en/latest/using/syntax-optional.html>`_.

Zbierka rozšírení Sphinx
------------------------

Nástroje v ekosystéme Sphinx na písanie krásnych online kníh a dokumentov:

* `sphinx-copybutton <https://sphinx-copybutton.readthedocs.io/>`_
* `sphinx-togglebutton <https://sphinx-togglebutton.readthedocs.io/>`_
* `sphinx-panels <https://sphinx-panels.readthedocs.io/en/latest/>`_
