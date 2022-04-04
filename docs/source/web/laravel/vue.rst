.. _doc_laravel_vue:

******
Vue.js
******

**Vue.js** (nebo jen Vue; vyslovuje se stejně jako view) je open-source progresivní JavaScriptový framework pro vytváření uživatelských rozhraní.Začlenění do projektů, které používají jiné JavaScriptové knihovny je s Vue snadné, protože je navržen tak, aby mohl být přijímán postupně. Vue může také fungovat jako webový aplikační framework, na kterém je možné vytvářet pokročilé Single-page applications. Zakladnu dokumentaciu najdes [TU](https://vuejs.org/).


Stavia na štandarde HTML, CSS a JavaScript a poskytuje deklaratívny a komponentný programovací model, ktorý vám pomáha efektívne rozvíjať používateľské rozhrania, či už jednoduché alebo zložité.

VUE 2
=====

Implementacia
-------------

Pre implementaciu cisteho **Vue 2** bez dalsich medzi frameworkov je optimalne vykonat starsim sposobom a to nasledovnym balickom :

.. code:: console

	composer require laravel/ui

.. warning::

	POZOR!!! Plati pre verziu 6.x a vyssiu pre VUE 2 .

Nasledne je nutne si vybrat reaktivny framework a v nasom pripade to je **Vue.js**

::

	// Generate basic scaffolding...

	php artisan ui bootstrap
	php artisan ui vue
	php artisan ui react

Po nainstalovaniu VUE dependencies je mozne vygenerovat login registration :

::

	// Generate login / registration scaffolding...

	php artisan ui bootstrap --auth
	php artisan ui vue --auth
	php artisan ui react --auth

Po uspesnej instalacii staci spustit :

.. code-block:: console

	npm install && npm run dev

Layout pouzitie
---------------

.. code:: php

	@extends('layouts.app')

	@section('content')
		<example-component></example-component>
	@endsection


.. warning::

	Nasledujuci js prihod do stranky :
		::

			<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

Struktura projektu
------------------

Zakladnym suborom v Laravel aplikacii je ``resources\js\app.js`` kde registrujeme VUE komponenty ako aj identifikujem zakladnu ROOT kostru vue priestoru.

Je nutne zadeklarovat hlavny HTML pre VUE instanciu nasledovnym sposobom :

.. code:: html

	<div id="vue-app">
		Hello Vue !
	</div>

K danemu kodu je nutne vytvorit uz zmienenu VUE instanciu :

.. code-block::

	<script type="text/javascript">
		var app = new Vue({
			el: '#vue-app'
		});
	</script>

Komponenty
----------

.. code-block:: php

	<?js

	Vue.component('example-component', require('./components/ExampleComponent.vue'));

	/**
	 * Aplikacia musi mat vo VIEW html element s ID <div id="app">
	 */

	<div id="app">
	  Hello {{ name }}.
	</div>

	<script>
	const app = new Vue({
		el: '#app',
		data: {
			name: 'Vašo'
		}
	});
	</script>

.. _doc_laravel_vue3:

VUE 3
=====

Instalacia
----------

Ak používate Laravel od **6.x** vyššie, možno ste natrafili na balík **Laravel/ui**, pomocou ktorého by sme mohli nainštalovať Bootstrap, ako aj React alebo Vue.

Pre aktualnu verziu Laravel **9.x** neexistuje žiadny balík pre instalaciu **Vue 3**, ale existuje pomerne jednoduchý spôsob, ako to urobiť.

Najprv nainštalujte závislosti potrebné pre Vue 3:

.. code-block:: console

	npm install --save vue@next && npm install --save-dev vue-loader@next

Konfigurcia
-----------

Po instalacii musíme povedať **webpacku**, aby skompiloval aj naše súbory vue.

Môžeme to urobiť otvorením súboru ``webpack.mix.js`` a pridaním nasledujúceho riadku ::

	const mix = require("laravel-mix");

	mix.js("resources/js/app.js", "public/js")
		.vue() //new
		.postCss("resources/css/app.css", "public/css", [
			//
	]);

Nasledne spustím inštaláciu npm :, po ktorej nasleduje npm run dev.

.. code-block:: console

	npm install && npm run dev.


Po vykonani vsetkych predchadzajucich krokoch mam laravel projekt pripraveny s VUE 3 frameworkom.

Projekt
-------

Vytvorime koreňovu komponentu, ktora bude obsahovať celú našu aplikáciu **Vue**.

Vytvorte nový súbor ``App.vue`` v priečinku ``resources/js`` s nasledujúcim označením:

.. code-block:: html+php

	<template>
		<div>
			<h1>Vue 3 App</h1>
		</div>
	</template>

Teraz musíme prispôsobiť našu ``app.js`` v ``resources/js``, aby sme mohli využívať náš súbor vue:

.. code-block::

	require("./bootstrap");

	import { createApp } from "vue";

	import App from "./App.vue";

	createApp(App).mount("#app");


Najprv importujeme metódu **createApp()**, ktorá je pre vývojárov Vue nová. Pomocou toho môžeme vytvoriť novú inštanciu Vue.

Potom importujeme náš súbor Vue a vytvoríme novú inštanciu Vue a pripojíme ju k prvku s ID „app“.

Taktiez ale mozeme  konstantnu premennu ktoru podobne pripojime k prvku s ID ako v predchadzajucom pripade

.. code-block::

	import { createApp } from "vue";

	import Home from "./components/Home.vue";
	import Dashboard from "./components/Dashboard.vue";

	const app = createApp({
	  components: {
		Home,
		Dashboard
	  }
	});

	app.mount("#app");

Teraz vytvorte prvok, ktorý má toto id. Aby sme to dosiahli, môžeme odstrániť štandardné označenie nachádzajúce sa v našom súbore ``welcome.blade.php`` a nahradiť ho týmto:

.. code-block:: html+php

	<!DOCTYPE html>
	<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
		<head>
			<meta charset="utf-8">
			<meta name="viewport" content="width=device-width, initial-scale=1">

			<title>Laravel</title>

			<!-- Fonts -->
			<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&display=swap" rel="stylesheet">
		</head>
		<body>
			<div id="app"></div>
		</body>
		<script src="{{ asset('js/app.js') }}"></script>
	</html>

Ako môžete vidieť, máme **div** s id *app*, ktorá bude nahradená našou aplikáciou Vue.

Nižšie máme značku skriptu, ktorá odkazuje **na app.js**, ktorú nemáme v ``resources/js``, ale v našom priečinku ``public/js``. Tento súbor je konečným výsledkom procesu vytvárania nášho webového balíka.

Predtým, ako to urobíme, musíme znova spustiť proces zostavovania, pretože sme v skutočnosti nespracovali súbory Vue, ktoré sme vytvorili.

.. code-block:: console

	npm run dev

.. note::

	Aby sme nemuseli spúšťať ``npm run dev`` zakaždým, keď vykonáme zmenu, môžeme spustiť ``npm run watch``, ktorý nám umožní spustiť proces zostavovania hneď po uložení zmien.

Import CSS from
---------------

V pripade ze mame hotovy FE, tak nema zmysel buildovat stale nove CSS a hotovy dizajn si vieme v hlavnom js subore ``app.js`` importovat

.. code-block::

	import './asset/css/mystyle.css'

Vue router
==========

.. code-block:: CONSOLE

	npm install vue-router@4

Po instalacii samotneho **Vue Router** je potrebne nakonfigurovat zakladnu kostru obdobne ako pri zavedeni **VUE** a to v subore
``app.js`` alebo ``main.js`` pripadne podla vlastneho uvazenia.

.. code-block:: javascript

	require("./bootstrap");

	import { createApp } from "vue";
	import Home from "./components/Home.vue";
	import Dashboard from "./components/Dashboard.vue";

	const app = createApp({
	  components: {
		Home,
		Dashboard
	  }
	});

	app.mount("#app");

Pri tvorbe SPA aplikacie, je vhodne pri pouziti vsetky ``<a>`` elemetoch pouzit ``<router-link>``.
Vtedy pri preklikoch sa nerefreshuju stranky.


.. toctree::
   :maxdepth: 3
   :name: laravel
