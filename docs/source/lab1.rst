Lab 1: Basic FST Manipulation
====

There are three classes used in Lab 1: :python:`_MutableFst`, the main class for an FST "mutable" (ie. that can be dynamically modified in the code); :python:`Arc`, which is the arc object used to connect states in an FST; and :python:`SymbolTable`, which maps input or output strings to the integer IDs used as arc labels by OpenFst.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab1.ipynb>`_ to view the jupyter notebook file for this lab.


.. autosummary::
   openfst_python.pywrapfst.SymbolTable
   openfst_python.pywrapfst._MutableFst
   openfst_python.pywrapfst.Arc


SymbolTable
***********

First, let's have a look at how to create a :python:`SymbolTable`.

>>> # Here is an example of instantiating a SymbolTable
>>> import openfst_python as fst
>>> st = fst.SymbolTable()

You will use two main methods of the class:

.. autoclass:: openfst_python.pywrapfst.SymbolTable
   :members: add_symbol, find


To add a new symbol to a symbol table,

>>> idx = st.add_symbol('a')
>>> idx
>>> 0 # as you can see above, the method, add_symbol, returns the index corresponding to the label 'a', because this is the first label we add into the symbol table.
>>> idx = st.add_symbol('b')
>>> idx
>>> 1 # this time it returns 1, as 'b' is the second label we add into the symbol table

To find the index corresponding to a label already in the symbol table, we can use the method :python:`SymbolTable.find()`

>>> idx = st.find('a')
>>> idx
>>> 0 # the label 'a' is in the symbol table, so it returns its index, and here it is 0.
>>> idx = st.find('c')
>>> idx
>>> -1 # the label 'c' is not in the symbol table, so it returns :python:`NO_SYMBOL` value, which here is -1 by default.

To recap, the :python:`SymbolTable` is just a mapping between the text symbol (:python:`string`) and the internal index used by OpenFst (:python:`int`).



Fst
**********

Now, let's create an FST object.

>>> f = fst.Fst()
>>> type(f)
>>> <class 'pywrapfst._MutableFst'>

To create an FST object, we use :python:`fst.Fst()`, but the instantiated object :python:`f` is an instance of the class :python:`pywrapfst._MutableFst`.  "Mutable" means that returned FST can be dynamically manipulated in the code.

Here are some frequently used class method used in the labs.

.. autoclass:: openfst_python.pywrapfst._MutableFst
   :members: add_state, add_arc, set_start, set_final, set_input_symbols, set_output_symbols

Here are some basic examples.

To add a new state in the Fst,

>>> new_state = f.add_state()
>>> new_state
>>> 0 # add_state() returns the state index (:python:`int`) for the state (new_state) we just added.

To set the state we just added (new_state) as the start state for the Fst,

>>> f.set_start(new_state)

Let's add another state and set it as the final state for the Fst,

>>> another_new_state = f.add_state()
>>> f.set_final(another_new_state)

To set a :python:`SymbolTable`, say input_symbols, as the input symbol table for our Fst,

>>> f.set_input_symbols(input_symbols)

To set a :python:`SymbolTable`, say output_symbols, as the output symbol table for our Fst,

>>> f.set_output_symbols(output_symbols)

The remaining method, :python:`add_arc()` will be mentioned in the following section together with :python:`fst.Arc`.

Arc
**********

The final class we'll inclue here is :python:`fst.Arc`.

.. autoclass:: openfst_python.pywrapfst.Arc

Let's see a simple example.

>>> import openfst_python as fst
>>> f = fst.Fst() # instantiate an fst._MutableFst object
>>> # Let's add two states into f.
>>> state1 = f.add_state() 
>>> state2 = f.add_state()
>>> arc = fst.Arc(0, 1, None, state2) 
>>> # We instantiate an arc here with 0 as the input index, 
>>> # 1 as the output index, 
>>> # None as the weight (we will talk more about weights in Lab 2), 
>>> # and state2 as the next state.
>>> f.add_arc(state1, arc) # Add the arc to our fst from state1

