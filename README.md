# Poster
![][image-1]

# Links to Referenced Software
[Maud][1] -\> Kinetic Modeling Software \\
[Stan][2] -\> Bayesian Inference Package

# Methionine Cycle
The methionine cycle is a fundamental pathway in human metabolism. Its intermediates participate in a variety of mechanisms competing for the same resources.  These functions all occur simultaneously resulting in a highly regulated pathway with approximately 6 allosteric effectors. In order to understand the operation of the methionine cycle we constructed a kinetic model as a system of ODEs, where the state variables are the metabolite concentrations and the fluxes are constrained by mechanistic rate laws. However, these systems are described as ‘sloppy parameter’ systems, where the marginal parameter distributions can be large, yet still display tight posterior predictions. Furthermore, measuring these parameters independently is obscured by measuring the system in _in vitro_ conditions, as opposed to those experienced _in vivo_. This prevents the standard practice of placing tight priors on the parameter values. 

## Rerunning simluation
The previous sampling run did not converge between chains, upon rerunning the simulation with a longer warmup and samling phase we were able to achieve all Rhat values \< 1.01. The rerun of simulations was conducted with simulated data constraining all metabolites and assuming 10% noise. The number of simulated experiments is 2 and the new data is under `data/simulation_study_input`

## Pathway
![][image-2]

## Measurement Distributions
Comparing the posterior distribution to the prior, it's easy to see a strong contraction towards the measured values. The prior concentrations
and fluxes vary on the order of magnitude level, whilst this is less prevalent in the posterior. 
![][image-3]

## Parameter Distributions
The dramatic increase in posterior performance for the measured variables is less noticeable in the parameters and is typical of sloppy parameter systems<sup>1</sup>. Most posteriors span similar orders of magnitude as their prior, especially with the Michaelis-Menten constants (kms). This isn't the case with equilibrium constants (keqs), whose values, in combination with metabolite concentrations determine the directionality of fluxes.
![][image-4]

### Pair plots
In order to understand how the sloppy parameter system arrises we can observe the pair plots, specifically for the enzyme CBS1. This enzyme has a highly correlation between the kcat parameter and the Michaelis-Menten (Km) constant for hcyc-L. A possible explanation of this is rate law is multiplicatively  degenerate with kcat/Km = constant. This typically is not the case as the Km also influences enzyme saturation and may explain why the Km for ser-L is not highly correlated. 

![][image-5]

Another interesting observation is the skewed equilibrium constants within MS1 and AHC1. There also appears to be interesting interactions between the Kms as well as Keqs within these enzymes as well. This interaction likely arises from the Haldane relationship where the reverse catalytic rate for reversible reactions is constrained by the Keq and Kms. This could result in higher dimensional correlations that are unidentifiable in pair plots. To remove these correlations more experiments must be conducted that constrain the Km parameters. By constraining these parameters further the correlations in the posterior space will dissipate, and potentially improve sampling speed.
![][image-6]
![][image-7]


## Conclusions
 


# References
1. Gutenkunst, R. N. et al. Universally sloppy parameter sensitivities in systems biology models. PLoS Computational Biology 3, 1871–1878 (2007).
2. Stan Development Team. 2021. Stan Modeling Language Users Guide and Reference Manual, 2.26.0. https://mc-stan.org

[1]:	https://github.com/biosustain/Maud
[2]:	https://mc-stan.org

[image-1]:	fig/Poster_Nicholas_Cowie_COBRA_2021.png?raw=true
[image-2]:	fig/Methionine_Cycle.png?raw=true
[image-3]:	fig/exp_forest.png?raw=true
[image-4]:	fig/kinetic_forest.png?raw=true
[image-5]:	fig/pair_plots/CBS1_pairplot.png
[image-6]:	fig/pair_plots/AHC1_pairplot.png
[image-7]:	fig/pair_plots/MS1_pairplot.png