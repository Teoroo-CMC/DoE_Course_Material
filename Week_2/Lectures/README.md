# Lectures  


## Lecture 1: Introduction to DoE and full factorial designs
Imagine a generic example of a chemical process in a plant where the input file contains the table for the parameters range as shown above. If we build a full-factorial DOE out of this, we will get a table with 81 entries because 6 factors permuted in 2 levels result in 2$^6$=64 combinations! 

Clearly, the full-factorial designs grow quickly! Engineers and scientists, therefore, often resort to using half-factorial/fractional-factorial designs where they confound one or more factors with other factors and build a reduced DOE. See example in the [DoE full factorial design notebook.](Jupyter-notebooks/DOE_example.ipynb) and notebooks for [workshop 3](../Workshop_3/Jupyter-notebooks/DoE-2factor_full.ipynb)

## Lecture 2: Block design and fractional factorial designs
Let’s say we decide to build a 2-level fractional factorial of this set of variables with the 4th variables as the confounding factor (i.e. not an independent variable but as a function of other variables). If the functional relationship is “A - B - C - BC” i.e. the 4th parameter vary depending only on the 2nd and 3rd parameter, see example in notebooks prepared for [workshop 4](../Workshop_4/Jupyter-notebooks/fractional_design.ipynb)


## Lecture 3: Experimental design and optimization
