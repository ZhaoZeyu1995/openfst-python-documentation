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


Lab-specific documentation: an overview
----------------

Lab 1: Building HMMs with OpenFst
^^^^^^^^^^^^^^^

See the full documentation at :doc:`lab1`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab1.ipynb>`_ to view the jupyter notebook file for this lab.


There are three classes used in Lab 1: :python:`_MutableFst`, the main class for a "mutable" FST (ie. one that can be dynamically modified in the code); :python:`Arc`, which is the arc object used to connect states in an FST; and :python:`SymbolTable`, which maps input or output strings to the integer IDs used as arc labels by OpenFst.

.. autosummary::
   openfst_python.pywrapfst.SymbolTable
   openfst_python.pywrapfst._MutableFst
   openfst_python.pywrapfst.Arc


Lab 2: FST with Weights
^^^^^^^^^^^^^^^

See the full documentation at :doc:`lab2`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab2.ipynb>`_ to view the jupyter notebook file for this lab.

The essential class for this lab is :python:`Weight`, and all weights are instances of this class.

.. autosummary::
   openfst_python.pywrapfst.Weight

Labs 3 and 4: Viterbi decoding
^^^^^^^^^^^^^^^

There is no additional documentation specific to either of these labs.

Labs 5: WFST operations
^^^^^^^^^^^^^^^

See the full documentation at :doc:`lab5`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab5.ipynb>`_ to view the jupyter notebook file for this lab.

This lab introduces several WFST operations.  You'll see how these can be used to implement solutions to the problem of matching phoneme sequences to entries in a lexicon, and also incorporating a grammar.  We use the following operations:

.. autosummary::
   openfst_python.pywrapfst.determinize
   openfst_python.pywrapfst.compose
   openfst_python.pywrapfst.shortestpath
   openfst_python.pywrapfst.minimize
   openfst_python.pywrapfst.project
   openfst_python.pywrapfst.rmepsilon
   openfst_python.pywrapfst.arcsort

