.. _doc_laravel_mail:

Mail
====

Je funkcionalita pre odosielanie mailov.

Viac na webe Laravelu `Mail <https://laravel.com/docs/9.x/mail>`_.

Konfiguracia
------------

Na odosielanie mailov je potrebne nakonfigurovat v subore ``.env`` potrebne atributy ktore je mozne nastavit aj na FAKE server.

**Korektne nastavenie :**

Email bude chodit cez zadany SMT server:


**Konfiguracia**

.. code-block:: ini

   MAIL_DRIVER=smtp
   MAIL_HOST=smtp.m1.websupport.sk
   MAIL_PORT=465
   MAIL_USERNAME=postmaster@lvconsult.sk
   MAIL_PASSWORD=Ye6cJx9.n|
   MAIL_ENCRYPTION=null
   MAIL_FROM_ADDRESS=postmaster@lvconsult.sk
   MAIL_FROM_NAME="LV consult s.r.o."
   MAIL_ENCRYPTION=tls

Fake nastavenie
---------------

Email bude chodit namiesto priamo userovi do schranky na **FAKE** server.
Pre zobrazenie mailov ako aj konfiguracnych udajov pouzi login na `mailtrap.io <https://mailtrap.io/signin>`_ :

.. code-block:: ini

	user = allacino@gmail.com
	password =

Je mozne vytvarat projekty a subinboxy.

.. code-block:: ini

	MAIL_MAILER=smtp
	MAIL_HOST=smtp.mailtrap.io
	MAIL_PORT=465
	MAIL_USERNAME=69dc9da0f35af5
	MAIL_PASSWORD=cfdc030754ebed
	MAIL_ENCRYPTION=tls

Mailablle class
---------------

Pomocnu triedu (Mailablle class) na odosielanie mailov je mozne vytvorit nasledujucimi prikazmy:

.. code-block:: console

   $ php artisan make:mail <Nazov_triedy>                                      // s pouzitim Blade view
   $ php artisan make:mail <Nazov_triedy> --markdown=<Cesta_k_suboru>          // s pouzitim sablony Markdown
   $ php artisan vendor:publish --tag=laravel-mail                             // export markdown komponent do vlastnej struktury

V kazdej vygenerovanej classe metoda **build** vytvara mail a je mozne pouzit parametre ako :

.. code-block:: ini

   -> from
   -> subject
   -> view
   -> attach

.. code-block:: php

   return $this->from('Meno_odosielatela','example@example.com')
   				->view('emails.orders.shipped');

V pripade ze nechceme **MAIL** formatovat tak posleme PLAIN text takto

.. code-block:: ini

   ->text('emails.orders.shipped_plain');

V pripade ze chceme do **MAIL** sablony posielat aj data , tak mame k dispozicii 2 moznosti :

1. Via **Public Properties**

V konstruktore vytvorenej mailablle triedy musime zadefinovat model z ktoreho budeme citat data:

.. code-block:: php

   public $order;
   public function __construct(Order $order)
   {
       $this->order = $order;
   }

2. Via The **with** Method

V takomto pripade mozeme do VIEW poslat aj pole s datami "**with**"

.. code-block:: php

   public function build()
   {
       return $this->view('emails.orders.shipped')
                    ->with([
                        'orderName' => $this->order->name,
                        'orderPrice' => $this->order->price,
                    ]);
   }

Odosielanie priloh
------------------

.. code-block:: php

   public function build()
   {
       return $this->view('emails.orders.shipped')
                   ->attach('/path/to/file');
   }

alebo

.. code-block:: PHP

   public function build()
   {
       return $this->view('emails.orders.shipped')
                   ->attach('/path/to/file', [
                       'as' => 'name.pdf',
                       'mime' => 'application/pdf',
                   ]);
   }

Odoslanie obrazku
-----------------

.. code-block:: html+php

   <body>
    Here is an image:

    <img src="{{ $message->embed($pathToFile) }}">
   </body>

Markdown mail
-------------

Zakladom je mat blade s pouzitim Markdown komponentami. Prikaz na vygenerovanie VIEW :

.. code-block:: console

   $ php artisan make:mail <Nazov_triedy> --markdown=<Cesta_k_suboru>          // s pouzitim sablony Markdown

napr.

.. code-block:: console

   $ php artisan make:mail OrderShipped --markdown=emails.orders.shipped

