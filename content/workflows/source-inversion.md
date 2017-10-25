---
title: "Source Inversion"
date: 2017-10-24T14:39:58-04:00
---

Accurate earthquake source mechanisms are an important prerequisite for regional or global tomography.  Even with a good source catalog, such as the [Global CMT](http://www.globalcmt.org/) catalog, it is still useful to perform the following quality control check.

Starting with Global CMT solutions, we solve a least squares problem to obtain updated source mechanisms.  In most cases, the difference between starting values and updated values is quite small.  Any large differences, however, require further investigation.

To perform a CMT inversion, the following steps need to be done.

<!-- ![Image of CMT inversion](/SeisStar/img/SourceInversion.jpg =200x100) -->
![CMT Inversion](/workflows/images/SourceInversion.jpg?classes=shadow&width=400px)


The procedure can be further summarized as follows.

#### 1. Prepare CMT files
The CMT inversion is based on finited difference method. i.e, **perturbing the paramters** of CMT solution and calculate waveform difference.  For global CMT solution, we usually invert 9 paramters: Moment tensor[*Mrr, Mtt, Mpp, Mrt, Mrp, Mtp*] and location[*latitude, longitude, Depth*]. Thus, 9 perturbed CMT files should be prepared at this stage.

#### 2. Forward simulation
To obtain updated source mechanisms, we compute **partial derivatives** of **synthetic seismograms** with respect to 6 moment tensor elements and 3 location parameters.  Using forward centered finite differences, 9 forward simulations must be carried out per earthquake.

#### 3. Pre-processing
Operations include **signal processing** and **window selection**.

More information could be found in the [**Pre-processing**](/building-blocks/pre-processing/) page.


#### 4. Source mechanism inversion
As with the gradient computation in Earth structure inversions, the Jacobian computation must be carried out using processed seismic traces.
Once the Jacobian has been computed, it only remains to solve the corresponding linear system.  We use the machinery provided by Pycmt [link] for doing so.

