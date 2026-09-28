# Survival Analysis of Human Occupation in Southern Africa from 21,000-1,300 years ago
## Objective
This project employs survival curves and Bayesian models to quantify the most porbable length of time that southern African hunter-gatherers used specific technologies.
## Hypothesis
### $H_1$: The length and duration of hunter-gatherer technology is a function of population size.

$H_{1A}$ Robberg technology lasts from 19,923-13,145 years ago
<br>
$H_{1B}$: Oakhurst technology lasts from 12,789-8,705 years ago
<br>
$H_{1C}$: Wilton technology lasts from 7,784-4,636 years ago
<br>
$H_{1D}$: Final Later Stone age technology lasts from 2,898-1,318 years ago
<br>

### $H_2$: The length and duration of hunter-gatherer technology is a function of geographic location and range

$H_{2A}$ Robberg technology has the same duration across all southern African regions
<br>
$H_{2B}$: Oakhurst technology has the same duration across all southern African regions
<br>
$H_{2C}$: Wilton technology has a shortened or absent duration in the southern African interior and greater duration along the coastal margins
<br>
$H_{2D}$: Final Later Stone age technology has the same duration across all southern African regions
<br>

# Methods
This project tests the presumed relationship between prehistoric technologies, geographic range, and demographics in southern Africa over the past 20,000 years. I use the largest collection of soutern Africa's radiocarbon database to determine the ages in which certain sites contained one technology over another and during which calendar period. I then model these via a Weibull distribution via Bayesian techniques to generate posterior probabilities for how long each technology was used. I use two Bayesian models to evaluate 1) the overall length of each technology across southern Africa, and 2) the length of each technology conditioned on southern African geographic range. In both cases, I allow the shape parameter to vary randomly via technological classifications, assuming different rates of change between prehistoric technologies.

## Database
The Southern African Radiocarbon Database (SARD) represents the largest up-to-date collection of radiocarbon data from southern Africa. This database contains information on the site names, biome, technology, and radiocarbon samples (**Figure 1**). Lombard and colleagues used a similar set of radiocarbon data to infer the most probable periods for each technological toolkit including the Robberg, Oakhurst, Wilton, and Final Later Stone Age (**Table 1**)
