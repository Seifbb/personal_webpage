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

- **Goal**: Detect and identify malwares from raw API representation 
- **Technologies used**: Dimensionality reduction methods (t-SNE, UMAP), NLP (TF-IDF, Doc2Vec), auto-encoders, clustering (DBSCAN, HDBSCAN)
- **Benchmark**: 1000 samples belonging to five malware families 
- **Results**: 100% classification accuracy on the benchmark, several new malwares detected on deployment 
- **Deployment**: Successful deployment, continuous running and follow-up on novel detections

![Secure Network Infrastructure](path/to/your/image1.png)

### Project 2: Command prompt analysis - Anomaly detection & deviation from baseline (masquerade detection)

In the realm of cybersecurity and IT management, monitoring command prompt activities is crucial for
detecting unauthorized actions and ensuring system integrity. Command prompts, while powerful tools
for legitimate users, can also serve as entry points for malicious activities if misused. Automated analysis
of command prompt activities not only helps in proactive monitoring but also significantly enhances the
ability to quickly respond to potential threats. 

In this project, we therefore addressed command prompts and the possibility of raising automated alerts on the basis on detected malicious or unusual activities. We developed essentially two approaches:
- **Supervised**: Detecting specific Atomic Red Teaming (ART) attacks  
- **Unsupervised**: Detecting irregular activities within a specific network

We furthermore developed active learning techniques that took advantage from domain expertise in order to reduce False Positives during deployment.

#### Command prompts tokenization and NLP embeddings 
Although structured and following a specific logic, command prompts, unlike natural language, does not provide a straightforward decoupling into tokens. A specific work needed to be done with this regards that takes into consideration existence of paths, network-specific directories' names, parameters' variablity (e.g. a different ProcessId's, times, etc, ...), and several other aspects that might interfere with comparing specific actions or intent of a set of commands. 

We here addressed the problem by leveraging and comparing the performance of several tokenizations that decouples paths in different ways, lowered the influence of directories' name, and created placeholders for a certain type of parameters, such as numbers, hashes, IP addresses, and so on. Once the tokens are produced within a specific corpus, we use regular NLP techniques for numerically embedding each command. We compared FastText and TF-IDF, both in the word and character based fashion. 

#### Supervised approach for ART detection
Since we needed labeled data for this approach, we used ART attacks from an open-source project developed by Red Canary (c.f. [https://github.com/redcanaryco/atomic-red-team](https://github.com/redcanaryco/atomic-red-team)). The initiative provides a library of security tests, which are mapped to the MITRE ATT&CK® framework.

We constructed a labeled dataset around this data (as positive class instances), coupled with locally generated data from regular network activity, simulated on our labs (as negative class instances). As model, we opted for XGBoost and hypertuned parameters to reach training and test accuracies of respectively 98,45% and 97,5%. We conducted a benchmark experiment where we run around 500 ART attacks, randomly executed within a network of computers. The rate of attacks compared to the amount of regular commands represented around 1%. The experiments results yielded a precision of approximately 93% and a recall of 87%.  

#### Unupervised approach for detecting deviation from baseline activities
Malicious activity within a network do not necessarily characterize throughout ART attacks. We therefore developed a second approach meant for detecting irregular activity that deviates from the standard behaviour of a specific user. The aim consisted in generating alerts for actions, that were either considered by domain experts as legit and simply novel (install new programs, softwares, new user), either evaluated as suspicious and worth further investigation. The algorithm acted therefore as a decision support system for domain experts to monitor and assess thousands of daily commands, while only leveraging a very little number of alerts. 

For this approach, we relied on auto-encoders. More specifically, we selected data from a specific network and made sure no malicious activity were detected. This data was then used for training an auto-encoder, for which a distribution of the reconstruction loss was constructed. A threshold corresponding to 98th-percentile of that distribution was then fixed, and command prompts with a higher reconstruction loss were judged irregular. 

Building performance metrics' on this approach is somehow not straightforward, since "irregular activity" is not necessarily malicious. We therefore asked our domain experts during deployment to assess the alerts for whether the latter were considered interesting and worth further exploration, or whether they were simply uninteresting. The experiments were conducted on three separate and distinct network and yielded precisions of 39%, 74% and 79%. The difference in results found explanation in the quantity of available data on each network, where precision systematically augmented with more available data. 

#### Active learning for the unsupervised approach


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
