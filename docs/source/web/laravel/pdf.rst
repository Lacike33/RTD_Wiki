***********
PDF Wrapper
***********

Pre tvorbu **PDF** je mozne vyuzitie viacero PDF modulov.
Asi medzi najoblubenejsie package patri 'DOMPDF <https://github.com/barryvdh/laravel-dompdf>'_

.. code-block:: console

	composer require barryvdh/laravel-dompdf

Po instalacii pridaj do suboru ``config/app.php``

.. code-block:: console

	Barryvdh\DomPDF\ServiceProvider::class,

	'PDF' => Barryvdh\DomPDF\Facade::class,

Nasledne je PDF wraper pouzit takto:

..code-block::

	$pdf = App::make('dompdf.wrapper');
	$pdf->loadHTML('<h1>Test</h1>');
	return $pdf->stream();


Alebo je mozne pouzit fasadu :

.. code-block::

	$pdf = PDF::loadView('pdf.invoice', $data);
	return $pdf->download('invoice.pdf');
