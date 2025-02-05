---
title: "ML-based Short Physical Performance Battery future score prediction based on questionnaire data"
collection: publications
category: manuscripts
permalink: /publication/ML-based-sppb-future-score-prediction-based-on-questionnaire-data
excerpt: 'A paper elaborated throughout a close collaboration with Dr Macin Kolakowski from Warsaw University of Technology (WUT) during the CAREUP project. We explain the methodology developed for prediction patients Intrinsic Capacity.' #This paper is about fixing template issue #693.'
date: 2024-11-17
venue: '32nd Telecommunications Forum (TELFOR)'
paperurl: 'https://ieeexplore.ieee.org/abstract/document/10819122'
citation: 'Kolakowski M., Ben Bader S.'
---

Effective slowing down of older adults’ physical capacity deterioration requires intervention as soon as the first symptoms surface. In this paper, we analyze the possibility of predicting the Short Physical Performance Battery (SPPB) score at a four-year horizon based on questionnaire data. The ML algorithms tested included Random Forest, XGBoost, Linear Regression, dense and TabNet neural networks. The best results were achieved for the XGBoost (mean absolute error of 0.79 points). Based on the Shapley values analysis, we selected smaller subsets of features (from 10 to 20) and retrained the XGBoost regressor, achieving a mean absolute error of 0.82.