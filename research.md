---
layout: page
title: Current Research
---

I deal mainly in **quasars** and **high-redshift galaxies**. My research for the past several years has dealt with studying the host galaxies of high-redshift quasars, especially to better understand quasar triggering or feeding mechanisms. I leverage my strong background in **programming** and **math** to analyze data using modern computational and statistical methods.

### psfMC ###

{% include figure.html url="/images/psfmc_posterior.png" caption="Example of parameter covariance in the quasar model below" class="image-float-right"%}

{% include icon-github.html username="mmechtley/psfMC" %}

My dissertation work revolved around improved methods for modeling and subtracting quasar point sources from imaging data, especially Hubble Space Telescope Wide Field Camera 3 images. I developed [psfMC](https://github.com/mmechtley/psfMC), a software tool for Bayesian 2D surface brightness modeling -- think of it as MCMC [galfit](https://users.obs.carnegiescience.edu/peng/work/galfit/galfit.html). Users supply a [model file](https://github.com/mmechtley/psfMC/blob/master/examples/model_J0005-0006.py) defining a parameterized model (Any number of point sources, Sérsic profiles, etc.) and prior distributions for each parameter, and the software then handles drawing MCMC samples from the posterior distribution. It propagates per-pixel statistical uncertainties and produces a series of images as well as a trace database of the posterior samples. You can then learn about parameter covariances that the simpler gradient descent methods don't provide.

{% include figure.html url="/images/psfmc_subtract.png" caption="psfMC modeling example from Mechtley et al. 2016 ApJ 830, 156" %}


### Quasar Host Galaxy Morphologies at z=2 ###

{% include icon-adsabs.html abs="2016ApJ...830..156M" text="Mechtley et al. 2016 ApJ 830, 156" %}

The most frequently proposed model for the origin of quasars holds that the high accretion rates seen in luminous active galactic nuclei are primarily triggered during major mergers between gas-rich galaxies. While plausible for decades, this model has only begun to be tested with statistical rigor in the past few years. We have recently focused on the host galaxies of quasars at z=2, during the peak of quasar activity and cosmic black hole growth. In a study of high-mass black holes that dominate the BH mass function at this redshift, we found no significant difference in merger fraction between 19 quasars hosts and a sample of 84 inactive galaxies. We are now performing a similar study of high-Eddington ratio quasars, to test the hypothesis that the highest accretion rates require mergers as a particularly efficient feeding mechanism.

{% include figure.html url="/images/high_mass_z2_merger_fractions.png" caption="Merger fraction in high-mass z=2 quasars, compared to massive inactive galaxies (Mechtley et al. 2016)" %}

### Rest-Frame UV Properties of z=6 Quasar Host Galaxies ###

{% include icon-adsabs.html abs="2012ApJ...756L..38M" text="Mechtley et al. 2012 ApJ 756 L38" %}

Details to follow
