.. _doc_laravel_vue:

******
Vue.js
******

**Vue.js** (nebo jen Vue; vyslovuje se stejně jako view) je open-source progresivní JavaScriptový framework pro vytváření uživatelských rozhraní.Začlenění do projektů, které používají jiné JavaScriptové knihovny je s Vue snadné, protože je navržen tak, aby mohl být přijímán postupně. Vue může také fungovat jako webový aplikační framework, na kterém je možné vytvářet pokročilé Single-page applications. Zakladnu dokumentaciu najdes [TU](https://vuejs.org/).


Stavia na štandarde HTML, CSS a JavaScript a poskytuje deklaratívny a komponentný programovací model, ktorý vám pomáha efektívne rozvíjať používateľské rozhrania, či už jednoduché alebo zložité.

Implementacia
=============

Pre implementaciu cisteho Vue bez dalsich medzi frameworkov je optimalne vykonat starsim sposobom a to nasledovne :

.. code:: console

	composer require laravel/ui

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

..code-block:: console

	npm install && npm run dev

Layout pouzitie
===============

..code-block:: php

	@extends('layouts.app')

	@section('content')
		<example-component></example-component>
	@endsection


..warning::

	Nasledujuci js prihod do stranky :
		::

			<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

Struktura projektu
==================

Zakladnym suborom v Laravel aplikacii je ``resources\js\app.js`` kde registrujeme VUE komponenty ako aj identifikujem zakladnu ROOT kostru vue priestoru.

Je nutne zadeklarovat hlavny HTML pre VUE instanciu nasledovnym sposobom :

..code-block:: html

	<div id="vue-app">
		Hello Vue !
	</div>

K danemu kodu je nutne vytvorit uz zmienenu VUE instanciu :

..code-block:: javascript

	<script type="text/javascript">
		var app = new Vue({
			el: '#vue-app'
		});
	</script>

Komponenty
==========

..code-block:: javascript

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

.. toctree::
   :maxdepth: 3
   :name: laravel
