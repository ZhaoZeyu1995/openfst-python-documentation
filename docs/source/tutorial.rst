Usage
=====

.. _installation:

Installation
------------

To use openfst-python, first install it using pip:

Here is also an example of code-block.

.. code-block:: console

   $ pip install openfst-python

Creating recipes
----------------

To compute the composition,
you can use the ``openfst_python.compose()`` function:

.. autofunction:: openfst_python.compose

This is fst creation function

.. autoclass:: openfst_python.Fst

This is mutable fst add arc

.. autofunction:: openfst_python.pywrapfst._MutableFst.add_arc

This is an autoclass.

.. autoclass:: openfst_python.pywrapfst._MutableFst
   :members:


For example:

>>> import openfst_python as fst
>>> fst.compose()
['The composition result']

