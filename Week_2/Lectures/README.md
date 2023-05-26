# DoE - Design of Experiments 
Knowledge about Design of Experiment (DOE) has become critical in this age of rapidly expanding the field of data science and associated statistical modeling and machine learning. Knowledge about efficient DoE techniques is important for any scientist or engineer planning to conduct experimental analysis. A well-planned DOE can give a researcher meaningful data set to act upon with the optimal number of experiments preserving critical resources.
To do good science with data, one needs to collect it through carefully thought-out experiments to cover all corner cases and reduce any possible bias.

## What is a scientific experiment?
In its simplest form, a scientific experiment aims at predicting the outcome by introducing a change of the preconditions, which is represented by one or more independent variables, also referred to as “input variables” or “predictor variables.” The change in one or more independent variables is generally hypothesized to result in a change in one or more dependent variables, also referred to as “output variables” or “response variables.” The experimental design may also identify control variables that must be held constant to prevent external factors from affecting the results.


## Empirical models 

## Why Experimental Design?
Experimental design involves not only the selection of suitable independent, dependent, and control variables but planning the delivery of the experiment under statistically optimal conditions given the constraints of available resources. There are multiple approaches for determining the set of design points (unique combinations of the settings of the independent variables) to be used in the experiment.

Main concerns in the experimental design include the establishment of validity, reliability, and replicability. For example, these concerns can be partially addressed by carefully choosing the independent variable, reducing the risk of measurement error, and ensuring that the documentation of the method is sufficiently detailed. Related concerns include achieving appropriate levels of statistical power and sensitivity.

The need for careful design of experiments arises in all fields of serious scientific, technological, and even social science investigation — computer science, physics, geology, political science, electrical engineering, psychology, business marketing analysis, financial analytics, etc…

For real-life engineering problems, it arises more often than you think. The engineering experiment budget is often limited and you still have to build a Machine Learning model. How would you gain the maximum exposure to all dimensions of data/ response still staying within the budget?


"… essential aim of Data Science is to conduct the highest quality scientific investigation and modeling with real-world data. And to do good science with data, one needs to collect it through carefully thought-out experiments to cover all corner cases and reduce any possible bias."

"The engineering experiment budget is often limited and you still have to build a Machine Learning model. How would you gain the maximum exposure to all dimensions of data/ response still staying within the budget?" 


# Different experimental design schemes 
The list below summarizes some of the available DoE schemes,

Full factorial,
2-level fractional factorial,
Plackett-Burman,
Sukharev grid,
Box-Behnken,
Box-Wilson (Central-composite) with the center-faced option,
Box-Wilson (Central-composite) with the center-inscribed option,
Box-Wilson (Central-composite) with the center-circumscribed option,
Latin hypercube (simple),
Latin hypercube (space-filling),
Random k-means cluster,
Maximin reconstruction,
Halton sequence-based,
Uniform random matrix

## Full/fractional factorial designs
Imagine a generic example of a chemical process in a plant where the input file contains the table for the parameters range as shown above. If we build a full-factorial DOE out of this, we will get a table with 81 entries because 6 factors permuted in 2 levels result in 2$^6$=64 combinations! 

Clearly, the full-factorial designs grow quickly! Engineers and scientists, therefore, often resort to using half-factorial/fractional-factorial designs where they confound one or more factors with other factors and build a reduced DOE. See example in the [DoE full factorial design notebook.](Jupyter-notebooks/DOE_example.ipynb) and notebooks for [workshop 3](../Workshop_3/Jupyter-notebooks/DoE-2factor_full.ipynb)

Let’s say we decide to build a 2-level fractional factorial of this set of variables with the 4th variables as the confounding factor (i.e. not an independent variable but as a function of other variables). If the functional relationship is “A - B - C - BC” i.e. the 4th parameter vary depending only on the 2nd and 3rd parameter, see example in notebooks prepared for [workshop 4](../Workshop_4/Jupyter-notebooks/fractional_design.ipynb)


## Central-composite design
A Box-Wilson Central Composite Design, commonly called ‘a central composite design,’ or response-surface-methodology (RSM) contains an embedded factorial or fractional factorial design with center points that is augmented with a group of ‘star points’ that allow estimation of curvature. The method was introduced by George E. P. Box and K. B. Wilson in 1951. The main idea of RSM is to use a sequence of designed experiments to obtain an optimal response.

Central composite designs are of three types. One central composite design consists of cube points at the corners of a unit cube that is the product of the intervals [-1,1], star points along the axes at or outside the cube, and center points at the origin. This is called Circumscribed (CCC) designs.

Inscribed (CCI) designs are as described above, but scaled so the star points take the values -1 and +1, and the cube points lie in the interior of the cube.

Faced (CCF) designs have the star points on the faces of the cube. Faced designs have three levels per factor, in contrast with the other types that have five levels per factor. The following figure shows these three types of designs for three factors.


## Latin Hypercube design

Sometimes, a set of randomized design points within a given range could be attractive for the experimenter to assess the impact of the process variables on the output. Monte Carlo simulations are a close example of this approach. However, a Latin Hypercube design is a better choice for experimental design rather than building a complete random matrix as it tries to subdivide the sample space into smaller cells and choose only one element out of each sub-cell.

In statistical sampling, a square grid containing sample positions is a Latin square if (and only if) there is only one sample in each row and each column. A Latin Hypercube is the generalization of this concept to an arbitrary number of dimensions, whereby each sample is the only one in each axis-aligned hyperplane containing it.

When sampling a function of N variables, the range of each variable is divided into M equally probable intervals. M sample points are then placed to satisfy the Latin Hypercube requirements; this forces the number of divisions, M, to be equal for each variable. This sampling scheme does not require more samples for more dimensions (variables); this independence is one of the main advantages of this sampling scheme. This way, a more ‘uniform spreading’ of the random sample points can be obtained.

Users can choose the density of sample points. For example, if we choose to generate a Latin Hypercube of 12 experiments from the same input files, that could look like the following. Of course, there is no guarantee that you will get the same matrix if you run this function because these are randomly sampled, but you get the idea!

## Further extensions
Currently, one can only generate various DOE and save the output in a CSV file. However, some useful extensions can be thought of,

More advanced randomized sampling based on model information gain i.e. sample those volumes of the hyperplane where more information can be gained for the expected model. This, of course, requires an idea of the input/output model i.e. which parameters are more important.
Add-on statistical functions to generate descriptive statistics and basic visualizations from the output from various experiments generated by the DOE function.
Basic machine learning add-on functions to analyze the output from various experiments and identify the most important parameters.


# Experimental design and optimization