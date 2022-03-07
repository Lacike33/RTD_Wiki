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

Bočný panel
-----------

Existuje niekoľko hlavných oblastí stránky, ktoré si môžete prispôsobiť podľa témy knihy.
Najbežnejší je primárny bočný panel (štandardne na ľavej strane stránky).

Prvky bočného panela sú definované ako šablóny HTML podľa Sphinx, rozšírení Sphinx a aktuálnej témy.
Pomocou konfigurácie ``html_sidebars`` môžete určiť, ktoré stránky by mali obsahovať prvky bočného panela.
Tento krok v tomto návode preskočíme, ale detaili su popisane v `Control the left sidebar items <https://sphinx-book-theme.readthedocs.io/en/stable/customize/sidebar-primary.html#sidebar-primary-items>`_ .

**Prispôsobme si logo našej stránky**

Za týmto účelom upravíme možnosti konfigurácie ``html_logo`` a ``html_title``.

Ak chcete pridať logo lokality, postupujte takto:

1. Vložte obrázok do koreňového adresára dokumentácie (napr. myimage.png).
2. Pridajte do súboru ``conf.py`` riadok, ktorý vyzerá takto:

.. code:: python

   html_logo = "path/to/myimage.png"

Ďalej prispôsobíme názov stránky.

Ak to chcete urobiť, pridajte do súboru ``conf.py`` riadok, ktorý vyzerá takto:

.. code:: python

   html_logo = "html_title = "My site title""

Okraje stranky
--------------

Existuje niekoľko špeciálnych druhov obsahu, ktoré táto téma podporuje, prevažne inšpirovaných štýlmi tém Tufte CSS.

Jeden druh obsahu je obsah na okraji. To vám umožní „vysunúť“ obsah na okraj stránky, na okraje.

Pridajte na stránku nejaký obsah okrajov pridaním nasledujúcej smernice (napísanej pomocou :doc:`MyST Markdown <markdown>`).

.. code::

	{margin} Look, some margin content!
	On wider screens, this content will pop out to the side!

Na širokouhlých obrazovkách sa obsah okrajov vysunie na stranu stránky a umožní obsahu pod ním pohybovať sa nahor.

To vám umožní poskytnúť ďalšie informácie bez prerušenia toku informácií.

Existuje mnoho ďalších vecí, ktoré môžete robiť s témou knihy Sphinx.
Teraz, keď ste začali, pozrite si ďalšie časti vľavo, kde sa dozviete viac o tom, ako ho používať.
