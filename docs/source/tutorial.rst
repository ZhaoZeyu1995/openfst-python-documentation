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


There are three classes in lab1. 

To compute the composition,
you can use the ``openfst_python.compose()`` function:

.. autofunction:: openfst_python.compose

This is an autoclass.

.. autoclass:: openfst_python.Fst

This is mutable fst add arc

.. autofunction:: openfst_python.pywrapfst._MutableFst.add_arc


