Tutorial
=====

.. _installation:

Installation
------------

*Not needed if you have followed the setup instructions for our ASR Labs*

.. role:: shell(code)
  :language: shell
  :class: highlight


To use openfst-python, we can simply install it with :shell:`pip`:

.. code-block:: console

   $ pip install openfst-python


Lab-specific documentation
----------------

Lab 1: Building HMMs with OpenFst
^^^^^^^^^^^^^^^

See the full documentation at :doc:`lab1`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab1.ipynb>`_ to view the jupyter notebook file for this lab.


There are three classes used in Lab 1: :python:`_MutableFst`, the main class for an FST "mutable" (ie. that can be dynamically modified in the code); :python:`Arc`, which is the arc object used to connect states in an FST; and :python:`SymbolTable`, which maps input or output strings to the integer IDs used as arc labels by OpenFst.

.. autosummary::
   openfst_python.pywrapfst.SymbolTable
   openfst_python.pywrapfst._MutableFst
   openfst_python.pywrapfst.Arc






