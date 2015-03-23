feat_dualcode
=======

This code is inspired by the paper of E.A. Allen, E.B. Erhardt, and V.D. Calhoun (*Neuron* 2012), see also their associated web page: [http://mialab.mrn.org/datavis](http://mialab.mrn.org/datavis)

They suggest a simple, yet thorough representation scheme for statistical maps that were obtained with an fMRI GLM analysis. Their idea behind this is to "Show more, hide less!". This representation shows significant clusters of voxels as contour outline and with solid colors, non-significant voxels code their subthreshold value as hue, and the parameter estimate is represented as color map (see example image). This way, the representation gives a quick impression of what is in the data, how large and reliable effects are.

Allen et al. provide [example matlab code](http://mialab.mrn.org/datavis/docs/dualcodeExample.zip) that demonstrate an implementation of their representation scheme. This neat scheme was adapted here to cope with 3D nifti files. In addition to this, a wrapper BASH script is provided that allows to easily create dual coded images from an existing feat directory from an [FSL](http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/) analysis.

The matlab script can be used on its own, only the first three arguments are mandatory, the others are optional:

    dualcode_image(bckimg, statmap, betamap, ...
                  [sigmap, slcs, sldim, betarng, alpharng, bckrng, ofl, ip, scl])

The Usage for the command line script is as follows:

    Usage: $0 <featdir> <contnum> <ofl> [options]

    OPTIONS:
            -bck     use different volume as background (must have same geometry)
            -fac     scaling factor to convert copes to something more like PSC
            -mask    apply mask to statistical images
            -dim     slice dimension
            -slc     slices to print (voxel index starts with 0)
                     numbers less than 1 indicate proportional slice numbers
            -s       scaling factor (default: 2)
            -ip      image interpolation (default: 2)
            -zthr    set upper z-threshold (default uses design.fsf)
            -p       cluster p-value (default: 0.01)
                     will rerun cluster threshold
            -2s      run two sided test
                     will rerun cluster threshold
            -beta    set upper threshold for the beta image
            -sig     use alternative mask to select significant voxel
            -brng    set intensity range for background
            -thick   increase width of slice line
            -keep    do not delete temporary files (for debugging)

Here is an example how to call the bash script from the command line:

```bash
    dualcode $featdir/cope1.feat samplemap -2s -zthr 3.2 -p 0.01 -bck $FSLDIR/data/standard/MNI152_T1_2mm_brain-s 2 -ip 2 -slc $(seq 0.3 0.05 0.75)-dim z
```

This call produces an image like this sample:

![Example slices of a statistical map that represents the parameter estimate as color code and the corresponding z-value as hue. Significant clusters are indicated by contour lines and are shown with solid colors.](samplemap.png?raw=true "Example slices of a statistical map that represents the parameter estimate as color code and the corresponding z-value as hue. Significant clusters are indicated by contour lines and are shown with solid colors.")

Please cite the original paper of Allen, Erhardt, and Calhoun when using the scripts provided here:

**Elena A. Allen, Erik B. Erhardt, & Vince D. Calhoun** (2012). Data Visualization in the Neurosciences: Overcoming the Curse of Dimensionality. *Neuron* **74**, 603 - 608

This Github repository is associated with this DOI: [![DOI](https://zenodo.org/badge/4883/wzinke/feat_dualcode.png)](http://dx.doi.org/10.5281/zenodo.12835)

Please feel free to clone or fork this repository. Comments, bug reports, and suggestions for improvement are welcome.
