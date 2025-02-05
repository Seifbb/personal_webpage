---
title: "Data-centric workloads with MPI_Sort"
collection: publications
category: manuscripts
permalink: /publication/data-centric-workloads-with-mpi-sort
excerpt: 'After my Ph.D. thesis, I worked for a short period of time as a Research Assistant and collaborated essentially with Dr. Diego Rossinelli and Dr. Patrick Zulian on wirting a paper about a sorting algorithm that they have elaborated.' #This paper is about fixing template issue #693.'
date: 2024-02-17
venue: 'Journal of Parallel and Distributed Computing'
paperurl: 'https://www.sciencedirect.com/science/article/abs/pii/S0743731523002034'
citation: 'Zulian P., Ben Bader S., Fourestey G., Krause R., and Rossinelli, D.'
---

Sorting is a fundamental task in computing and plays a central role in information technology. The advent of rack-scale and warehouse-size data processing shaped the architecture of data analysis platforms towards supercomputing. In turn, established techniques on supercomputers have become relevant to a wider range of application domains. This work is concerned with multi-way mergesort with exact splitting on distributed memory architectures. At its core, our approach leverages a novel and parallel algorithm for multi-way selection problems. Remarkably concise, the algorithm relies on MPI_Allgather and MPI_ReduceScatter_block, two collective communication schemes that find hardware support in most high-end networks. A software implementation of our approach is used to process the Terabyte-size Data Challenge 2 signal, released by the SKA radio telescopes organization. On the supercomputer considered herein, our approach outperforms the state of the art by up to 2.6X using 9,216 cores. Our implementation is released as a compact open source library compliant to the MPI programming model. By supporting the most popular elementary key types, and arbitrary fixed-size value types, the library can be straightforwardly integrated into third-party MPI-based software.
