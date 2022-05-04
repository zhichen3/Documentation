**************
Unit Tests
**************

pytest
========

Use ``pytest`` for creating unit test framework for python.

Test Discovery
===============

Tests are automatically found for the following files:

* Unit test file should start or end with "test" :
  * test_example.py
  * example_test.py

* When testing in a class, class name should start with ``Test`` :
  * ``TestExample``
  * This class should not have the constructor or ``__init__()``


Testing
=========

Testing should make use of ``assert`` statement.

An example of testing would be creating a file called ``test_simple.py`` and with the following content:

.. code:: python

   def multiply(a,b):
	  return a*b

   def test_multiply():
	  assert multiply(4,6) == 24


Then run the following command for running the test in the current directory:

.. prompt:: bash

   pytest -v                   #v for verbose

.. tip::

   To always show stdout from ``print`` statements, include ``-s`` flag.
   

class
=======

Using a ``class`` for testing is usually more clear and concise.

`pytest` has the few methods for setting up a speciic data for test, ``setup_method()`` and ``setup_class(cls)``  and methods to clean up data ``teardown_method()`` and ``teardown_class(cls)``.

Example:

.. code:: python

   class TestClass:

	  @classmethod
	  def set_upclass(cls):
	      ''' this is run once for each class, before any tests '''
	      pass

	  @classmethod
	  def teardown_class(cls):
	      ''' this is run once for each class, after all tests '''
	      pass

	  def setup_method(self):
	      ''' this is run before each of the test methods '''
	      pass

	  def teardown_method(self):
	      ''' this is run after each of the test methods '''
	      pass
	      
	  def test(self):
	      ''' some tests '''
	      pass

	      
	      
	  
	      
