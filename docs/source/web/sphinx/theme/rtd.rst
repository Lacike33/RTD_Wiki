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

Konfiguracia
------------

Nasledujúce možnosti možno definovať v súbore ``conf.py`` vášho projektu pomocou konfiguračnej možnosti **html_theme_options**.

Napríklad:

.. code:: python

	html_theme_options = {
		'analytics_id': 'G-XXXXXXXXXX',  #  Provided by Google in your dashboard
		'analytics_anonymize_ip': False,
		'logo_only': False,
		'display_version': True,
		'prev_next_buttons_location': 'bottom',
		'style_external_links': False,
		'vcs_pageview_mode': '',
		'style_nav_header_background': 'white',
		# Toc options
		'collapse_navigation': True,
		'sticky_navigation': True,
		'navigation_depth': 4,
		'includehidden': True,
		'titles_only': False
	}

Table of contents options
:::::::::::::::::::::::::

Nasledujúce voľby menia spôsob, akým direktívy toctree generujú navigáciu v dokumentácii.
