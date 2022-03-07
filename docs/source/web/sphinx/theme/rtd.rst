.. _doc_sphinx_theme_rtd:

Read the Docs Sphinx Theme
==========================

Táto téma Sphinx bola navrhnutá tak, aby používateľom dokumentácie na stolných aj mobilných zariadeniach poskytla skvelú čitateľskú skúsenosť.

Táto téma sa bežne používa s projektmi na **Read the Docs**, ale môže pracovať s akýmkoľvek projektom Sphinx.

Dokumentacia je dostupna `TU <https://sphinx-rtd-theme.readthedocs.io/en/stable/#>`_.

Instalacia a aktivacia témy
---------------------------

Nainštaluj balík (alebo ho pridajte do svojho súboru ``requirements.txt``):

.. code:: console

	$ pip install sphinx_rtd_theme

Vloz do suboru ``conf.py`` :

.. code:: python

	import sphinx_rtd_theme

	extensions = [
		'sphinx_rtd_theme',
	]

	html_theme = "sphinx_rtd_theme"

.. note::

	Pridanie tejto témy ako rozšírenia umožňuje lokalizáciu reťazcov tém vo vašom preloženom výstupe.

	Ak tieto reťazce nie sú preložené vo vašom výstupe, buď nám chýbajú lokalizované reťazce pre vaše miestne nastavenie, alebo používate starú verziu témy.

Via Download
------------

.. warning::

	Inštalácia priamo zo zdroja úložiska je zastaraná a neodporúča sa. Od vydania 3.0.0 nebudú do úložiska zahrnuté statické aktíva.

Stiahni balik z repozitára sphinx_rtd_theme/sphinx_rtd_theme do vašej dokumentácie na docs/_themes/sphinx_rtd_theme a potom pridajte do svojho súboru Sphinx ``conf.py`` nasledujúce dve nastavenia:

.. code:: python

	html_theme = "sphinx_rtd_theme"
	html_theme_path = ["_themes", ]
