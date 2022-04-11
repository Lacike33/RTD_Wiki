******
QR kod
******

Instalacia
----------

Pre generovanie QR kodov je vhodny jednoduchy QRcode `/simple-qrcode/ <https://www.simplesoftware.io/#/docs/simple-qrcode>`_ package

.. code-block:: console

	composer require simplesoftwareio/simple-qrcode

Po instalcia ako byva zvykom je potrebne do konfig suboru ``config/app.php`` pridat service provider and aliases.

.. code-block::

	//config/app.php

	'providers' => [
	 ….
	 SimpleSoftwareIO\QrCode\QrCodeServiceProvider::class
	 ],

	'aliases' => [
	 ….
	 'QrCode' => SimpleSoftwareIO\QrCode\Facades\QrCode::class
	 ],

Pouzitie
--------

Po uspesnych krokoch vieme uz pouzivat QR code :

.. code-block::

	Route::get('qrcode', function () {
		 return QrCode::size(300)->generate('A basic example of QR code!');
	 });

QR Code with Color
------------------

.. code-block::

	Route::get('qrcode-with-color', function () {
		 return \QrCode::size(300)
						 ->backgroundColor(255,55,0)
						 ->generate('A simple example of QR code');
	 });

QR Code with Image
------------------

.. code-block::

	Route::get('qrcode-with-image', function () {
			 $image = \QrCode::format('png')
							 ->merge('images/laravel.png', 0.5, true)
							 ->size(500)->errorCorrection('H')
							 ->generate('A simple example of QR code!');
		  return response($image)->header('Content-type','image/png');
	 });

Email QR code
-------------

.. code-block::

	Route::get('qrcode-with-special-data', function() {
		 return \QrCode::size(500)
					 ->email('info@tutsmake.com', 'Welcome to Tutsmake!', 'This is !.');
	 });

QR Code Phone Number
--------------------

.. code-block::

	QrCode::phoneNumber('111-222-6666');

QR Code Text Message
--------------------

.. code-block::

	QrCode::SMS('111-222-6666', 'Body of the message');
