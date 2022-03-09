.. _doc_sphinx_sample:

Sample
======

V tejte sekcii su zozbrazene veskere ukazky pouzitia.

Code block
----------

Ukazka blokov pomocou direktivy ``.. code-block:: **[language]**``.

**YAML**

.. code-block:: yaml

	# Configuration in YAML

**XML**

.. code-block:: xml

	<!-- Configuration in XML -->

**PHP**

.. code-block:: php

	// Configuration in PHP

**HTML+PHP**

.. code-block:: html+php

	<! Test pre HTML !>

**CONSOLE**

.. code-block:: console

    $ pip install lumache

**BASH**

.. code-block:: bash

   # common.sh
   pip install my-dependency==1.2.3

**PYTHON**

.. code-block:: python

    from celery.contrib import rdb; rdb.set_trace()

**INI**

.. code-block:: ini

   # Configuration for nova-rootwrap
   # This file should be owned by (and only-writeable by) the root user

   [DEFAULT]
   # List of directories to load filter definitions from (separated by ',').

Zaroven je mozne aj pouzitie alternativnej direktivy ``.. code:: **[language]**``.

.. code:: python

    import sphinx_rtd_theme

    extensions = [
        ...
        'sphinx_rtd_theme',
    ]

    html_theme = "sphinx_rtd_theme"

GUI label
---------

.. code::

	:guilabel:`Some action`

:guilabel:`Some action`
