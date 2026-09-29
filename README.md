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
The Southern African Radiocarbon Database (SARD) represents the largest up-to-date collection of radiocarbon data from southern Africa. This database contains information on the site names, biome, technology, and radiocarbon samples (**Figure 1**). Lombard and colleagues (2022) used a similar set of radiocarbon data to infer the most probable periods for each technological toolkit including the Robberg, Oakhurst, Wilton, and Final Later Stone Age (**Table 1**). Whereas, the SARD has the empirically observed technology at each site, **Figure 1** and **Table 1** show do not exactly line up in time or space.
<p align="center">
  <img src="/results/figures/Fig1.png" alt="Figure 1" width="800">
</p>
<p align="center">
  <img src="/results/tables/Table1.png" alt="Table 1" width="800">
</p>


## Radiocarbon Calibration
I use *rcarbon* to calibrate the radiocarbon data for each site. I first separate each site's radiocarbon data into terrestrial-sourced (i.e., wood remains. skeletal remains, etc.) and marine-sourced (i.e., shellfish). I do this because the carbon content in oceans have varying degrees of carbon through time that differ from terrestrial sources, commonly referred to as a *reservoir effect*. Due to this, I offset the marine-sourced. I then combine the dates back together and use the highest density portion of the calibrated dates to determine the age estimates for each technology at each site.

## Bayesian Models
For the Bayesian model development, I had to grapple with the issue that the SARD technology does not end exactly within the periods set by Lombard et al. (2022). To account for this, I right-censored the data. In other words, if the technology ends after the assigned period (*ss.*, Lombard et al. (2022)), I label that site as right-censored. I then compute the duration as the difference between Lombard et al.'s (2022) classification. I add these data to a Bayesian model where I treat the duration as a censored variable as a function of technology and southern Africa's geographic ranges with a Weibull family. I treat shape as a random variable, which I model as a function of technology.
<br>
<br>
I further determine southern Africa's regions via the *Biome* variable within the SARD. I chose to combine those biomes that are adjacent, similar in climate, and have low sample sizes. These include lumping the Nama-Karoo and Savanna biomes into one biome labeled *Interior*; the Succulent Karoo, Fynbos, Thicket, Forest, and Azonal biomes labeled as *Coastal*; and the Indian Ocean Coastal Belt and Grassland biomes labeled as *Grassland*.
<br>
<br>
The first model simply measures the relationship between duration (right-censored) and the technology across southern Africa under a Weibull distribution. I assigned informative priors for the intercept and regression coefficients. The second model measures the relationship between duration (right-censored) and the interaction between technology and southern African biome. I similar assigned informative priors to the intercept and the regression coefficients, including the interaction terms.

# Results
## Model 1: Duration as a function of technolgoy
The posterior distribution for the first model provides evidence that each technology is associated with different length of use (**Table 2**). In particular, there is a systematic decrease in the length of each technology as we get closer to the present with the Robberg assigned to a estimate mean duration of 1,735 years (CI [1,513, 1,998]) and the Final Later Stone Age at an estimated mean 547 year duration (CI [507, 598]).
<p align="center">
  <img src="/results/tables/Table2.png" alt="Table 2" width="500">
</p>

## Model 2: Duration as a function of the interaction between technology and biome
The posterior distribution for the second model confirms the hypothesis that technology duration varies by region in southern Africa (**Table 3**). The exclusion here is the Final Later Stone Age technology, which shows a similar distribution through all regions except the desert biome. However, the extremely large upper credible intervals for the desert biomes in all technological classifications showcase the low sample size within this region.
<p align="center">
  <img src="/results/tables/Table3.png" alt="Table 3" width="500">
</p>
<br>
In regards to my initial hypotheses, there is strong evidence that the Robberg technological duration is similar across all southern African biomes except between the savanna and coastal biomes (P(Savanna duration > Coastal duration) = 0.93) (**Table 4**). In contrast, there are several significant differences for Oakhurst technological duration between southern African regions except between the desert and interior (P(Desert > Interior) = 0.82), Coastal and Interior (P(Coastal > Interior) = 0.2), and savanna and coastal (P(Savanna > Coastal) = 0.53). The Wilton technology is similar across all regions except for between the savanna and coastal biomes (P(Savanna > Coastal) = 0.91). Lastly, the Final Later Stone Age technology is similar across all regions except between the savanna and grassland (P(Savanna > Grassland) = 0.90).
<p align="center">
  <img src="/results/tables/Table4.png" alt="Table 4" width="500">
</p>

# Discussion
## Evaluating the initial hypotheses
My first hypothesis is that technological change and duration is a function of demographic change. Since we have predictions on population size for each technological classification, we can compare these estimates with the posterior estimates for the technological duration. Sealy (2016) suggests that Robberg and Wilton technology are associated with highly mobile, sparsely distributed populations, and the Oakhurst and Final Later Stone Age technologies are associated with greater population size and less mobile groups. My results from the first model provide evidence to refute this hypothesis. Specifically, the model shows a 95% probability that the Robberg duration is longer than the Oakhurst, the Oakhurst is 100% probable to be longer than the Wilton, which is then 100% probable to be longer than the Final Later Stone Age. Therefore, there is no relationship between the technology and estimated population sizes.
<br>
<br>
My second hypothesis stated that duration is a function of the interaction between technology and southern African regions. I expected that the Robberg, Oakhurst, and Final Later Stone Age durations to be similar across all regions while the Wilton technology varied. Specifically, Sealy (2016) estimates the Wilton technology to be increasingly varied between the coastal and interior regions. My results showed that each technology had at least one significantly different technological duration, but Oakhurst showed the majority of regions were significantly different. This contradicts my initial hypothesis and shows that the Wilton technology lasted a similar duration across most regions while the Oakhurst is the period that varied.
<br>
<br>
## Regional differences
