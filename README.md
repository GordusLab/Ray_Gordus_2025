## AIB Modeling Datasets - NeuroPAL Dataset ## 
Written by Amanda Ray (written 10.21.25)

This repository is for the publication, “Nonlinear integration of sensory inputs and behavior by a single neuron in C. elegans”.
DOI: https://doi.org/10.1101/2025.04.05.647390

Code is written using Jupyter Notebook, python version 3.9.7


# This repository includes numpy files and notebooks to analyze AIB activity in response to some specified input using convolution modeling. There are two folders provided, each with their own README for proper usage:

# 1. Modeling with Ray_Gordus Datasets
This folder contains:
- Modeling notebooks to reproduce modeling of AIB activity in the publication (single-neuron, summation, time-dependent sensory sliding window, and reversal-dependent derivative) using our own generated datasets.
- Numpy datasets for calcium imaging of AIB, AVA, AIA, and AWC for WT and various neuron-silenced animals. 
- Numpy datasets with resulting parameters and residuals from each model. 
- Miscellaneous notebooks for processing calcium imaging data, for comparing AIB dynamics (delta fluorescence), and for sliding an AWC pulse relative to AVA onset.

# 2. Modeling with NeuroPAL Dataset
This folder contains:
- Modeling notebooks to reproduce modeling of AIB activity in the publication (single-neuron, summation, time-dependent sensory sliding window, and reversal-dependent derivative) using the published NeuroPAL dataset.
- Notebook for finding top inputs that are the most correlated to AIB activity in the NeuroPAL dataset.
