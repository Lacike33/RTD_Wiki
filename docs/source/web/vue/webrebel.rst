********
Webrebel
********

Vue 2 vs. Vue 3
===============

Zakladne rozdiely medzi Vue2 a Vue3 :

* vytvorenie instancie VUE (create App)
* eventBus
* zrusili sa filtre pouzivane cez pipe | (staci prerobit na methods)
* inline template (toto som este nepouzival)

Zakladna kostra VUE 3
=====================

.. code-block::

	<script>

		import VueComponent from 'cesta_k_suboru/VueComponent.vue';

		export default {

			// vsetky pouzite komponenty vo VUE komponente
			components: {
				VueComponent,
			},

			// data ktore pouzivana v komponente
			data {
				return {
					legend: 'Meno Legendy',
					newObject: '',
				}
			},

			// sekcia pri vzniknutom komponnete
			created() {
				window.eventBus.on('NAZOV_GLOBALNEHO_EVENTU', (event) => (this.newObject = event) )
			},

			// metody a funkcie pouzite v komponente
			methods: {
				showAlert() {
					alert('Legenda : ' + this.legend)
				},
				formSubmited() {
					this.$emit('new-object', this.newObject)
				},
			},

		}
	</script>

Events
------

Eventy si vstavane direktivy vo vue a pouziva sa prefix ``@``

@input
^^^^^^
Udalost ked nastane zmena na input fielde

**Zrusenie refreshu prehliadaca**

::

	@submit.prevent

**Nastavenie metody po potvrdeni form** ::

	@submit.prevent="newMethod"

Nasledne je potrebne vytvorit vo VUE komponente aj metodu

.. code-block::

	<script>
		export default {
		  methods: {
			newMethod() {
				alert('FORM submited!')
			},
		  },
		}
	</script>

Kumunikacia z rodica na potomka
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Data z rodica do podradenej komponenty (potomka) sa data posielaju cez ``props``

.. code-block::

	<vue-component :myName="Meno v premennej myName" />

Kumunikacia z potomka na rodica
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
V pripade odchytenie eventu potomok vie tuto udalost resp. po odchyteni poslat spravu rodicovi cez ``$emit`` ::

	<script>
		export default {
		  methods: {
			newMethod(e) {
				this.$emit('NAZOV_VLASTNEHO_EVENTU', data)
			},
		  },
		}
	</script>

Po udalisti sa zavola metoda, na ktoru dokaze rodic reagovat po pridani takeho eventu do svojej implementacie komponentu ::

	<vue-component @NAZOV_VLASTNEHO_EVENTU="data = @event" />

	<p>
	{{ data }}
	</p>

Kumunikacia cez EventBus
^^^^^^^^^^^^^^^^^^^^^^^^

Kuminikacia cez na seba nezavisle komponenty.

Vo Vue 3 si zrusilo pouzivanie **EventBus** a odporuca sa pouzit externy package.

Napriek tomu pre velke aplikacie sa odporuca pouzivat **VUEX** na menezovanie stavov a pod cross velku aplikaciu.


.. note::

	Urcite pri budovani vacsej aplikacie by chcelo pouzit **VUEX**


EventBus mitt
^^^^^^^^^^^^^

Na ukazku pouzijeme externu kniznicu **mitt**

Nainsatlovat ::

	npm insatll mitt

Do ``app.js`` alebo ``main.js`` je potrebne importovat mitt ::

	import mitt from 'mitt'

	window.eventBus = mitt()

Nasledne u podobne ako pri komunikaii s rodicom vieme poslat udalost do Globalneho eventBus-u ::

	window.eventBus.emit('NAZOV_GLOBALNEHO_EVENTU', data)

mixins
------

V pripade ze sa nas kod bude v aplikacii opakovat 2 a viac krat , je vhodne pre zachovanie REUSABLE pouzit mixins .

Mixins je v podstate vlastna kniznica s datami a funkciami, ktoru vieme jednoducho pouzitv akomkolvek VUE komponente.

Na ukazku jednoducheho filter mixin:

.. code-block::

	export default {
		data() {
			return {
				data: [],
				search: ''
			}
		},
		computed: {
			filteredItems() {
				return this.data.filter( item => {
					return item[this.searchColumn]
						.toLowerCase()
						.includes(this.search.toLowerCase())
				})
			}
		},
	}

.. warning::

	Nezabudnite importovat svoje Mixins do komponenty ::

		    mixins: [filterMixin]

Moment js
---------

Uprava resp. formatovanie datumu na FE tzn.  ze ked zo servera nepride naformatovany cas napr. packagom Carbon. N

Nutne doinstalovat package :

.. code-block:: console

	npm install moment

Potom staci do svojeho nejakeho Mixin prihodit funkciu na formatovanie napr. :

..code-block::

		import moment from 'moment'

	    methods: {
			niceDay(dateTime) {
				return moment(dateTime).fromNow()
			}
		},

Nasledne v komponente kde mame dotiahnuty mixin , tak staci vo vypise hodnoty zabalit do funkcie ``{{ niceDay( VALUE ) }}``
