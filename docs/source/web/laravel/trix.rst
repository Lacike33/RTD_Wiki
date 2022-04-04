Trix editor
===========

Trix je open-source projekt od Basecampu, tvorcov Ruby on Rails.
Milióny ľudí dôverujú svoj text Basecamp a my sme vytvorili Trix, aby sme im poskytli čo najlepší zážitok z úpravy.

::

	npm install trix

Alternativy:

* vue-trix
* vue-trix-editor


Nasledne si trix editor naimportujeme do komponenty kde chceme pouzivat editor :

.. code-block::

	<script>
	import trix from 'trix'

	export default {
		components: {
			trix,
		},
	}

Zaroven je potrebne zadat v komponente aj CSS :

.. code-block::

	<style lang="scss" scoped>
		@import '~trix/dist/trix.css';
	</style>

Nasledne pouzijeme v kode :

.. code-block::

	<form>
		<input id="x" value="Editor content goes here" type="hidden" name="content">
		<trix-editor input="x"></trix-editor>
	</form>
