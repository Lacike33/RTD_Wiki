******
Test
******

**Vue.js** (nebo jen Vue; vyslovuje se stejně jako view) je open-source progresivní JavaScriptový framework pro vytváření uživatelských rozhraní.Začlenění do projektů, které používají jiné JavaScriptové knihovny je s Vue snadné, protože je navržen tak, aby mohl být přijímán postupně. Vue může také fungovat jako webový aplikační framework, na kterém je možné vytvářet pokročilé Single-page applications. Zakladnu dokumentaciu najdes [TU](https://vuejs.org/).


Stavia na štandarde HTML, CSS a JavaScript a poskytuje deklaratívny a komponentný programovací model, ktorý vám pomáha efektívne rozvíjať používateľské rozhrania, či už jednoduché alebo zložité.

.. note::

	Detail pre implemnentaciu **Vue.js** do laravel projektu popisujem v sekcii :ref:`doc_laravel_vue`.



Vseobecny postup instalacie NPM Packages
========================================

1. Nainstaluj komponentu cez NPM

::

	npm install --save "NAZOV_KOMPONENTY"

2. Registruj komponentu v subore ``app.js``

   Registrovat kompenentu mozeme podla potreby :

**GLOBALNE**

-- globalnu registraciu robime v zakladnom subore ``resources/assets/js/app.js``

::
   // import nainstalovaneho pluginu

   import VueFormWizard from 'vue-form-wizard'
   import 'vue-form-wizard/dist/vue-form-wizard.min.css'

   // registracia komponenty
   Vue.use(VueFormWizard)

**LOKALNE**

-- robime priamo v inej komponente

::
   import {FormWizard, TabContent} from 'vue-form-wizard'
   import 'vue-form-wizard/dist/vue-form-wizard.min.css'

   //component code
   components: {
     FormWizard,
     TabContent
   }

Existujuce VUE form komponenty
==============================

** Multisteps formulare**

* `vue-form-wizard <https://www.npmjs.com/package/vue-form-wizard>`_
* `vue-good-wizard <https://www.npmjs.com/package/vue-good-wizard>`_

** Flash spravy**

* `vue-flash-message <https://www.npmjs.com/package/vue-flash-message>`_
* `Vuex Flash <https://www.npmjs.com/package/vuex-flash>`_

Mnou vytvorene komponenty

VUE dirctives
	v-show - pouziva sa pre zobrazenie elementu
	v-model - pouziva sa pre previazanie input pola s nejakou premennou
	@click - odchytava event na kliknutie, zvykne sa odkazovat na metodu
	@submit - potvrdenie formulara a odoslanie dat

..note::
	Pre zrusenie defaultne funkcionality pri odoslani formulara je potrebne pouzi ``@submit.prevent``

.. toctree::
   :maxdepth: 3
   :name: laravel

   test
