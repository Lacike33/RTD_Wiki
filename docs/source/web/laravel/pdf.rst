***********
PDF Wrapper
***********

Pre tvorbu **PDF** je mozne vyuzitie viacero PDF modulov.
Asi medzi najoblubenejsie package patri `DOMPDF <https://github.com/barryvdh/laravel-dompdf>`_

.. code-block:: console

	composer require barryvdh/laravel-dompdf

Po instalacii bolo v minulosti pridat do suboru ``config/app.php``

.. code-block:: console

	Barryvdh\DomPDF\ServiceProvider::class,

	'PDF' => Barryvdh\DomPDF\Facade::class,

.. note::

	V aktualnej verzii laravelu a instalacii DomPDF nie je nutne modifikovat subor ``config/app.php``.

Nasledne je PDF wraper pouzit takto:

.. code-block::

	$pdf = App::make('dompdf.wrapper');
	$pdf->loadHTML('<h1>Test</h1>');
	return $pdf->stream();


Alebo je mozne pouzit fasadu :

.. code-block::

	$pdf = PDF::loadView('pdf.invoice', $data);
	return $pdf->download('invoice.pdf');

Nastavenia mozeme urobit v konfiguracnom subore ``config/dompdf.php`` ak pouzijeme prikaz

.. code-block:: console

	php artisan vendor:publish --provider="Barryvdh\DomPDF\ServiceProvider"

.. warning::

	Pri pouziti attachment v maili je potrebne do build metody dannej mail triedy pouzit ``attachData`` pre vlozene surovych dat, ale data musia prist cez ``output()``.
