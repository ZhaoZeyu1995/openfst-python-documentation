Tutorial
=====

.. _installation:

Installation
------------

To use openfst-python, first install it using pip:

Here is also an example of code-block.

.. code-block:: console

   $ pip install openfst-python


Useful Functions and Classes in Lab1
----------------

We may put all the content here!

To compute the composition,
you can use the ``openfst_python.compose()`` function:

.. autofunction:: openfst_python.compose

This is an autoclass.

.. autoclass:: openfst_python.Fst

This is mutable fst add arc

.. autofunction:: openfst_python.pywrapfst._MutableFst.add_arc


Or, we may also put it in another file as below, if you think it could be too long to put all of the content here, which is up to you.
For Lab1, please refer to :doc:`lab1`.


Here is an example of python codes:

>>> import openfst_python as fst
>>> fst.compose()
['The composition result']

