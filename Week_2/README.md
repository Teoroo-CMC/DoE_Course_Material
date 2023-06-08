# Week 2: DoE - Design of Experiments

By the end of this part of the course, you should be able to:
- Understand how experimental design can be used for the building of empirical models
- Understand key issues in statistical design of experiments

Before attending these lectures, it would be good to freshen up your knowledge about statistics. Please have a looka at the [Workshop "extra"](Workshop_extra/README.md), which cover some excercises in basic probability and statistics using python. 
## What is Experimental design?
The best way to introduce the need for experimental design is to use an example. To understand scientific phenomena is common to perform experiments where we change *one variable at a time* (OVAT): 

* Change one variable
* Keep everything else constant to the best of your ability
* See how the results change

This procedure is very intuitive and often serves as a common practice in science. But is is efficient? Well, let's propose that we want to optimize the yield of a particular synthetic reaction. We then first have to decide What possible *factors* that would influence the yield of a chemical reaction. Here are some examples: 

* Concentration of Reagent 1
* Concentration of Catalyst
* Concentration of Catalyst Ligand
* Solvent
* Temperature
* Reaction Time

Any more? 

That's already a lot of possible things to change, so we make it simple. Let's imagine  that we just change catalyst loading and temperature:

<img src="./Lectures/Jupyter-notebooks/Figures/DoE.png" width="300" />

1. We start at our initial concentration of 0.5 mM and scan temperature (10, 20, 30, 40, 50, 60°C)

<img src="./Lectures/Jupyter-notebooks/Figures/Temperature.png" width="300" />

We find a maximum at 40°C.  
2. We now scan concentration at our initial temperature of 40°C:

<img src="./Lectures/Jupyter-notebooks/Figures/Concentration.png" width="300" />

From this study it looks like our best conditions are 40°C and 2 mM of catalyst! This is a much better yield than at the (118.g vs. 85.g initial)

However, is this the best we can do? 

In fact, if we would perform experiments where we would have changed the concentration at every temperature, we would have seen that the best conditions are at 50°C, 2.5 mM of catalyst, yielding 123.g of product!

<img src="./Lectures/Jupyter-notebooks/Figures/Response.png" width="300" />

**Why did we miss our best conditions?**

There are often interactions between otherwise independent factors in our experiments. Maybe temperature and concentration are correlated *together*?

Instead of varying one variable at a time, we should use Design of Experiments (DoE).

<img src="./Lectures/Jupyter-notebooks/Figures/grid.png" width="300" />

Note if we pick the four "corner" points, we'll get a much better idea if there's an interaction between the two variables. One of them is likely to be close to the best point.

Even better, we could add a center point.


**Iterative Design of Experiments**

We don't want to assume that we can answer all the questions in one huge experiment. Particularly when we start out, we may not know which factors contribute. Maybe the critical step in the reaction is really fast, so reaction time doesn't matter much.

Even in my example here, picking the four "corner points" won't exactly find the best point. But we'll learn that we should investigate more carefully the upper left region (higher temperature, higher concentration) in subsequent studies.

When we perform this *iterative* process, we will often want to balance **exploration** and **exploitation**
- **Exploration** - sampling new regions / conditions which have high uncertainty
- **Exploitation** - trying to find the best near the points we have tried already

After all, performing experiments of any kind is often expensive and time-consuming. It is therefore important that we don't to much in the wrong areas and that we learn as much as we can from each experiment. Box and Norman (see reference in reading list) talks about different classes (stages) (WHICH, HOW, WHY) 
- Screening (WHICH Stage)
  - aiming to determine the subset of important parameters from a given larger set of potentially important parameters
- Empirical Model Building (HOW stage)
  - Determine empirically the effects of the known input parameters
  - Build approximate function for local interpolation 
- Mechanistic Model Building (WHY Stage) 
  - Build function for extrapolation 

The use of DoE will take us from the screening stage to the level of local optimization or mechanistic understanding for global optimization in the most efficient way. 

**So, what can we learn?**

- Screening studies: vary a few things to determine which factors are important (e.g., in combination with ANOVA)
    - Consider the efficiency of a rechargable battery. The redox levels of the anode and cathode matter (voltage). But you also care about the mass, volume, speed of recharging … etc.
- Modeling a process: similar - get a better understanding of a system
    - Maybe a process has interactions or nonlinear effects?
- Optimization: finding the best yield, best coffee, etc.

**How is it done?**
Mathematically, we usually treat this as an example of **multiple regression**:

$$
Y=\beta_{0}+\beta_{1} X_{1}+\beta_{2} X_{2}+\beta_{12} X_{1} X_{2}+\text { experimental error }
$$

In other words, we'll add an *interaction* term $\beta_{12} X_{1} X_{2}$ that can capture any correlations between the two variables.

We can also consider quadratic or nonlinear terms:

$$
Y=\beta_{0}+\beta_{1} X_{1}+\beta_{2} X_{2}+\beta_{11} X_{1}^{2}+\beta_{22} X_{2}^{2}+\text { experimental error }
$$

In general, we might have a *lot* of factors and interactions.

Second-order interactions are pretty common. Maybe a catalyst doesn't work as well at higher temperature (e.g., it decomposes). Or light roast coffee requires longer brew times?

In general, third-order interactions and higher are much less common. This is good because we essentially get replication "for free."



## Course Content
- [Lecures](/Week_2/Lectures/README.md)
  - Lecture 4 - Introduction to DoE and factorial design (chapter 1 and 4 ) 
  - Lecture 5 - Block design and fractional factorial design (chapter 5)
  - Lecture 6 - Optimization using DoE (Chapter 6) 
- Workshops
  - [Workshop 4 - Full factorial design and analysis of results (chapter 4)](/Week_2/Workshop_4/README.md)
  - [Workshop 5 - Block design and fractional factorial design (chapter 5)](/Week_2/Workshop_5/README.md)
- Laboration
  - [Laboration 1 - DoE in in practice](/Week_2/Lab_1/README.md)  

These lectures and work shops are inteded to introduce you to the topic of DoE. However, the field is much more ... Modern design of experiments are often full optimization problems (which is fun!) and could involve DoE's based on machine learning or Bayesian methods to minimize errors and maximize the chance of finding the best solution in the fewest experiments or measurements. My hope is that this introduction give you the basis to start using DoE for the benefit of your own research. 


## Reading Material
Also, please have a look at the reading material. The main book is: 
- Chapter 1, 4, 5, 6 of Empirical model-building and response surfaces by George E. P. Box and Norman R.Draper, Wiley Series in probability and mathematical statistics (ISBN 0-471-81033-9)
  
There is also a book in swedish that cover almost everything (except chapter 6):  
- Försöksplanering för utveckling och förbättring, Bo Bergman, Martin Arvidsson, Ida Gremyr, Studentlitteratur 2017 (ISBN 978-91-44-11658-7) (book in swedish)

-------
Parts of this text is adapted from Prof. Geoffrey Hutchison, University of Pittsburgh
https://github.com/ghutchis/chem1000

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>