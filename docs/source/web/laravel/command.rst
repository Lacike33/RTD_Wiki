*******
Command
*******

Vygenerovanie vlastneho commandu pre PHPOartisan

.. code-block:: console

	php artisan make:command ExportItems

Nasledne vo vytvorenej klase vieme upravit nazov command cez ktory sa spusti kodu.

Nazov commandu s argumentom
---------------------------

Argument s defaultnou hodnotou ``{ARGUMENT=default}``

.. code-block:: php

	/**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'products:exportCSV {product=all : All products or only one ID of the product}';

Argument s nepovinnym argumentom ``{ARGUMENT?}``

.. code-block:: php

	/**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'products:exportCSV {product? : All products or only one ID of the product}';

Argument s polom argumentov ``{ARGUMENT*}``

.. code-block:: php

	/**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'products:exportCSV {product* : All products or only one ID of the product}';


Pomocny argument ``{--ARGUMENT}``

.. code-block:: php

	/**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'products:exportCSV {--queue : Whether the job should be queued}' takto sa pridava option';
