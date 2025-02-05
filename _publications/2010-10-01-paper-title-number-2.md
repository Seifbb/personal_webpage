---
title: "Space-time multilevel Monte Carlo methods and their
application to cardiac electrophysiology"
collection: publications
category: manuscripts
permalink: /publication/Space-time-multilevel-monte-carlo-methods-and-their-application-to-cardiac-electrophysiology
excerpt: 'The first and one of the main papers published during my thesis. We treat the uncertainty related to heart fibers orientation and its effects on the cardiac activation map. We conduct Monte-Carlo studies and use multilevel strategies for reducing the computational costs.' #'This paper is about the number 2. The number 3 is left for future work.'
date: 2021-02-02
venue: 'Journal of Computational Physics'
slidesurl: #'http://academicpages.github.io/files/slides2.pdf'
paperurl: 'https://doi.org/10.1016/j.jcp.2021.110164'
citation: 'Ben Bader S., Benedusi P., Quaglino A., Zulian P., and Krause R.'
---

In this paper, we present a novel approach aimed at high-performance uncertainty quantification for time-dependent problems governed by partial differential equations. In particular, we consider input uncertainties described by a Karhunen-Loève expansion and compute statistics of high-dimensional quantities-of-interest, such as the cardiac activation potential. Our methodology relies on a close integration of multilevel Monte Carlo methods, parallel iterative solvers, and a space-time discretization. This combination allows for space-time adaptivity, time-changing domains, and to take advantage of past samples to initialize the space-time solution. The resulting sequence of problems is distributed using a multilevel parallelization strategy, allocating batches of samples having different sizes to a different number of processors. We assess the performance of the proposed framework by showing in detail its application to the solution of nonlinear equations arising from cardiac electrophysiology. Specifically, we study the effect of spatially-correlated perturbations of the heart fibers' conductivities on the mean and variance of the resulting activation map. As shown by the experiments, the theoretical rates of convergence of multilevel Monte Carlo are achieved. Moreover, the total computational work for a prescribed accuracy is reduced by an order of magnitude with respect to standard Monte Carlo methods.