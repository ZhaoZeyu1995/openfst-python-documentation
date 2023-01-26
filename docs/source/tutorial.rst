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

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs>`_ to view the jupyter notebook file for our labs.

.. currentmodule:: openfst_python

.. autosummary::
   pywrapfst.SymbolTable
   pywrapfst._MutableFst
   pywrapfst.Arc


First, let's have a look at how to create a SymbolTable.

>>> # Here is an example of instantiating a SymbolTable
>>> import openfst_python as fst
>>> st = fst.SymbolTable()

You will use two main methods of the class :python:`SymbolTable`.

.. autoclass:: pywrapfst.SymbolTable
   :members: add_symbol, find


For example,

>>> idx = st.add_symbol('a')
>>> idx
>>> 0 # as you can see above, the method, add_symbol, returns the index corresponding to the label 'a', because this is the first label we add into the symbol table.
>>> idx = st.add_symbol('b')
>>> idx
>>> 1 # this time it returns 1, as 'b' is the second label we add into the symbol table

To find the index corresponding to a label, we may use the method :python:`SymbolTable.find()`

>>> idx = st.find('a')
>>> idx
>>> 0 # the label 'a' is in the symbol table, so it returns its index, and here it is 0.
>>> idx = st.find('c')
>>> idx
>>> -1 # the label 'c' is not in the symbol table, so it returns :python:`NO_SYMBOL` value, and here it is -1 by default.


