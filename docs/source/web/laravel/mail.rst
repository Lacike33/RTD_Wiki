.. _doc_laravel_mail:

Mail
====

Je funkcionalita pre odosielanie mailov.

Viac na webe Laravelu - `Mail <https://laravel.com/docs/9.x/mail>`.

Konfiguracia
------------

Na odosielanie mailov je potrebne nakonfigurovat v subore ```.env``` potrebne atributy ktore je mozne nastavit aj na FAKE server.

**Korektne nastavenie :**

Email bude chodit cez zadany SMT server:


.. code-block:: env
	MAIL_DRIVER=smtp
	MAIL_HOST=smtp.forpsi.com
	MAIL_PORT=587
	MAIL_USERNAME=postmaster@lvconsult.sk
	MAIL_PASSWORD=vBUP827_xM
	MAIL_ENCRYPTION=null
	MAIL_FROM_ADDRESS=postmaster@lvconsult.sk
	MAIL_FROM_NAME="LV consult s.r.o."
	MAIL_ENCRYPTION=tls

Fake nastavenie
---------------

Email bude chodit namiesto priamo userovi do schranky na FAKE server.
Pre zobrazenie mailov ako aj konfiguracnych udajov pouzi login na `mailtrap.io <https://mailtrap.io/signin>`:

user: allacino@gmail.com
password:

.. code-block:: env
	MAIL_MAILER=smtp
	MAIL_HOST=smtp.mailtrap.io
	MAIL_PORT=2525
	MAIL_USERNAME=68fa6f3e3194c0
	MAIL_PASSWORD=448c2b8dbfeddf
	MAIL_ENCRYPTION=tls

Mailablle class
---------------

Pomocnu triedu (Mailablle class) na odosielanie mailov je mozne vytvorit nasledujucimi prikazmy:

.. code-block:: console
   php artisan make:mail <Nazov_triedy>                                      // s pouzitim Blade view
   php artisan make:mail <Nazov_triedy> --markdown=<Cesta_k_suboru>          // s pouzitim sablony Markdown
   php artisan vendor:publish --tag=laravel-mail                             // export markdown komponent do vlastnej struktury

V kazdej vygenerovanej classe metoda **build** vytvara mail a je mozne pouzit parametre ako :

-> from

-> subject

-> view

-> attach

.. code-block:: PHP
	return $this->from('Meno_odosielatela','example@example.com')
                ->view('emails.orders.shipped');

V pripade ze nechceme **MAIL** formatovat tak posleme PLAIN text takto

.. code-block:: PHP
	->text('emails.orders.shipped_plain');

V pripade ze chceme do **MAIL** sablony posielat aj data , tak mame k dispozicii 2 moznosti :

1. Via Public Properties

V konstruktore vytvorenej mailablle triedy musime zadefinovat model z ktoreho budeme citat data:

.. code-block:: PHP
	public $order;
	public function __construct(Order $order)
    {
        $this->order = $order;
    }

2. Via The with Method

V takomto pripade mozeme do VIEW poslat aj pole s datami "**with**"

.. code-block:: PHP
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

.. code-block:: PHP
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

.. code-block:: PHP
   <body>
    Here is an image:

    <img src="{{ $message->embed($pathToFile) }}">
   </body>

Markdown mail
-------------

Zakladom je mat blade s pouzitim Markdown komponentami. Prikaz na vygenerovanie VIEW :

.. code-block:: console
   php artisan make:mail <Nazov_triedy> --markdown=<Cesta_k_suboru>          // s pouzitim sablony Markdown

   napr.

.. code-block:: console
   php artisan make:mail OrderShipped --markdown=emails.orders.shipped

V pripade pouzitia Markdown sablony v metode **build** pouzijeme metodu **markdown** :

.. code-block:: PHP
	return $this->from('example@example.com')
                ->markdown('emails.orders.shipped');

Kustomizacia Markdown komponentov
---------------------------------

V prvom rade musime mat vyexportovane MARKDOWN komponenty do vlastnej struktury :

.. code-block:: console
   php artisan vendor:publish --tag=laravel-mail

Po vygenerovani sa komponenty nachadzaju v ```resources/views/vendor/mail```

Kustomizacia CSS Markdown komponentov
*************************************

Vygenerovane komponenty obsahuju defaultny css subor ```default.css``` pre kazdu temu  ```resources/views/vendor/mail/html/themes``` ktoreho upravou sa zmeny prejavia automaticky.

V pripade ze si chceme vytvorit vlastnu themu, tak ju vytvorime tu ```resources/views/vendor/mail/html/themes``` ale nesmieme zabudnut na nastavenie temy v configu ```config\mail```

Odoslanie mailu
---------------

.. code-block:: PHP
	Mail::to($request->user())->send(new OrderShipped($order));

alebo

.. code-block:: PHP
	Mail::to($request->user())
		->cc($moreUsers)
		->bcc($evenMoreUsers)
		->send(new OrderShipped($order));

MAIL je mozne odoslat priamo do prehliadaca :

.. code-block:: PHP
	Route::get('/mailable', function () {
    	$invoice = App\Invoice::find(1);

		return new App\Mail\InvoicePaid($invoice);
	});

Dalsou moznostou je vyrenderovanie Mailu. Metoda **render** vráti vyhodnotený obsah Mailu ako reťazec

.. code-block:: PHP
   $invoice = App\Invoice::find(1);

   return (new App\Mail\InvoicePaid($invoice))->render();

Lokalizovanie jazyka mailu
--------------------------

.. code-block:: PHP
	Mail::to($request->user())->send(
    (new OrderShipped($order))->locale('es')
	);

Queueing Mail
-------------

Keďže odosielanie e-mailových správ môže drasticky predĺžiť čas odozvy vašej aplikácie, mnohí vývojári sa rozhodnú do frontu odosielať e-mailové správy.
Laravel to uľahčuje pomocou zabudovaného rozhrania API pre jednotnú frontu.
Ak chcete na fronte e-mailovú správu, použite metódu frontu na priečke pošty po zadaní príjemcov správy:

.. code-block:: PHP
	Mail::to($request->user())
		->cc($moreUsers)
		->bcc($evenMoreUsers)
		->queue(new OrderShipped($order));

Táto metóda sa automaticky postará o stlačenie úlohy na frontu, aby sa správa odoslala na pozadí. Samozrejme, pred použitím tejto funkcie budete musieť nakonfigurovať svoje fronty `Queues <https://laravel.com/docs/9.x/queues>`.
