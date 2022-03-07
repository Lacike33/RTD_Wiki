.. _doc_sphinx_theming:

HTML Theming
============

Sphinx poskytuje množstvo hotovych tem pre HTML a formáty založené na HTML.

.. note::

	Táto časť poskytuje informácie o používaní už existujúcich tém HTML.
	Ak si chcete vytvoriť vlastnú tému, pozrite si tému `Vývoj témy HTML <https://www.sphinx-doc.org/en/master/development/theming.html>`_.

Sphinx podporuje zmenu vzhľadu svojho HTML výstupu prostredníctvom tém. Téma je kolekcia HTML šablón, štýlov a iných statických súborov.
Okrem toho má konfiguračný súbor, ktorý určuje, z ktorej témy sa má dediť, aký štýl zvýraznenia sa má použiť a aké možnosti existujú na prispôsobenie vzhľadu a štýlu témy.

Témy sú navrhnuté tak, aby nezohľadňovali projekt, takže ich možno bez zmeny použiť pre rôzne projekty.


Použitie témy
-------------

Použitie témy v Sphinx je jednoduché.
Keďže ich nie je potrebné inštalovať, stačí nastaviť konfiguračnú hodnotu html_theme.

Ak chcete napríklad povoliť klasickú tému, pridajte do ``conf.py`` nasledovné:

.. code-block:: python

	html_theme = "classic"

Pre danu temu môžete tiež nastaviť možnosti špecifické pre tému pomocou konfiguračnej hodnoty ``html_theme_options``.
Tieto možnosti sa vo všeobecnosti používajú na zmenu vzhľadu a štýlu témy.

Ak chcete napríklad umiestniť bočný panel na pravú stranu a čierne pozadie pre panel vzťahov (panel s navigačnými odkazmi v hornej a dolnej časti stránky), pridajte nasledujúci ``conf.py`` :

.. code-block:: python

	html_theme_options = {
    "rightsidebar": "true",
    "relbarbgcolor": "black"
	}

Oblubene témy
-------------

Medzi najoblubenejsie temy patria nasledujuce :

.. toctree::
   :maxdepth: 3
   :name: theme

   theme/rtd
   theme/booktheme
