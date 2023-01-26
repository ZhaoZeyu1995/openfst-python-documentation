Welcome to openfst-python documentation!
===================================

There are basically two different types of links available.

Here is an example of the link to another file named :doc:`tutorial`.

Here is an example of the link to a specific section named :ref:`installation`.

Below is an example of Note!

.. note::

   This project is under active development.

For basic usage, please refer to the `official documentation <https://www.openfst.org/twiki/bin/view/FST/PythonExtension/>`_.

This documentation is designed as a complementation for the official one, as you may find that the latter is not that comprehensive.

Contents
--------

.. role:: python(code)
  :language: python
  :class: highlight

Here is an example of toctree, which is like table of content.

There are mainly two parts in this documentation.

The first part :doc:`tutorial` contains most of the frequently used functions and methods in our labs, just in case you are not that familiar with these and you may think the official documentation is not that sufficient for you.
The second part :doc:`api` lists almost all of the functions, classes (including their methods and attributes), which can be also be found by the :python:`help()` function.

>>> help(object) # object represents an abitary object here in openfst_python

.. toctree::
   :maxdepth: 2

   tutorial
   api
