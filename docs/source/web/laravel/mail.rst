.. _doc_laravel_mail:

Mail
====

Je funkcionalita pre odosielanie mailov.

Viac na webe Laravelu `Mail <https://laravel.com/docs/9.x/mail>`_.

Konfiguracia
------------

Na odosielanie mailov je potrebne nakonfigurovat v subore ```.env``` potrebne atributy ktore je mozne nastavit aj na FAKE server.

**Korektne nastavenie :**

Email bude chodit cez zadany SMT server:

Laravel je framework pre vývoj web aplikácii s kladeným dôrazom na elegantnú syntax a dokumentáciu, ktorá je dostupná na `Laravel dokumentácia <https://laravel.com/docs/9.x>`_.

Pre sťahovanie dependencies slúži `Composer <https://getcomposer.org/>`_ a všetky dostupné balíčky resp. repozitár balíčkov je dostupný na `Packagist <https://packagist.org/>`_ alebo `GitHub <https://github.com/>`_.

Laravel má aj vlastný adresár balíčkov `Packalyst <http://packalyst.com/>`_ určený pre **Laravel** projekty a teší sa aj veľkému počtu fanúšikov vlastných videotutoriálov `Laracast <https://laracasts.com/>`_ ako aj `Scotch.io <https://scotch.io/tag/laravel>`_ tutoriálov.

**Konkrétne riešenia :**

.. code-block:: none
   MAIL_DRIVER=smtp
   MAIL_HOST=smtp.forpsi.com
   MAIL_PORT=587
   MAIL_USERNAME=postmaster@lvconsult.sk
   MAIL_PASSWORD=vBUP827_xM
   MAIL_ENCRYPTION=null
   MAIL_FROM_ADDRESS=postmaster@lvconsult.sk
   MAIL_FROM_NAME="LV consult s.r.o."
   MAIL_ENCRYPTION=tls
