---
title: "Space-time multilevel quadrature methods and their
application to cardiac electrophysiology"
collection: publications
category: manuscripts
permalink: /publication/2015-10-01-paper-title-number-3
excerpt: 'TBD-description.' #This paper is about the number 3. The number 4 is left for future work.'
date: 2023-01-01
venue: 'Journal 1'
slidesurl: #'http://academicpages.github.io/files/slides3.pdf'
paperurl: 'https://epubs.siam.org/doi/abs/10.1137/21M1418320'
citation: 'Ben Bader S., Harbrecht H., Krause R., Multerer M., Quaglino A. and Schmidlin M.'
---

In this paper, we present a novel approach which aims at high-performance uncertainty quantification for cardiac electrophysiology simulations. Employing the monodomain equation to model the transmembrane potential inside the cardiac cells, we evaluate the effect of spatially correlated perturbations of the heart fibers on the statistics of the resulting quantities of interest. Our methodology relies on a close integration of multilevel quadrature methods, parallel iterative solvers, and space-time finite element discretizations, allowing for a fully parallelized framework in space, time, and stochastics. Extensive numerical studies are presented to evaluate convergence rates and to compare the performance of classical Monte Carlo methods such as standard Monte Carlo (MC) and quasi-Monte Carlo (QMC), as well as multilevel strategies, i.e., multilevel Monte Carlo (MLMC) and multilevel quasi-Monte Carlo (MLQMC) on hierarchies of nested meshes. We especially also employ a recently suggested variant of the multilevel approach for nonnested meshes to deal with a realistic heart geometry.