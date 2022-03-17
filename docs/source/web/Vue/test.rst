.. _doc_vue_laravel:

Laravel
-------

**Vue.js** (nebo jen Vue; vyslovuje se stejně jako view) je open-source progresivní JavaScriptový framework pro vytváření uživatelských rozhraní.Začlenění do projektů, které používají jiné JavaScriptové knihovny je s Vue snadné, protože je navržen tak, aby mohl být přijímán postupně. Vue může také fungovat jako webový aplikační framework, na kterém je možné vytvářet pokročilé Single-page applications. Zakladnu dokumentaciu najdes [TU](https://vuejs.org/).


Stavia na štandarde HTML, CSS a JavaScript a poskytuje deklaratívny a komponentný programovací model, ktorý vám pomáha efektívne rozvíjať používateľské rozhrania, či už jednoduché alebo zložité.


```
composer require laravel/ui
```
Nasledne je nutne si vybrat reaktivny framework a v nasom pripade to je VUE
```
// Generate basic scaffolding...

php artisan ui bootstrap
php artisan ui vue
php artisan ui react
```

Po nainstalovaniu VUE dependencies je mozne vygenerovat login registration
```
// Generate login / registration scaffolding...

php artisan ui bootstrap --auth
php artisan ui vue --auth
php artisan ui react --auth
```

Po uspesny instalaciach staci spustit
```
npm install
a
npm run dev
```

Nasledne pouzitie:
```
@extends('layouts.app')

@section('content')
    <example-component></example-component>
@endsection
```

** Nevyhnutne **

Nasledujuci js prihod do stranky
```
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

## Struktura

Zakladnym suborom v Laravel aplikacii je ```resources\js\app.js``` kde registrujeme VUE komponenty ako aj identifikujem zakladnu ROOT kostru vue priestoru. Je nutne zadeklarovat hlavny HTML pre VUE instanciu nasledovnym sposobom :
```
<div id="vue-app">
    Hello Vue !
</div>
```
 a k danemu kodu je nutne vytvorit uz zmienenu VUE instanciu
```
<script type="text/javascript">
    var app = new Vue({
        el: '#vue-app'
    });
</script>
```
## Properties

**data**
* (jejíž hodnotou musí být funkce, která vrací javascriptový objekt) slouží, jak její název napovídá, k uložení dat / informací ke komponentě.
*
```
data () {
   return {
      premenna: 'value'
   }
}

```
**mounted**

**computed**

**methods**

## Komponenty
```
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

```


### Vseobecny postup instalacie NPM package: ###

1. Nainstaluj komponentu cez NPM

```
npm install --save "NAZOV_KOMPONENTY"
```
2. Registruj komponentu v subore ```app.js```
   Registrovat kompenentu mozeme podla potreby :

* GLOBALNE

-- globalnu registraciu robime v zakladnom subore ```resources/assets/js/app.js```

```
   // import nainstalovaneho pluginu

   import VueFormWizard from 'vue-form-wizard'
   import 'vue-form-wizard/dist/vue-form-wizard.min.css'

   // registracia komponenty
   Vue.use(VueFormWizard)

```

* LOKALNE

-- robime priamo v inej komponente

```
   import {FormWizard, TabContent} from 'vue-form-wizard'
   import 'vue-form-wizard/dist/vue-form-wizard.min.css'

   //component code
   components: {
     FormWizard,
     TabContent
   }
```

## Existujuce VUE form komponenty

** Multisteps formulare**

* [**vue-form-wizard**](https://www.npmjs.com/package/vue-form-wizard)
* [**vue-good-wizard**](https://www.npmjs.com/package/vue-good-wizard)

** Flash spravy**

* [**vue-flash-message**](https://www.npmjs.com/package/vue-flash-message)
* [**Vuex Flash**](https://www.npmjs.com/package/vuex-flash)

## Mnou vytvorene komponenty ##

## VUE dirctives ##

### v-show ###

- pouziva sa pre zobrazenie elementu

```
#!vue


```

### v-model ###

- pouziva sa pre previazanie input pola s nejakou premennou

```
#!vue

<input type="text" v-model="data">
```

### v-model ###

- v cykle sa vypisu data

```
#!vue


```
### @click ###

- odchytava event na kliknutie, zvykne sa odkazovat na metodu

```
#!vue


```

### @submit ###

- potvrdenie formulara a odoslanie dat

```
#!vue


```
pre zrusenie defaultne funkcionality pri odoslani formulara je potrebne pouzi ```@submit.prevent```

.. toctree::
   :maxdepth: 3
   :name: laravel

   laravel
