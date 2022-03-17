.. _doc_laravel_tailwind:

Tailwind css
============

Instalacia TailwindCSS
=====================================

**TailwindCSS** sa stal veľmi populárnym nielen u vývojárov **Laravel**, ale aj vývojárov **Vue**.

**Tailwind** vám umožňuje vytvárať aplikácie a webové stránky bez toho, aby ste museli opustiť svoj html.

Najprv musíme nainštalovať potrebné závislosti:

.. code-block:: console

	npm install -D tailwindcss@latest postcss@latest autoprefixer@latest

Konfiguracia TailwindCSS
========================

Teraz môžeme vytvoriť konfiguračný súbor tailwind, ktorý môžeme použiť na rozšírenie predvolených nastavení **TailwindCSS** :

.. code-block:: console

	npx tailwindcss init

Tým sa v našom projekte vytvorí nový súbor ``tailwind.config.js``.

Potom musíme nakonfigurovať **webpack** na spracovanie inštalácie tailwind:

.. code-block:: php

	const mix = require("laravel-mix");

	mix.js("resources/js/app.js", "public/js")
		.vue()
		.postCss("resources/css/app.css", "public/css", [require("tailwindcss")]);

