.. _doc_laravel_authentication:

Authentication
==============

Laravel ponúka vlastný vstavaný **autentifikačný** systém, ktorý je sa jednoducho implementoval do verzie **6.x**.

Laravel zároveň vygeneroval aj základný **layout** aplikácie ako aj **login page** a **registráciu**.

Stacilo pouzit príkaz :

.. code:: console

	php artisan make:auth

.. note::

	V pripade, ze chcete registraciu zakazat tak v subore ``routes/web.php`` pridajte ``Auth::routes(['register' => false])``

Od verzie **6.x** az po aktualnu verziu je mozne pouzit 2 implemnentacie tzv. '**Starter kit**<https://laravel.com/docs/9.x/starter-kits>'_ .

Laravel Breeze
--------------

Laravel Breeze je minimálna, jednoduchá implementácia všetkých overovacích funkcií Laravel, vrátane prihlásenia, registrácie, resetovania hesla, overenia e-mailu a potvrdenia hesla.
Predvolená vrstva zobrazenia Laravel Breeze sa skladá z jednoduchých šablón Blade v štýle Tailwind CSS.

Najskor je nutne stiahnut package ::

	composer require laravel/breeze --dev

Nasledne spustit artisan prikazy:

.. code:: console

	php artisan breeze:install

.. note::

	Please execute the ``npm install && npm run dev`` command to build your assets.

.. code:: console

	npm install
	npm run dev
	php artisan migrate

Reaktivny scafolding
^^^^^^^^^^^^^^^^^^^^
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

Laravel Jetstream
-----------------

Zatiaľ čo <Laravel Breeze>_ poskytuje jednoduchý a minimálny východiskový bod pre vytvorenie aplikácie Laravel, **Jetstream** rozširuje túto funkčnosť o robustnejšie funkcie a ďalšie frontendové technologické balíky.

Pre tých, ktorí sú v Laravel úplne noví, odporúčame naučiť sa s Laravel Breeze pred absolvovaním Laravel Jetstream.

.. note::

	Kompletnú dokumentáciu pre inštaláciu Laravel Jetstream nájdete v 'oficiálnej dokumentácii Jetstream <https://jetstream.laravel.com/2.x/introduction.html>'_.
