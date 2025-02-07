---
title: "Intern - iCeBound Project (HEPIA, CERN and the City of Geneva)"
permalink: /industry/hepia
excerpt: " In 2016, I collaborated with the Haute école du paysage, d'ingénierie et d'architecture (HEPIA), the CERN and the city of Geneva on the iCeBound project. The project aimed at calculating the solar radiation map of the city of Geneva, such that this provides a prior quantitative information on the amount of produceable solar energy induced by specific solar pannel installations.  

	The calculation model heavily relied on a specific and critical parameter, denoted as as Sky Viewing Factor (SVF). Every location in space would have a specific SVF value between 0 and 1, describing the amount of clear sky view for that location, depending on the surrounding buildings. The SVF calculation for a small piece of land suffered extremely high computational costs on its initial CPU implementation. 

	My task consisted therefore in leveraging my experience at Sony (see below), and port the calculations on GPUs with minor algorithmic modifications. The designed solution provided a spectacular speed up. For this project, I was jointly supervised by Prof. Jan S. Hesthaven from EPFL and Prof. Nabil Abdennadher from HEPIA. I collaborated extensively with Dr. John White from CERN, and Dr. Gilles Fourestey from the Scientific IT and Application Support (SCITAS) of EPFL. 

"
collection: industry
---

## Overview

The iCeBound project is a collaborative project between Hepia, CERN and the city of Geneva, that focuses on designing and developing a Decision Support System that leverages 3D digital urban data to facilitate environmental analyses in cities. The main desired usage of such a tool is to evaluate the potential of building roofs located in urban areas for producing solar energy and to identify good candidate roofs for installing solar panels, by calculating a yearly radiation map for the whole city of Geneva.


![Digital Urban Surface Model (DUSM) of Geneva repartitioned in tiles](../images/Geneva_in_tiles.png)

The model for computing the radiation map relies on a computationally costly algorithm, the Sky Viewing Factor, as this took initially around 150 minutes on 40 CPUs to be computed for a small portion of land. My primary task was to transfer an existing cloud based implementation to GPUs in order to investigate the potential of acceleration and a subsequent deployment of the GPU based software.

![Block diagram for calculating the radiation map](../images/block_diagram_radiation_process.png)


The outcome of the project was quite satisfying, as it led to a demonstrated 
acceleration of two orders of magnitude (10 times faster on a single GPU compared to 40 CPUs), hence enabling the modeling of the entire Geneva region. The implementation on multiple GPUs was further deployed on the Amazon Web Services cloud for public use purposes, with a treatment cost reduced by a factor of 100 in comparison with the initial code version.

<iframe src="../slides/master_thesis_hepia.pdf" width="100%" height="600px"></iframe>

![PDF Preview](path/to/first-page-image.jpg)

[Download the PDF](path/to/your/file.pdf)


