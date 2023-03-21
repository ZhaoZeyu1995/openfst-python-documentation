Labs 5: WFST operations
====

This lab introduces several WFST operations.  You'll see how these can be used to implement solutions to the problem of matching phoneme sequences to entries in a lexicon, and also incorporating a grammar.  We use the following operations:

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab1.ipynb>`_ to view the jupyter notebook file for this lab.

We use the following operations in this lab.  See the :doc:`api` for complete documentation of all operations.

.. autosummary::
   openfst_python.pywrapfst.determinize
   openfst_python.pywrapfst.compose
   openfst_python.pywrapfst.shortestpath
   openfst_python.pywrapfst._MutableFst.minimize
   openfst_python.pywrapfst._MutableFst.project
   openfst_python.pywrapfst._MutableFst.rmepsilon
   openfst_python.pywrapfst._MutableFst.arcsort

Detailed description of operations
****

.. automodule:: openfst_python.pywrapfst
   :members: determinize, compose, shortestpath, 

.. automodule:: openfst_python.pywrapfst._MutableFst
   :members: minimize, project, rmepsilon, arcsort