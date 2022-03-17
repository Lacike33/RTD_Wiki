.. _doc_laravel_sass:

Sass
====

Metóda sass vám umožňuje zostaviť **Sass** do CSS, ktoré sú zrozumiteľné pre webové prehliadače.

Metóda sass akceptuje cestu k vášmu súboru Sass ako svoj prvý argument a adresár, do ktorého by sa mal umiestniť kompilovaný súbor, ako svoj druhý argument :

.. code:: javascript

	mix.sass('resources/sass/app.scss', 'public/css');
