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

Od verzie **6.x** az po **7.x** Laravel preveroval vo svojej dokumentacii `laravel/ui <https://laravel.com/docs/6.x/authentication#included-routing>`_

Laravel ui
----------

Balík **laravel/ui** spoločnosti Laravel poskytuje rýchly spôsob, ako vytvoriť všetky trasy a zobrazenia, ktoré potrebujete na overenie, pomocou niekoľkých jednoduchých príkazov:

.. code:: console

	composer require laravel/ui --dev

	php artisan ui vue --auth

Detail pre implemnentaciu **Vue.js** do laravel projektu popisujem v sekcii :ref:`doc_laravel_vue`.

Od verzie **8.x** az po aktualnu verziu je mozne pouzit 2 implemnentacie tzv. `Starter kit <https://laravel.com/docs/9.x/starter-kits>`_ .

Laravel Breeze
--------------

Laravel Breeze je minimálna, jednoduchá implementácia všetkých overovacích funkcií Laravel, vrátane prihlásenia, registrácie, resetovania hesla, overenia e-mailu a potvrdenia hesla.
Predvolená vrstva zobrazenia Laravel Breeze sa skladá z jednoduchých šablón Blade v štýle Tailwind CSS.

Najskor je nutne stiahnut package

.. code:: console

	composer require laravel/breeze --dev

Nasledne spustit artisan prikazy:

.. code:: console

	php artisan breeze:install

.. note::

	Spusti prikaz ``npm install && npm run dev`` pre instalaciu **NPM** balickov.

Po instalacii NPM balikov nasleduje este spustit migraciu DB

.. code:: console

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
