# About

This page details the steps to set up and run the GUI_environments script (written by Oscar Miranda-Domínguez (miran045@umn.edu)).
Repo location: `https://gitlab.com/Fair_lab/GUI_environments`

# Introduction

The **GUI_environments** is a graphical user interface (GUI) developed in Matlab aimed to calculate connectivity matrices using parcellated data (i.e. Gordon[^1]  or HCP  parcellation schemas) processed following the surface-based registration pipelines implemented in the DCAN lab (https://www.ohsu.edu/school-of-medicine/developmental-cognition-and-neuroimaging-lab) where the data are saved as ciftis in BIDS format folders.


The **GUI_environments** applies motion censoring and calculate connectivity matrices controlling the number of frames across participants. This GUI calculate connectivity matrices using 3 different methods or environments:

- Standard. Connectivity matrices using Pearson-correlations.
- No-autocorrelation. Same as before but after removal of autocorrelation.
- Connectotyping. Using a model based approach as defined in the manuscript Connectotyping: Model Based Fingerprinting of the Functional Connectome”  (still Work in Progress due to figuring out a way to generalize jonb submission in different clusters).

To run it, you need an iterative Matlab session and also to have access to the processed data

[^1]. Test