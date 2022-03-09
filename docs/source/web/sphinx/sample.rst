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

**Code block** s cislovanymi riadkami s podfarbenim a caption ...

.. code-block:: python
   :linenos:
   :emphasize-lines: 3,5
   :caption: Code Blocks can have captions.

   def some_function():
       interesting = False
       print 'This line is highlighted.'
       print 'This one is not...'
       print '...but this one is.'

GUI label
---------

.. code::

	:guilabel:`Some action`

Ina ukazka pre block ::

	:guilabel:`Some action`

:guilabel:`Some action`

Centered text
-------------

You can create a statement with centered text with ``.. centered::``

.. centered:: This is centered text!

Admonitions
-----------

.. Attention:: Directives at large.

.. Caution:: Don't take any wooden nickels.

.. DANGER:: Mad scientist at work!

.. Error:: Does not compute.

.. Hint:: It's bigger than a bread box.

.. Important::
   - Wash behind your ears.
   - Clean up your room.

     - Including the closet.
     - The bathroom too.

       - Take the trash out of the bathroom.
       - Clean the sink.
   - Call your mother.
   - Back up your data.

.. Note:: This is a note.
   Equations within a note:
   :math:`G_{\mu\nu} = 8 \pi G (T_{\mu\nu}  + \rho_\Lambda g_{\mu\nu})`.

.. Tip:: 15% if the service is good.

    +---------+
    | Example |
    +=========+
    | Thing1  |
    +---------+
    | Thing2  |
    +---------+
    | Thing3  |
    +---------+

.. WARNING:: Strong prose may provoke extreme mental exertion.
   Reader discretion is strongly advised.

.. admonition:: And, by the way...

   You can make up your own admonition too.

Download Links
==============

:download:` <img/intro.jpg>`


Target
------

Implicitny odkaz na nadpis bez stitka Glossary_

Blocks
======

Literal Blocks
--------------

Literal blocks are indicated with a double-colon ("::") at the end of
the preceding paragraph (over there ``-->``).  They can be indented ::
    if literal_block:
        text = 'is left as-is'
        spaces_and_linebreaks = 'are preserved'
        markup_processing = None

Or they can be quoted without indentation::
>> Great idea!
>
> Why didn't I think of that?
-->

Sidebar
-------

.. sidebar:: A code example

    With a sidebar on the right.

Glossary
========

.. glossary::

  Documentation
     Provides users with the knowledge they need to use something.

  Reading
     The process of taking information into ones mind through the use of eyes.
