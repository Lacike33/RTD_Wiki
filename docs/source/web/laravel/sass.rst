.. _doc_laravel_sass:

Sass
====

Metóda sass vám umožňuje zostaviť **Sass** do CSS, ktoré sú zrozumiteľné pre webové prehliadače.

Najskor je potrebne nainstalova sass loader :

.. code-block:: console

	npm install resolve-url-loader@^5.0.0 --save-dev --legacy-peer-deps

Metóda sass akceptuje cestu k vášmu súboru Sass ako svoj prvý argument a adresár, do ktorého by sa mal umiestniť kompilovaný súbor, ako svoj druhý argument :

.. code:: javascript

	mix.sass('resources/sass/app.scss', 'public/css');

Vlozenie normalize

.. code-block::

	npm install --save normalize.css
