---
title: "AI/ML Research Scientist (Eclexys)"
excerpt: " In 2022, I joined [Eclexys](http://eclexys.com) a cybersecurity company located in Lugano, Switzerland. My primary responsibility was to develop innovative machine learning strategies for detecting malicious activity, using data gathered from a variety of sources. Given the company's strong cybersecurity expertise in securing medical data, I also contributed to healthcare projects focused on delivering innovative AI approaches. This experience allowed me to collaborate on the development of ML solutions for several European healthcare projects funded by Horizon 2020.

	The link above provides an overview of my professional journey at Eclexys, which includes exciting AI-driven projects in both cybersecurity and healthcare."
collection: industry
---

## Overview

During my professional experience at Eclexys, I had the opportunity to work on AI cutting-edge projects that blended both cybersecurity and healthcare. This period included meaningful work in those fields, with several notable projects that helped me grow both technically and professionally.

---

## Cybersecurity

### Project 1: Malware detection

In this project, the idea consisted in analyzing collected executables suspected of representing malware samples. The main objective was to leverage their API representation in order to identify main malwares' fingerprints, enabling their systematic detection by AI automated techniques, no matter the obfuscation techniques employed.


#### The starting point
We proceeded by grouping APIs into categories describing their type of actions, e.g. read (r), write (w), or file (f) operations. Likewise, the initial API representation was spanned in a lower dimensional dictionary of actions, in such a way any executable original representation was translated into a finite sequence characters (e.g. fffwwrwrr ... ). 

Note: The dictionary of values grouping APIs is actually much larger than the example cited above, but cannot be disclosed. 

#### Entropy representation
Provided this new representation in terms of finite dictionary values, we could now infer probability distributions and leverage Shannon entropy representation for each executable. This not only provided a conversion in numerical values of original samples, but also provided a powerful graphical insight, allowing for immediate naked eye detection of similar patterns between different samples. 

![Entropy representation](path/to/your/image1.png)

#### Explored solutions
Being able to detect similar malwares by simply comparing their entropy representation is an interesting feature but much more may be achieved with ML techniques. By considering the entropy representation as numerical time-series, several methods can be employed here for classification. However, leveraging time-series clustering in this situation might be quite tedious due to their different lengths, and the employed obfuscation techniques.

![Obfuscation and different signal lengths](path/to/your/image1.png)

#### Optimal retained solution
 After several employed methods around entropy representation, a step back was taken by reconsidering the character representation of each sample. We decided to employ instead NLP techniques, assuming that each malware throughout its fingerprint, might associate a specific language or a discussion topic. Likewise, the problem cann be undertaken as text classification. Applying therefore regular NLP methods shall be much more robust, not only considering the different "documents" lengths, but also in regards with the noise introduced by obfuscation. 

 The solution pipeline goes as follows: 
 - **Text embedding**: we embed numerically each document (the character representation for original samples) throughout employing TF-IDF or context-based methods such as Doc2Vec
 - **Latent space representation**: For retaining the maximum of information, the dimension set for Doc2Vec is quite high and can constitute a challenge for clustering. By employing auto-encoders on the Doc2Vec embedding, we rsignificantly reduce the vectors dimensions' and retain their latent representation, a much more powerful condensed set of information can be extracted
 - **Manifold learning method**: We combine the auto-encoder by "a manifold learning technique which ex-
plicitly takes local structure into account, that increases the quality of the representation learned in terms
of clusterability" (cite the article, talk about deep clustering). We used t-SNE and UMAP that behaved slightly better and was more stable. For the dimension, we typically choose half the dimension of the latent representation. 
- **Clustering**: Since we are supposed to evolve in the wild with no information on categories (number of malwares we will recover in a given database), we proceed to clustering. Density-based methods were preferred in absence of any assumption on reduced data distribution and homogeneity (therefore no K-means nor Gaussian Mixture Models).

#### The benchmark
Although the algorithm was designed to be employed in the wild, we still needed some benchmark for evaluating the methodology. We designed a database of 1000 well identified malwares, distibuted homogeneously across five families. The result was 100% classification accuracy, and the method was judged stable with respect to the several hyperparameters (Doc2Vec several parameters, auto-encoder dimension, manifold learning method parameters). 

![Clustering results](path/to/your/image1.png)

#### Deployment
We were able to detect several malwares primarily absent from our database. Once important collection of each was recovered, we built malware classifiers, in a classical multi-class logistic approach.

#### Summary

- **Role**: Lead Network Engineer
- **Technologies used**: Dimensionality reduction methods (t-SNE, UMAP), NLP (TF-IDF, Doc2Vec), auto-encoders, clustering
- **Benchmark**: 1000 samples belonging to five malware families 
- **Results**: 100% classification accuracy on the benchmark, several new malwares detected on deployment 
- **Deployment**: Successful deployment, continuous running and follow-up on novel detections

![Secure Network Infrastructure](path/to/your/image1.png)

### Project 2: Command prompt analysis - Anomaly detection & deviation from baseline (masquerade detection)
In this project, I performed a thorough vulnerability assessment of internal systems, identifying and mitigating security risks that could have been exploited by attackers.

- **Role**: Security Analyst
- **Technologies used**: Nessus, Metasploit, Burp Suite
- **Results**: Identified and fixed 50+ critical vulnerabilities

![Vulnerability Assessment](path/to/your/image2.png)

---

## Healthcare

### Project 1: AI-Based Diagnostic Tool
As part of the AI healthcare team, I contributed to the development of an AI-based diagnostic tool that aids doctors in diagnosing rare diseases by analyzing medical imaging data.

- **Role**: AI Research Assistant
- **Technologies used**: TensorFlow, Python, CNNs
- **Results**: Achieved 85% diagnostic accuracy, improving early detection of diseases

![AI Diagnostic Tool](path/to/your/image3.png)

### Project 2: Predictive Healthcare Analytics
This project focused on using machine learning to predict patient outcomes based on historical data, aiming to improve healthcare delivery and resource allocation.

- **Role**: Data Scientist
- **Technologies used**: Scikit-learn, Pandas, Jupyter
- **Results**: Developed a model with 90% accuracy for predicting patient risk levels

![Predictive Healthcare Analytics](path/to/your/image4.png)

---

## Conclusion
This experience has provided a solid foundation in both cybersecurity and AI healthcare, which I continue to build upon in my career.
