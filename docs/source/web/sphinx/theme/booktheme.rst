.. _doc_sphinx_theme_booktheme:

Book Theme
==========

Téma ** Book Theme Sphinx** s čistým dizajnom, podporou interaktívneho obsahu a moderným vzhľadom a štýlom ako z knihy.

Dokumentacia je dostupna `TU <https://sphinx-book-theme.readthedocs.io/en/stable/index.html>`_.

Get started
-----------

.. note::

	Táto dokumentácia a nižšie uvedené príklady sú napísané pomocou **MyST Markdown**, čo je forma markdown, ktorá funguje so Sphinx.

	Blizsie informacie su popisane na stranke :doc:`Konfiguracia markdown <../markdown>`

**Predpoklady**

Mali by ste byť relatívne oboznámení s ekosystémom Sphinx a mali by ste ho mať nainštalovaný lokálne vo svojom počítači.

Instalacia a aktivacia témy
---------------------------

Najprv si nainštalujte tému **sphinx-book-theme** s pip:

.. code:: console

	$ pip install sphinx-book-theme

Potom aktivuj tému v konfigurácii Sphinx ``conf.py`` :

.. code:: python

	html_theme = "sphinx_book_theme"

Tým sa aktivuje téma Book Sphinx pre vašu dokumentáciu.

.. note::

	Možno budete musieť zakomentovať svoju konfiguráciu html_theme_options v závislosti od vašej predchádzajúcej témy.

Zdrojové úložisko
-----------------

Pridajte do svojej témy tlačidlo zdrojového úložiska.

Existuje niekoľko spôsobov, ako si môžete prispôsobiť tému Book Sphinx.

V tomto priklade ukazeme  pridanie úložiska GitHub.

Ak chcete pridať tlačidlo, ktoré odkazuje na úložisko vašej dokumentácie, pridajte nasledujúcu konfiguráciu do ``conf.py``.

.. code:: python

	html_theme_options = {
		"repository_url": "https://github.com/{your-docs-url}",
		"use_repository_button": True,
	}
