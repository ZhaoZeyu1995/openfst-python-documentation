Lab 2: Computing HMM probabilities with FST weights 
====

In Lab2, we will learn how to assign weights to transitions (or arcs) of an FST by applying the class :python:`Weight` and how to traverse the arcs and states or a previously-constructed FST using iterators.

To compute the total weight for a path in an FST, a simple example is provided to show you how to do it with the APIs in :python:`openfst_python`.

.. note::
   Please go to the `github repo <https://github.com/ZhaoZeyu1995/asr_labs/blob/master/asr_lab2.ipynb>`_ to view the jupyter notebook file for this lab.


.. autosummary::
   openfst_python.pywrapfst.Weight

Traversing a WFST
**********

Below are the useful functions for traversing a WFST.

.. autoclass:: openfst_python.pywrapfst._MutableFst
   :members: final, arcs, start, states

In this example, we print the arcs for each state in the FST

>>> # Iterate over all the states in the FST
>>> for state in f.states():
>>>     
>>>     # iterate over all arcs leaving this state    
>>>     for arc in f.arcs(state):
>>>          print(state, arc.ilabel, arc.olabel, arc.weight, arc.nextstate)

In this example, we traverse all the arcs of an FST in a depth-first manner.  **Warning: this code will run forever if an FST has self-loops of cycles!**

>>> def traverse_arcs(state):
>>>     """Traverse every arc leaving a particular state
>>>     """
>>>     for arc in f.arcs(state):
>>>         print(state, arc.ilabel, arc.olabel, arc.weight, arc.nextstate)
>>>         
>>> s = f.start()
>>> traverse_arcs(s)

FST Weights
***********

For the purposes of these labs, you can think of the weights on the arcs of your FSTs as being equivalent to negative log probabilities.  That is, *w = -log p*.  We'll use the "log semi-ring", which (roughly) means that summing weights is equivalent to multiplying probabilities.  

.. autoclass:: openfst_python.pywrapfst.Weight
   :members: One, Zero
   
Let's create an FST object with :python:`Weight`.
   
>>> import openfst_python as fst
>>> f = fst.Fst('log') # Note the 'log' means we're using the log semi-ring
>>> type(f)
>>> <class 'pywrapfst._MutableFst'>

To create an FST object with weights, we use :python:`fst.Fst()`, and pass a string :python:`'log'` to it, indicating the weights of the FST are from log semiring.  

>>> s1 = f.add_state()
>>> s2 = f.add_state()
>>> w = fst.Weight('log', 10) # Note 'log' is the weight type and 10 is the value.
>>> f.add_arc(s1, fst.Arc(0, 0, w, s2)

In the above example, we first add two states in the FST, then instantiate a weight object :python:`w = fst.Weight('log', 10)`, and add an arc from :python:`s1` to :python:`s2` with :python:`w`.
You might wonder why we need to instantiate a :python:`Weight` object but not simply passing a :python:`float` value to :python:`fst.Acr()`.
The reason is that the weights in a WFST must be objects from a specific semi-ring, so with the class :python:`Weight`, the addition and multiplication operations are defined correctly.

OpenFst defines two functions :python:`Weight.Zero(), Weight.One()` that return special weights that correspond probabilities of zero and one respectively.  Like other weights, they are stored internally as negative log probabilities.  The toolkit also defines functions python:`fst.plus(), Weight.times()` whose behaviour depends on the semi-ring you are using, but roughly corresponds to the normal operations of summing and multiplying probabilities respectively.  However, these function operate directly on the weights in negative log-probability form.

Here are some examples:

>>> # Initialise some weights using the log semi-ring
>>> w_half = fst.Weight('log', 0.693)  # weight corresponding to probability of 0.5
>>> w_zero = fst.Weight.Zero('log') # weight corresponding to probability of 0
>>> w_one = fst.Weight.One('log') # weight corresponding to probability of 1
>>>
>>> fst.plus(w_zero, w_zero)
>>> <log Weight Infinity>   # 0 + 0 = 0 (=Infinity in negative log domain)
>>>
>>> fst.times(w_zero, w_zero) 
>>> <log Weight Infinity>   # 0 x 0 = 0 (=Infinity in negative log domain)
>>> 
>>> fst.times(w_one, w_zero)
>>> <log Weight Infinity>   # 1 x 0 = 0 (=Infinity in negative log domain)
>>> 
>>> fst.plus(w_one, w_zero) 
>>> <log Weight 0>   # 1 + 0 = 1 (=0 in negative log domain)
>>>
>>> fst.times(w_one, w_one)
>>> <log Weight 0>   # 1 x 1 = 1 (=0 in negative log domain)
>>> 
>>> fst.plus(w_half, w_half)
>>> <log Weight 0>   # 0.5 x 0.5 = 1 (=0 in negative log domain)
>>>                  # Summation uses the formula -log(exp(-w1) + exp(w2)) in log semi-ring
>>>                  # (it won't be exactly this value due to numerical issues)

However, if you prefer to directly compute the weight along a path in an FST without using pre-defined operations, this is possible.  You have to transform the :python:`Weight` to :python:`float` by :python:`float()`.

>>> # Suppose we wish to sum the weights on two arcs, arc1 and arc2
>>> # This is equivalent to multiplying the corresponding probabilities
>>> 
>>> # Using FST operations
>>> weight_sum = fst.times(arc1.weight, arc2.weight)
>>>
>>> # Using direct maths operations to get the same result
>>> float_sum = float(arc1.weight) + float(arc.weight)
