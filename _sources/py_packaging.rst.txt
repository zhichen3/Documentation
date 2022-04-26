***********
Packaging
***********

Put the source code inside a directory, say ``mymodule``. There should be a file called ``__init__.py``, which can be empty.

However, it is better to import all written functions/classes inside ``__init__.py``. An example of the ``__init__.py`` is the following:

.. code:: python

   from .module import function
   

In order to install module locally on the machine, create a ``setup.py`` in the same parent directory containing ``mymodule``.

A template of the ``setup.py`` is the following:

.. code:: python

   from setuptools import setup, find_packages

   setup(name='mymodule',
      description='description',
      url='github url',
      author='author name',
      author_email='email',
      license='BSD',
      packages=find_packages(),
      install_requires=['numpy', 'matplotlib','other needed packages'])


To install python module on machine run:

* If just want one-time install

  .. prompt:: bash

     python setup.py install

     python setup.py uninstall
     
* If want constant update due to constant development

  .. prompt:: bash

     python setup.py develop

     python setup.py develop --uninstall

    

     
