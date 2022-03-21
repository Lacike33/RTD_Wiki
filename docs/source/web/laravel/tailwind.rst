.. _doc_laravel_tailwind:

************
Tailwind css
************

Instalacia TailwindCSS
----------------------

**TailwindCSS** sa stal veľmi populárnym nielen u vývojárov **Laravel**, ale aj vývojárov **Vue**.

**Tailwind** vám umožňuje vytvárať aplikácie a webové stránky bez toho, aby ste museli opustiť svoj html.

Najprv musíme nainštalovať potrebné závislosti:

.. code-block:: console

	npm install -D tailwindcss postcss autoprefixer

Konfiguracia TailwindCSS
------------------------

Teraz môžeme vytvoriť konfiguračný súbor tailwind, ktorý môžeme použiť na rozšírenie predvolených nastavení **TailwindCSS** :

.. code-block:: console

	npx tailwindcss init

Tým sa v našom projekte vytvorí nový súbor ``tailwind.config.js``.

Mix configuration
-----------------

Potom musíme nakonfigurovať **webpack** na spracovanie inštalácie tailwind:

.. code-block:: php

	const mix = require("laravel-mix");

	mix.js("resources/js/app.js", "public/js")
		.vue()
		.postCss("resources/css/app.css", "public/css", [require("tailwindcss")]);

Configure your template paths
-----------------------------

Add the paths to all of your template files in your ``tailwind.config.js`` file :

.. code-block::

	module.exports = {
	  content: [
		"./resources/**/*.blade.php",
		"./resources/**/*.js",
		"./resources/**/*.vue",
	  ],
	  theme: {
		extend: {},
	  },
	  plugins: [],
	}

Tailwind directives
-------------------

Aby ste mohli vo svojom projekte použiť pomocné triedy tailwind, môžeme ich jednoducho pridať do nášho súboru
``resources/css/app.css`` :

.. code-block:: css

	@tailwind base;
	@tailwind components;
	@tailwind utilities;

Tieto direktívy tailwind sú preberané našimi procesmi zostavovania webpacku a triedy obslužných programov tailwind sú umiestnené do výsledného vytvoreného súboru css.

Nakoniec môžeme pridať šablónu so štýlmi na stránku ``welcome.blade.php``, aby sme mohli použiť štýly v našom projekte:

.. code-block:: html+php

	<!DOCTYPE html>
	<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
		<head>
			<meta charset="utf-8">
			<meta name="viewport" content="width=device-width, initial-scale=1">

			<title>Laravel</title>

			<!-- Fonts -->
			<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&display=swap" rel="stylesheet">
			<link rel="stylesheet" href="{{ asset('css/app.css') }}">
		</head>
		<body>
			<div id="app"></div>
		</body>
		<script src="{{ asset('js/app.js') }}"></script>
	</html>

Možno budete musieť znova reštartovať vývojový server a/alebo reštartovať proces buildovania.

Teraz môžeme do nášho komponentu pridať niekoľko pomocných tried, aby sme otestovali, že všetko funguje:

.. code-block:: html+php

	<template>
		<div class="flex justify-center mt-24">
			<h1 class="text-2xl font-bold text-gray-700">Vue 3 App</h1>
		</div>
	</template>
