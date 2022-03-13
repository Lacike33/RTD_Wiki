.. _doc_laravel_authentication:

Authentication
==============

Laravel ponúka vlastný vstavaný **autentifikačný** systém, ktorý je sa jednoducho implementoval do verzie **5.6**.

Laravel zároveň vygeneroval aj základný **layout** aplikácie ako aj **login page** a **registráciu**.

Stacilo pouzit príkaz :

.. code:: console

	php artisan make:auth

.. note::

	V pripade, ze chcete registraciu zakazat tak v subore ``routes/web.php`` pridajte ::

		Auth::routes(['register' => false]);

V aktualnej verzii **9.x** je mozne pouzit implemnentaciu :

Laravel Breeze
--------------

Laravel Breeze je minimálna, jednoduchá implementácia všetkých overovacích funkcií Laravel, vrátane prihlásenia, registrácie, resetovania hesla, overenia e-mailu a potvrdenia hesla.
Predvolená vrstva zobrazenia Laravel Breeze sa skladá z jednoduchých šablón Blade v štýle Tailwind CSS.

.. code::

	php artisan breeze:install

	npm install
	npm run dev
	php artisan migrate

Reaktivny scafolding
--------------------
::

	php artisan breeze:install vue

Alebo ...

::

	php artisan breeze:install react

A nasledne nainstalovat NPM moduly :

.. code:: console

	npm install
	npm run dev
	php artisan migrate
