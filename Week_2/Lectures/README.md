# DoE - Design of Experiments 
Knowledge about Design of Experiment (DOE) is important for any scientist or engineer planning to conduct experimental analysis and has become critical in this age of rapidly expanding the field of data science and associated statistical modeling and machine learning. A well-planned DOE can give a researcher meaningful data set to act upon with the optimal number of experiments preserving critical resources.

After all, the essential aim of Data Science is to conduct the highest quality scientific investigation and modeling with real-world data. And to do good science with data, one needs to collect it through carefully thought-out experiments to cover all corner cases and reduce any possible bias.

## What is a scientific experiment?
In its simplest form, a scientific experiment aims at predicting the outcome by introducing a change of the preconditions, which is represented by one or more independent variables, also referred to as “input variables” or “predictor variables.” The change in one or more independent variables is generally hypothesized to result in a change in one or more dependent variables, also referred to as “output variables” or “response variables.” The experimental design may also identify control variables that must be held constant to prevent external factors from affecting the results.

## What is Experimental Design?
Experimental design involves not only the selection of suitable independent, dependent, and control variables but planning the delivery of the experiment under statistically optimal conditions given the constraints of available resources. There are multiple approaches for determining the set of design points (unique combinations of the settings of the independent variables) to be used in the experiment.

Main concerns in the experimental design include the establishment of validity, reliability, and replicability. For example, these concerns can be partially addressed by carefully choosing the independent variable, reducing the risk of measurement error, and ensuring that the documentation of the method is sufficiently detailed. Related concerns include achieving appropriate levels of statistical power and sensitivity.

The need for careful design of experiments arises in all fields of serious scientific, technological, and even social science investigation — computer science, physics, geology, political science, electrical engineering, psychology, business marketing analysis, financial analytics, etc…

For real-life engineering problems, it arises more often than you think. The engineering experiment budget is often limited and you still have to build a Machine Learning model. How would you gain the maximum exposure to all dimensions of data/ response still staying within the budget?


"… essential aim of Data Science is to conduct the highest quality scientific investigation and modeling with real-world data. And to do good science with data, one needs to collect it through carefully thought-out experiments to cover all corner cases and reduce any possible bias."

"The engineering experiment budget is often limited and you still have to build a Machine Learning model. How would you gain the maximum exposure to all dimensions of data/ response still staying within the budget?" 






## Design options
Following design options are available to generate from input variables,

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

### Full/fractional factorial designs
Imagine a generic example of a chemical process in a plant where the input file contains the table for the parameters range as shown above. If we build a full-factorial DOE out of this, we will get a table with 81 entries because 4 factors permuted in 3 levels result in 3$^4$=81 combinations! 

Clearly, the full-factorial designs grow quickly! Engineers and scientists, therefore, often resort to using half-factorial/fractional-factorial designs where they confound one or more factors with other factors and build a reduced DOE. See example in the [DoE full factorial design notebook.](Jupyter-notebook/DOE_example.ipynb)

Let’s say we decide to build a 2-level fractional factorial of this set of variables with the 4th variables as the confounding factor (i.e. not an independent variable but as a function of other variables). If the functional relationship is “A - B - C - BC” i.e. the 4th parameter vary depending only on the 2nd and 3rd parameter, the output table could look like this,