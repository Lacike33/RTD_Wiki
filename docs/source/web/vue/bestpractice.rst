Best practice
=============

Form
----

Pouzitie elementu ``<form>`` je mozne aj vo vue ale je takmer nevyhnute pridat osetrenie na refresh formulara ::

	<form @submit.prevent="MOJA_METODA"

REF
---

Referenciu pouzivama na identifikaciu konkretneho elementu, a to tak ze do elementu pridame tag ``ref=VLASTNY_NAZOV`` a potom vieme vo funkciach pouzit :

.. code-block:: console

	this.$refs.VLASTNY_NAZOV.value = ''
	this.$refs.VLASTNY_NAZOV.focus()
