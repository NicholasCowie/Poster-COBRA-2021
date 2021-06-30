# Poster
![](fig/Poster_Nicholas_Cowie_COBRA_2021.pdf?raw=true)

# Links to Referenced Software
[Maud](https://github.com/biosustain/Maud) -> Kinetic Modeling Software
[Stan](https://mc-stan.org) -> Bayesian Inference Package

# References
1. Gutenkunst, R. N. et al. Universally sloppy parameter sensitivities in systems biology models. PLoS Computational Biology 3, 1871–1878 (2007).
2. Stan Development Team. 2021. Stan Modeling Language Users Guide and Reference Manual, 2.26.0. https://mc-stan.org

# Methionine Cycle
## Pathway
![](fig/Methionine_Cycle.png?raw=true)

## Measurement Distributions
Comparing the posterior distribution to the prior, it's easy to see a strong contraction towards the measured values. The prior concentrations
and fluxes vary on the order of magnitute level, whilst this is less prevalent in the posterior.
![](fig/exp_forest.png?raw=true)

## Parameter Distributions
The dramatic increase in posterior performance for the measured variables is less noticable in the parameters, where most posteriors span similar
orders of magnitude as their prior.
![](fig/kinetic_forest.png?raw=true)
