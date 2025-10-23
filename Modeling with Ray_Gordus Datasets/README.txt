## AIB Modeling Datasets - Our Datasets ## 
Written by Amanda Ray (written 04.05.25, latest update: 10.16.25)

The datasets are provided for the publication, “Nonlinear integration of sensory inputs and behavior by a single neuron in C. elegans”.
DOI: https://doi.org/10.1101/2025.04.05.647390

Code is written using Jupyter Notebook, python version 3.9.7
(for the 'Extracting Data from tif Files (videos).ipynb' notebook, computer used to run this has python version 3.7.12)

All calcium videos were cropped and processed with 'Extracting Data from tif Files (videos).ipynb' to extract fluorescence data, which is provided. Raw videos not provided for the sake of saving space due to large file sizes.

( Detailed code for how to read and analyze data will be provided )
* Files include the following numpy datasets for modeling:
 - “WT AVA-AIB-AIA.npy”
15 AVA-AIB-AIA recordings from WT worms

- “WT AWC.npy”
20 AWC recordings from WT worms

- “nmr-1_HisCl AVA-AIB-AIA.npy”
20 AVA-AIB-AIA recordings from motor-silenced worms (nmr-1::HisCl)

- “str-2_HisCl AVA-AIB-AIA.npy”
14 AVA-AIB-AIA recordings from AWC-silenced worms (str-2::HisCl)

- “ins-1s_HisCl AVA-AIB-AIA.npy”
12 AVA-AIB-AIA recordings from AIA-silenced worms (ins_1s::HisCl)

* All files contain raw traces for neurons (with the last column containing background fluorescence), background subtracted traces, and normalized traces. 


# Normalization process: 
(data provided already contains normalized traces, but if you are curious about the process, it's done with: Processing Neuron Data (Smoothing and Normalization).ipynb)

* All raw and background corrected traces start with 300 frames (30 seconds, 10 fps) of no stimulus. This plus an additional 50 frames are cut off in the beginning during processing to exclude photodecay artifacts in the beginning.

* These truncated traces are then smoothed by shifting traces by 5 frames at the beginning and end of each trace, to reduce jittering and noise.

* Finally, these smoothed traces are normalized for each neuron for one set of experiments (odor, red light, odor+red light). This is done to fully capture the dynamic activity of each neuron across a full set of experiments. Since some experiments (ie red light for AWC) are designed to not stimulate all neurons, if each individual trace was normalized and the neuron was inactive, the normalization would amplify the inactivity as noise. 

* These normalized traces will be used for modeling. Individual codes for each model will be provided. 


# Dataset formatting:

* Data provided are in numpy files (listed above), and are in dictionary format. 

* Dictionary (d) formatting example: 
{‘Worm0_Raw’: {‘NeuronX ExpA’: array([Data]), ‘NeuronX ExpB’: array([Data]) etc through rest of worms }, 
‘Worm0_BG Corr’: {‘NeuronX ExpA’: array([Data]), ‘NeuronX ExpB’: array([Data]) etc through rest of worms}, 
‘Worm0_Norm’: {‘NeuronX ExpA’: array([Data]), ‘NeuronX ExpB’: array([Data]) etc through rest of worms}}

* Where, for each worm, dictionary loops through raw traces (d[’Worm#_Raw’]), then background corrected traces (d[’Worm#_BG Corr’]), then normalized traces (d[’Worm#_Norm’]). 

* Within each key (raw, bg corr, norm), dictionary loops through each neuron (AVA, AIB, AIA, or AWC separately), where each neuron loops through all 3 experiments (odor, red light, odor+red light; simplified into Odor, Red, Both), such that the ordering would be [‘AVA Odor’], [‘AVA Red’], [‘AVA Both’] - repeat for other neurons. 

* In datasets with ‘AVA-AIB-AIA’ in the filename, order of neurons is always AVA first, AIB second, and AIA last. 

# Detailed code for how to pull out data for each type of trace, worm, neuron, and experiment is provided and explained in their respective scripts.

# Recommended workflow, because you will need resulting parameters from each step for the next model:
1. Modeling Neuron Data - Single Neuron Convolution.ipynb
2. Modeling Neuron Data - Summation.ipynb
3. Modeling Neuron Data - Sliding (Time-dependent sensory).ipynb
4. Modeling Neuron Data - Derivative (Reversal-dependent).ipynb

# I will also provide the resulting parameter numpy files, if you don't to run all the models. You can also use these to compare your resulting parameters to make sure your outputs are correct and you are running the scripts properly. 

## Other Codes Provided ##

# Comparing deltaF of AIB Dynamics.ipynb 
# This is how we compared the AIB dynamics between WT and nmr-1::HisCl (motor-silenced) worms in Supplemental Figure 5A.

# Modeling Shifting AWC Pulses Relative to AVA Onset.ipynb
# This is how we computationally modeled one AWC pulse and time-shifted it relative to AVA onset for Figure 6.