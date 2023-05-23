# DoE - Design of Experiments

By the end of this part of the course, you should be able to:
- Understand "orthogonal" and factorial design
- Understand key issues in statistical design of experiments

Content: 

- Workshop "extra" - Basic math and statistics in python 
- Lecture 3 - Introduction to DoE and factorial design 
- Workshop 3 - Full factorial design  
- Lecture 4 - Fractional factorial design 
- Workshop 4 - Fractional factorial design 
- Lecture 5 - More advanced DoE designs 
- Lab 1 - DoE in in practice. 

These lectures and work shops are inteded to introduce you to the topic. However, the field is much more ... Modern design of experiments are often full optimization problems (fun!) and can involve computational design, machine learning or Bayesian methods to minimize errors and maximize the chance of finding the best solution in the fewest experiments or measurements.

## Why Bother?

We often are introduced to science using the concept of *one variable at a time* experiments (OVAT).

* Change one variable
* Keep everything else constant to the best of your ability
* See how the results change

Let's propose that we want to optimize the yield of a particular synthetic reaction.

We should consider possible *factors* that influence yield, like:

* Concentration of Reagent 1
* Concentration of Catalyst
* Concentration of Catalyst Ligand
* Solvent
* Temperature
* Reaction Time

Phew, that's a lot of possible things to change. Let's imagine just changing catalyst loading and temperature:

<img src="./Figures/DoE.png" width="300" />

1. We start at our initial concentration of 0.5 mM and scan temperature (10, 20, 30, 40, 50, 60°C)

<img src="./Figures/Temperature.png" width="300" />

2. We now scan concentration at our initial temperature of 30°C:

<img src="./Figures/Concentration.png" width="300" />

Great, it looks like our best conditions are 40°C and 2 mM of catalyst! Much better yield (118.g vs. 78.6g initial)

In this example, the best conditions are at 50°C, 2.5 mM of catalyst, yielding 123.g of product!

<img src="./Figures/Response.png" width="300" />

**Why did we miss our best conditions?**

There are often interactions between otherwise independent factors in our experiments. Maybe temperature and concentration are correlated *together*?

Instead of varying one variable at a time, we should use Design of Experiments (DoE).

<img src="./Figures/grid.png" width="300" />

Note if we pick the four "corner" points, we'll get a much better idea if there's an interaction between the two variables. One of them is likely to be close to the best point.

Even better, we could add a center point.

Think about a car's fuel efficiency. We need to try a small engine in a big car and a big engine in a big car .. not just a Prius and a Hummer SUV.

**Iterative Design of Experiments**

We don't want to assume that we can answer all the questions in one huge experiment. Particularly when we start out, we may not know which factors contribute. Maybe the critical step in the reaction is really fast, so reaction time doesn't matter much.

Even in my example here, picking the four "corner points" won't exactly find the best point. But we'll learn that we should investigate more carefully the upper left region (higher temperature, higher concentration) in subsequent studies.

When we perform this *iterative* process, we will often want to balance **exploration** and **exploitation**
- **Exploration** - sampling new regions / conditions which have high uncertainty
- **Exploitation** - trying to find the best near the points we have tried already

After all, performing experiments of any kind is often time-consuming.

**What can we learn?**

- Screening studies: vary a few things to determine which factors are important (e.g., in combination with ANOVA)
    - Consider the efficiency of a rechargable battery. The redox levels of the anode and cathode matter (voltage). But you also care about the mass, volume, speed of recharging … etc.
- Modeling a process: similar - get a better understanding of a system
    - Maybe a process has interactions or nonlinear effects?
- Optimization: finding the best yield, best coffee, etc.

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

-------
This notebook is adapted from Prof. Geoffrey Hutchison, University of Pittsburgh
https://github.com/ghutchis/chem1000

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>