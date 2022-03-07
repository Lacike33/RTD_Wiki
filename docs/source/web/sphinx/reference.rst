.. _doc_sphinx_reference:

Reference
=========

V podstate sphinx dokumentacia umoznuje viacero pristupov k odkazovaniu na ci uz interne alebo externe zdroje :

1. Odkazovanie na interny dokument v projekte
1. Odkazovanie na internu sekciu v akomkolvek dokumente
1. Odkazovanie na externu url

Link na dokument
----------------

Odkaz na určený dokument ``:doc:``; názov dokumentu môže byť špecifikovaný v absolútnom alebo relatívnom zmysle.

Napríklad, ak sa odkaz ``:doc:`parrot``` vyskytuje v sketches/indexe dokumentu, potom odkaz odkazuje na sketches/parrot.

Ak je odkaz ``:doc:`/people``` alebo ``:doc:`../people```, odkaz odkazuje na ľudí.

Ak nie je uvedený žiadny explicitný text odkazu (ako zvyčajne: ``:doc:`Členovia Monty Python </people>```), titulok odkazu bude názvom daného dokumentu.

.. _doc_sphinx_reference_section:

Link na sekciu
--------------

Pri použití **ref** je možné vygenerovať krížový odkaz s definovaným iba názvom, za predpokladu, že je uvedený explicitný názov.

Príklad:

.. code::

	See :ref:`this code snippet <this-py>` for an example.

Na podporu krížových odkazov na ľubovoľné miesta v akomkoľvek dokumente sa používajú štandardné štítky ReST.

.. note::

	Názvy štítkov musia byť jedinečné v celej dokumentácii.

	Referenčné štítky musia začínať podčiarkovníkom.
	Pri odkazovaní na štítok je potrebné vynechať podčiarknutie (pozri príklady vyššie).

Existujú dva spôsoby, ako môžete odkazovať na štítky:

1. Ak štítok umiestnite priamo pred názov sekcie, môžete naň odkazovať pomocou ``:ref:`názov-názvu```.

Napríklad:

.. code::

	.. _my-reference-label:

	Section to cross-reference
	--------------------------

	This is the text of the section.

	It refers to the section itself, see :ref:`my-reference-label`.

Rola ``:ref:`` potom vygeneruje odkaz na sekciu s názvom odkazu „Sekcia na krížový odkaz“.

Funguje to rovnako dobre, keď sú sekcia a odkaz v rôznych zdrojových súboroch.

2. Na štítky, ktoré nie sú umiestnené pred názvom sekcie, možno stále odkazovať, ale odkazu musíte prideliť explicitný názov pomocou tejto syntaxe: ``:ref:`Názov odkazu <názov-názvu>```.

Použitie **ref** sa odporúča pred štandardnými odkazmi reStructuredText na sekcie (ako je ```Názov sekcie`_``), pretože funguje naprieč súbormi.
Keď sa zmenia nadpisy sekcií, zobrazí sa varovanie ak sú nesprávne.

Link na externu url
-------------------
