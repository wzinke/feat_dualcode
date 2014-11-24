feat_dualcode
=======

This code is inspired by the paper of E.A. Allen, E.B. Erhardt, and V.D. Calhoun (*Neuron* 2012), see also their associated web page: [http://mialab.mrn.org/datavis](http://mialab.mrn.org/datavis)

They suggest a simple, yet thorough representation scheme for statistical maps that were obtained with an fMRI GLM analysis. Their idea behind this is to "Show more, hide less!". This representation shows significant clusters of voxels as contour outline and with solid colors, non-significant voxels code their subthreshold value as hue, and the parameter estimate is represented as color map (see example image). This way, the representation gives a quick impression of what is in the data, how large and reliable effects are.

This neat plotting scheme was implemented here as matlab function that can cope with 3D nifti files. In addition to this, a wrapper BASH script is provided that allows to easily create dual coded images from an existing feat directory.

![Example slices of a statistical map that represents the parameter estimate as color code and the corresponding z-value as hue. Significant clusters are indicated by contour lines and are shown with solid colors.](samplemap.png?raw=true)

Please cite the original paper of Allen, Erhardt, and Calhoun when using the scripts provided here: 

**Elena A. Allen, Erik B. Erhardt, & Vince D. Calhoun** (2012). Data Visualization in the Neurosciences: Overcoming the Curse of Dimensionality. *Neuron* **74**, 603 - 608

This Github repository is associated with this DOI: [![DOI](https://zenodo.org/badge/4883/wzinke/feat_dualcode.png)](http://dx.doi.org/10.5281/zenodo.12835)
