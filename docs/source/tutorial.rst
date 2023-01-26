Tutorial
=====

.. _installation:

Installation
------------

.. role:: shell(code)
  :language: shell
  :class: highlight


To use openfst-python, first install it with :shell:`pip`:

.. code-block:: console

   $ pip install openfst-python


Lab1
----------------

.. note::
   We may put all the content here!
   Or, we may also put it in another file, if you think it could be too long to put all of the content here, which is up to you.
   For Lab1, please refer to :doc:`lab1`.


There are three essential classes in lab1.

.. currentmodule:: openfst_python

.. autosummary::
   pywrapfst.SymbolTable
   pywrapfst._MutableFst
   pywrapfst.Arc


First, let's have a look at how to create a SymbolTable.

>>> # Here is an example of instantiating a SymbolTable
>>> import openfst_python as fst
>>> st = fst.SymbolTable()

You will probably use two main methods of the class :python:`SymbolTable`.

.. autoclass:: pywrapfst.SymbolTable
   :members: add_symbol, find


