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

.. line-block::
   MAIL_DRIVER=smtp
   MAIL_HOST=smtp.forpsi.com
   MAIL_PORT=587
   MAIL_USERNAME=postmaster@lvconsult.sk
   MAIL_PASSWORD=vBUP827_xM
   MAIL_ENCRYPTION=null
   MAIL_FROM_ADDRESS=postmaster@lvconsult.sk
   MAIL_FROM_NAME="LV consult s.r.o."
   MAIL_ENCRYPTION=tls

Email bude chodit namiesto priamo userovi do schranky na **FAKE** server.
Pre zobrazenie mailov ako aj konfiguracnych udajov pouzi login na `mailtrap.io <https://mailtrap.io/signin>`_ :

::
user: allacino@gmail.com
password:

.. line-block::
	MAIL_MAILER=smtp
	MAIL_HOST=smtp.mailtrap.io
	MAIL_PORT=2525
	MAIL_USERNAME=68fa6f3e3194c0
	MAIL_PASSWORD=448c2b8dbfeddf
	MAIL_ENCRYPTION=tls