V pripade pouzitia Markdown sablony v metode **build** pouzijeme metodu **markdown** :

.. code-block:: php

   return $this->from('example@example.com')
                ->markdown('emails.orders.shipped');

Kustomizacia Markdown komponentov
---------------------------------

V prvom rade musime mat vyexportovane MARKDOWN komponenty do vlastnej struktury :

.. code-block:: console

   $ php artisan vendor:publish --tag=laravel-mail

Po vygenerovani sa komponenty nachadzaju v ``resources/views/vendor/mail``

Kustomizacia CSS Markdown komponentov
=====================================

Vygenerovane komponenty obsahuju defaultny css subor ``default.css`` pre kazdu temu  ``resources/views/vendor/mail/html/themes`` ktoreho upravou sa zmeny prejavia automaticky.

V pripade ze si chceme vytvorit vlastnu themu, tak ju vytvorime tu ``resources/views/vendor/mail/html/themes`` ale nesmieme zabudnut na nastavenie temy v configu ``config\mail``

Odoslanie mailu
---------------

.. code-block:: php

	Mail::to($request->user())->send(new OrderShipped($order));

alebo

.. code-block:: php

	Mail::to($request->user())
		->cc($moreUsers)
		->bcc($evenMoreUsers)
		->send(new OrderShipped($order));

MAIL je mozne odoslat priamo do prehliadaca :

.. code-block:: php

	Route::get('/mailable', function () {
    	$invoice = App\Invoice::find(1);

		return new App\Mail\InvoicePaid($invoice);
	});

Dalsou moznostou je vyrenderovanie Mailu. Metoda **render** vráti vyhodnotený obsah Mailu ako reťazec

.. code-block:: php

   $invoice = App\Invoice::find(1);

   return (new App\Mail\InvoicePaid($invoice))->render();

Lokalizovanie jazyka mailu
--------------------------

.. code-block:: php

	Mail::to($request->user())->send(
    (new OrderShipped($order))->locale('es')
	);

Queueing Mail
-------------

Keďže odosielanie e-mailových správ môže drasticky predĺžiť čas odozvy vašej aplikácie, mnohí vývojári sa rozhodnú do frontu odosielať e-mailové správy.
Laravel to uľahčuje pomocou zabudovaného rozhrania API pre jednotnú frontu.
Ak chcete na fronte e-mailovú správu, použite metódu frontu na priečke pošty po zadaní príjemcov správy:

.. code-block:: console

   Mail::to($request->user())
		->cc($moreUsers)
		->bcc($evenMoreUsers)
		->queue(new OrderShipped($order));

Táto metóda sa automaticky postará o stlačenie úlohy na frontu, aby sa správa odoslala na pozadí. Samozrejme, pred použitím tejto funkcie budete musieť nakonfigurovať svoje fronty `Queues <https://laravel.com/docs/9.x/queues>`.

Mail verifikacia
================

**Laraval** ma v sebe uz zabudovanu funkcionalitu overovania mailov..

Viac na webe Laravelu - `Mail verification <https://laravel.com/docs/9.x/verification#main-content>`_

Konfiguracia
------------

Na odosielanie mailov je potrebne nakonfigurovat v subore ``.env`` potrebne atributy ktore je mozne nastavit aj na FAKE server.

Verify Email
------------

** Postup ** po vygenerovani Auth Scaffolding ``php artisan make:auth``

Implementovat rozhranie **MustVerifyEmail** do modelu ``User``

.. code-block::

   class User extends Authenticatable implements MustVerifyEmail
   {
       use Notifiable;

       // ...
   }

Do potrebneho modelu pridaj IF ``use Illuminate\Contracts\Auth\MustVerifyEmail;``

Pridaj verifikacnu Route do ``web.php``

Do suboru ``routes >> web.php`` pridaj extra parameter

.. code-block::

   Auth::routes(['verify' => true]);

Toto enabluje controller s názvom ``VerificationController.php``, ktorý je už dodávaný s Laravelom.

3.Pre ostrenie vstupu neverifikovanym pridaj do konstruktoru daneho Controllera nazov middleware **verified**

.. code-block::

    public function __construct()
    {
        $this->middleware(['auth', 'verified']);
    }

alebo /nove riesenie Laravel 7.*/

.. code-block::

   Route::get('profile', function () {
    // Only verified users may enter...

   })->middleware('verified');
