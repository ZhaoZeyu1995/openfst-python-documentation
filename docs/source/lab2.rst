Lab 2: FST with Weight 
====

In Lab2, we will learn how to assign weights to transitions (or arcs) of an FST by applying the class :python:`Weight`.
To compute the total weight for a path in an FST, a simple example is provided to show you how to do it with the APIs in :python:`openfst_python`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab2.ipynb>`_ to view the jupyter notebook file for this lab.


.. autosummary::
   openfst_python.pywrapfst.Weight


Weighted FST
***********

Now, let's create an FST object with :python:`Weight`.

.. autoclass:: openfst_python.pywrapfst.Weight

>>> import openfst_python as fst
>>> f = fst.Fst('log') # Note the string 'log'
>>> type(f)
>>> <class 'pywrapfst._MutableFst'>

To create an FST object with weights, we use :python:`fst.Fst()`, and pass a string :python:`'log'` to it, indicating the weights of the FST are from log semiring.  

>>> s1 = f.add_state()
>>> s2 = f.add_state()
>>> w = fst.Weight('log', 10) # Note 'log' is the weight type and 10 is the value.
>>> f.add_arc(s1, fst.Arc(0, 0, w, s2)

In the above example, we first add two states in the FST, then instantiate a weight object :python:`w = fst.Weight('log', 10)`, and add an arc from :python:`s1` to :python:`s2` with :python:`w`.
You might wonder why we need to instantiate a :python:`Weight` object but not simply passing a :python:`float` value to :python:`fst.Acr()`.
The reason is that the weights in a WFST must be the elements from a semiring, so with the class :python:`Weight`, the addition and multiplication operations are defined.
Thus, as you will see below, when you compute the weight along a path in an FST, you have to transform the :python:`Weight` to :python:`float` by :python:`float()`.

Traverse a WFST and Compute Weights
**********

Below are the useful functions for traversing a WFST.

.. autoclass:: openfst_python.pywrapfst._MutableFst
   :members: final, arcs, start, states

>>> # Suppose f is a WFST that we have already created by openfst_python.
>>> start_state = f.start() 
>>> # get the start state of an FST
>>> for arc in f.arcs(start_state): 
>>> # use Fst.arcs(state) to obtain an iterator of the arcs departing from the state
>>>     print(arc.ilabel, arc.olabel, arc.weight, arc.nextstate) 
>>>     # print out the input label, the output label, the weight and the next state of the arc.
>>>     weight = float(arc.weight) 
>>>     # please remember to transform it to float before you do any calculations
>>> for state in f.states(): 
>>> # use Fst.states() to get an iterator of all the states in the FST
>>>     print(state) 
>>>     # print out the state 
