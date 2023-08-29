# Temporal Dynamics ECoG (TDE) Matlab code repository

This repository contains Matlab code to reproduce analyses and figures reported in Piantoni G, Montenegro S, Flinker A, Devore S, Devinsky O, Doyle W, Dugan P, Friedman D, Ramsey N, Petridou N, Winawer JA (2022) Temporal dynamics of neural responses in human visual cortex. The Journal of Neuroscience 42(40):7562-7580  (https://doi.org/10.1523/JNEUROSCI.1812-21.2022).

Paper figures can be reproduced by running the scripts located in mkFigures/. 

The full pipeline, to extract and process the data for the analyses reported in the paper, can be run using the script tde_run.m

## Instructions on using the code

First, it is necessary to download the BIDS-formatted data from OpenNeuro: 
Visual ECoG dataset https://openneuro.org/datasets/ds004194

The files located in the derivatives/Groen2022TemporalDynamics/ folder on OpenNeuro should be placed in a directory inside this Github repository named 'analysis' (see function help for analysisRootPath.m). 

The script tde_run.m contains demo code showing how to extract and preprocess the data from the main BIDS directory and how to fit temporal models to the resulting neural time courses. 

## A high level analysis on the repo works
Architecture and Flow of the temporalECoG Repository:

  Scripts Directory:
        Contains primary scripts to preprocess data and run the pipeline.
        Main scripts:
            preprocessECoGBOLD.m, preprocessPRF.m, preprocessRET.m: Used for preprocessing various types of data.
            runPipeline.m: A wrapper to execute the entire pipeline.
            spatiotemporalECoG.m: The central script to analyze spatiotemporal ECoG data.
            wrapECoGBOLD.m, wrapPRF.m, wrapRET.m: Wrappers for preprocessing functions.

  Utils Directory:
        Houses utility functions that are called by main scripts and other functions.
        Functions deal with data manipulation, processing, and formatting, among other tasks.
        Examples include fitNakaRushton.m (fits the Naka-Rushton function to contrast-response data) and groupElecsByVisualArea.m (groups electrodes based on atlas assignments).

  External Directory:
        Contains third-party functions or scripts that are utilized by the main code. For example:
            cbrewer.m: Provides color maps.
            nanconv.m: Convolves data with a kernel, treating NaNs as missing values.

   Temporal Models Directory:
        Expected to have scripts related to various temporal modeling techniques, which we have yet to explore in detail.

   mkFigures Directory:
        Likely contains scripts to generate figures, visualizations, and plots based on the analysis, which we have yet to explore.

Working:

   Data Preprocessing:
        Raw data undergoes preprocessing to extract relevant signals and format the data for analysis.
        Preprocessing varies based on the data type, e.g., ECoGBOLD, PRF, or RET.

   Electrode Grouping:
        Electrodes are grouped based on their assignments in the atlas.
        Probabilistic assignments are also possible, where electrodes are assigned to visual areas based on given probabilities.

   Data Analysis:
        Once preprocessed, the data is subjected to various analysis techniques, potentially including the fitting of temporal models, contrast-response fitting, etc.
        The analysis aims to decode or predict the visual stimulus from the brain activity.

   Visualization:
        Results from the analysis are visualized using various plots, providing insights into the neural representations of visual stimuli.

## Dependencies

The code has dependencies to the following toolboxes:

- https://github.com/WinawerLab/ECoG_utils
- https://github.com/fieldtrip/fieldtrip
- https://github.com/acerbilab/bads

When using the repository, it may be helpful to make use of the ToolboxToolbox which is a Matlab toolbox provided by provided by ToolboxHub to manage code/toolbox dependencies. See https://wikis.nyu.edu/display/winawerlab/ToolboxToolbox for more instructions on how to set it up. The relevant ToolboxToolbox config associated with this Github repository is located here: https://github.com/WinawerLab/ToolboxRegistry/blob/master/configurations/temporalECoG.json

Some of the data (e.g. retinotopic atlases) were computed using code located in:
https://github.com/BAIRR01/BAIRanalysis

## Contact

Please contact Iris Groen (i.i.a.groen@uva.nl, https://orcid.org/0000-0002-5536-6128) for questions.
