# Introduction

The **GUI_environments** is a graphical user interface (GUI) developed in Matlab aimed to calculate connectivity matrices using parcellated data (i.e. Gordon<sup>1</sup>  or HCP<sup>2</sup>  parcellation schemas) processed following the surface-based registration pipelines implemented in the DCAN lab (https://www.ohsu.edu/school-of-medicine/developmental-cognition-and-neuroimaging-lab) where the data are saved as ciftis in BIDS format folders <sup>3/sup>.


The **GUI_environments** applies motion censoring and calculate connectivity matrices controlling the number of frames across participants. This GUI calculate connectivity matrices using 3 different methods or environments:

- Standard. Connectivity matrices using Pearson-correlations.
- No-autocorrelation. Same as before but after removal of autocorrelation.
- Connectotyping. Using a model based approach as defined in the manuscript Connectotyping: Model Based Fingerprinting of the Functional Connectome”  (still Work in Progress due to figuring out a way to generalize jonb submission in different clusters).

To run it, you need an iterative Matlab session and also to have access to the processed data


# References


1. Gordon EM, Laumann TO, Adeyemo B, Huckins JF, Kelley WM, Petersen SE. 2014. **Generation and Evaluation of a Cortical Area Parcellation from Resting-State Correlations**. Cereb Cortex. 26(1):288–303. doi:10.1093/cercor/bhu239. [accessed 2014 Oct 15]. http://www.cercor.oxfordjournals.org/cgi/doi/10.1093/cercor/bhu239.

1. Glasser MF, Coalson TS, Robinson EC, Hacker CD, Harwell J, Yacoub E, Ugurbil K, Andersson J, Beckmann CF, Jenkinson M, Smith SM, Van Essen DC, 2016. **A multi-modal parcellation of human cerebral cortex**. Nature, 536, pp. 171–178.

1. Gorgolewski KJ, Alfaro-Almagro F, Auer T, Bellec P, Capotă M, Chakravarty MM, Churchill NW, Cohen AL, Craddock RC, Devenyi GA, et al. 2017. **BIDS apps: Improving ease of use, accessibility, and reproducibility of neuroimaging data analysis method**s**. PLoS Comput Biol. 13(3):e1005209. doi:10.1371/journal.pcbi.1005209. http://www.ncbi.nlm.nih.gov/pubmed/28278228.