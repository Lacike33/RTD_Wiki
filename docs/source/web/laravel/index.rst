Laravel
=======

Laravel je framework pre vývoj web aplikácii s kladeným dôrazom na elegantnú syntax a dokumentáciu, ktorá je dostupná na `Laravel dokumentácia <https://laravel.com/docs/9.x>`_.

Pre sťahovanie dependencies slúži `Composer <https://getcomposer.org/>`_ a všetky dostupné balíčky resp. repozitár balíčkov je dostupný na `Packagist <https://packagist.org/>`_ alebo `GitHub <https://github.com/>`_.

Laravel má aj vlastný adresár balíčkov `Packalyst <http://packalyst.com/>`_ určený pre **Laravel** projekty a teší sa aj veľkému počtu fanúšikov vlastných videotutoriálov `Laracast <https://laracasts.com/>`_ ako aj `Scotch.io <https://scotch.io/tag/laravel>`_ tutoriálov.

Inštalácia Via Composer
-------------------------

.. code-block:: console

	composer create-project laravel/laravel example-app
	cd example-app
	php artisan serve

Inštalátor Laravel
------------------

Alebo si môžete nainštalovať **Laravel Installer** ako globálnu závislosť **Composer**:

.. code-block:: console

	composer global require laravel/installer

.. note::

	Uistite sa, že ste do vašej ``$PATH`` umiestnili celý systémový adresár dodávateľa bin Composer, aby váš systém mohol nájsť spustiteľný súbor laravel.

	Tento adresár existuje na rôznych miestach v závislosti od vášho operačného systému; niektoré bežné miesta však zahŕňajú: ::

		macOS: $HOME/.composer/vendor/bin

V mojom pripade zafungovalo pridanie nasledujucej adresy do suboru ``~/.zshrc``

::

	export PATH="/Users/lacike/.composer/vendor/bin"

.. note::

	Nasledne este spustit ``source ~/.zshrc``

Laravel Git projekt
-------------------

Pre pohodlie môže inštalátor Laravel vytvoriť aj úložisko **Git** pre váš nový projekt.
Ak chcete označiť, že chcete vytvoriť úložisko Git, zadaj pri vytváraní nového projektu príznak ``--git`` :

.. code-block:: console

	laravel new example-app --git

Laravel GitHub projekt
----------------------

Namiesto použitia príznaku ``--git`` môžete tiež použiť príznak ``--github`` na vytvorenie úložiska Git a tiež na vytvorenie zodpovedajúceho súkromného úložiska na **GitHub**:

.. code-block:: console

	laravel new example-app --github

.. toctree::
   :maxdepth: 3
   :name: laravel

   api
   authentication
   mail
   sass
   tailwind
   vue
