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

Link na externu url
-------------------
