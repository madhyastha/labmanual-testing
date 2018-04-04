---
title: "Scenes From an AFNI Bootcamp"
author: Tara Madhyastha
sidebar: neuroimaging_sidebar
permalink: neuroimaging_afnibootcamp.html
folder: neuroimaging
---

## Fundamental AFNI Concepts
AFNI has many programs with many options. To simplify there are
"superscripts". The most important of these is `afni_proc.py`, which
is what you should use for fMRI analysis. Another very useful
superscript is `align_epi_anat.py`, which is a general 3D image
aligment program. However, you can also create batch scripts (e.g., in bash) to run a bunch of things.

Most of the examples of AFNI scripts shown below put options a few per
line and use backslashes to format things nicely. Note that if there
is a space after a backslash, which you can't see in an editor, the
command will terminate early, and you will get weird error messages
from the next command line flag. (You laugh. I made this exact mistake
less than 24 hours after writing this.) A lot of AFNI scripts that are
generated use `tcsh` rather than `bash` so you might see different
error messages than you are used to when scripts fail. Be careful.

Scripting conventions are inconsistent. Some are `tcsh` scripts
that you need to run using `tcsh`. Some are scripts that have the
program to run them configured in the first line. The scripts
beginning with `@` are scripts that can be executed from the command line.

Here are some useful AFNI commands.

* 3dinfo - get information about a file
* 3dDeconvolve + 3DREMLfit - multiple linear regression
* 3dvolreg - 3D+time dataset registration
* 3dANOVA + 2dLME - group analyis
* 3dcalc - general purpose voxelwise calculate
* 3dsvm - SVM multi-voxel pattern analysis program.
* 3dresample - reorient and resize dataset voxel grid
* 3dSkullStrip - remove skull
* 3dDWItoDT - diffusion tensor analysis

SUMA is the AFNI surface mapper, for displaying surface models of the cortex. Surfaces are generated from FreeSurfer (or Caret or BrainVoyager). 
All of the 3d* programs are so named to emphasize that they are working on 3d. But over time they have been rewritten to not care whether it is 3d or 2d - so that you can use them on surface data. 

### Data Structures and Naming Conventions
The basic unit of data is the `dataset`. This is a collection of one or
more 3D arrays of numbers. These can be images or calculated
statsitics maps. Each 3D array in a dataset is called a
sub-brick. There is one number in each voxel in each sub brick. The
terminology `brick` was to indicate that it was a 3D thing, as opposed
to a slice. Sub-brick counting begins at 0.

In the dataset there is a header, which includes the dimensions,
orientation, location of dataset in scanner coordinates, time between
sub-bricks (for 3d+time datasets, used for fMRI data) and statistical
parameters associated with each sub-brick.

They are stored in a .HEAD file (with the aux information) and the
.BRIK file, with the data. Datasets can be stored in one of 2 views - the
original data (+orig) view, from the scannner, and the Tailairach view
(+tlrc view) which has been rescaled.  The coordinate system is stored
in the header and in the filename. The reason for putting in the
filename is that it is so important to understanding the data, to compare individuals. Also note - even if you convert to MNI space, the header will reflect this but the file name will still be +tlrc.

Filenames consist of a user-selected prefix, a view, and the suffix
(one of .BRIK or .HEAD). The program selects everything but the
prefix. AFNI also supports nifti files. To write them, end the prefix
with .nii or .nii.gz.

Note that nifti files need to have their sforms correctly set for anything to work with them in AFNI. Depending on how they have been either converted or processed, this might not be correctly set or might be missing. To interrogate the nifti file, use the program `nifti_tool`. For example, to see the header:

```
nifti_tool -disp_hdr -input T1.nii.gz
```

## Keeping up AFNI
Update AFNI using:

```{bash, eval=FALSE}
@update.afni.binaries
```

To get the afni version number, type

```{bash, eval=FALSE}
afni -ver
```
    


## Working With the GUI

I have not gone mad - yes, `afni` is a
graphical user interface (GUI) but it can be totally scripted.  When you start AFNI it loads all
the files that it can read in the current directory. If you start up
AFNI in an empty directory, it creates a dummy image and issues a
warning.  It's a good idea to name anatomical images with the `anat`
prefix so that they are at the top of the alphabet and show up first
as the underlay when you initiate `afni`.

The button labeled `BHelp` at the lower left corner causes the cursor to turn into a hand and provide more extended help when clicking on other things. In particular, click on one of the images after you click on `BHelp` to get a big overview of the keyboard shortcuts. Also look at AFNI Tips, for information about using the GUI.

If you right click on Axial/Sagittal/Coronal buttons on the main AFNI panel, you can "get back" windows that are lost.

You can create nice montages (make sure to set Xhairs to multi to see
multiple crosshairs on other views). To save it you can save the
images as jpgs. Note that the size of the image that you save doesn't
have anything to do with what you actually save - you should choose a
blowup factor that is appropriate. The image is not a screendump; it is created from the raw data.

There are some "hidden menus" that you can see when right clicking on buttons that show up when the cursor changes angle and the head turns orange.

For fun, right click on the top image of the splash screen that comes
up when you click on the AFNI logo in the main window. Click again.


Resizing (especially on a mac) will change the aspect ratio - to make it go back, you can click on the color bar or type ```a``` in the window. If you click on the `EditEnv` button you can change the environment variable that controls this behavior. You can also set the AFNI environment variables in your ```~/.afnirc``` file to enforce the aspect. There are lots of other envionment variables there that you can change "permanently".

```
export AFNI_ENFORCE_ASPECT=YES
```

You can click on the `New` button to open up a new controller, which will bring up a windows with a new letter (B) in the window title. You can open up a new image and the controller are linked - so that you can click on one window and it will go to a coordinate that is close that that coordinate in the linked controller. Theoretically you could go to 10 subjects and see the same region (or create montages) across the individuals (using `Define Datamode -> Lock` buttons).

Clusterize menu. First thing to define is how you determine a cluster. Then you can determine what size of cluster you want. This is quite arbitrary. By default it assumes positive and negative clusters are treated together - if you say Bi-sided it will treat them separately. The `Rpt` button gives you a report.

All of the AFNI functionality is impressive, but what is even more
impressive is that it can be scripted. `@DriveAfni` is a script that
sends commands to the AFNI interface and allows you to script a
sequence of operations (and save montages, movies, etc). For example,
the following command can be used to generate an axial fMRI movie.

```
afni -com 'OPEN_WINDOW A.axialimage'       \
     -com 'SAVE_MPEG A.axialimage FaceReactivity blowup=4' \
     -com 'QUIT'                           \
     facereactivity/001/scan1/nifti/
```

AFNI can take 2D images in realtime from an external program and
assemble them to 3D+time datasets. FMRI scanners at NIH are set up to
start AFNI on a remote Linux computer, use the Dimon program to send
images to AFNI to do real time monitoring of motion, etc.

##Alignment  

Templates that are available are the Colin brain `TT_N27+tlrc` which is the template for cytoarchitectonic atlases (spm_anatomy_toolbox).

```auto_tlrc -base TT_N27+tlrc. -input anat+orig. -suffix NONE
```

## Preprocessing fMRI Data

### Motion Correction
`3dvolreg` is good for EPI motion correction, with 6 dof. It is not good for inter-modal registration. It is very fast for this. 

```{bash, eval=FALSE}
3dvolreg -base 4 -heptic -zpad 4 \
-prefix fred1_epi_vr \
-1Dfile fred_vr_dfile.1D \
fred1_epi+orig 
```
`-base` selects the reference sub-brick. Normally this would be the one closest to the structural image but now it doesn't matter. 
`-prefix` specifies a prefix for the output file 
`-zpad` uses zero padding with that many voxels before shift/rotation, then strips them off afterwards 
`-1Dfile` specifies where output should go. Recall this can be plotted using `1dplot`


### Aligning to T1
Most of the work in aligning the EPI image to the T1 is done by the
Python script `align_epi_anat.py`. This script uses the program
`3dAllineate` to perform affine registration.

`3dAllineate` has different cost functions, and one of the most useful for EPI to T1 is the local (negative) Pearson correlation. We are aligning CSF to CSF across modalities. 
The  `align_epi_anat.py`  script will also do motion correction and slice timing. Below is an example of usage. The flag `-epi_base` indicates which volume (sub-brick) to use as a base for alignment. In FSL `mcflirt` normally this would be the middle volume. AFNI used to recommend that one use the volume taken closest to the T1. However, now the CSF to CSF alignment is so good that it doesn't matter. 

```
align_epi_anat.py -anat T1.nii -epi rawfunctional.nii.gz -epi_base 5 
```

I tried this on a random Udall brain and ran into problems with the skull strip where a major chunk of the cortex was missing. Always fun. To remove the neck and then skull strip, aggressively avoiding ventricles and following suggestions in the help:

```
@clip_volume -below -65 -input T1.nii.gz 
3dSkullStrip  -input T1.nii.gz_clp+orig -blur_fwhm 2 -use_skull -avoid_vent -avoid_vent -init_radius 75 
```

The good skull strip can then be passed to the `align_epi_anat.py`
script to go forward with motion correction, etc.

```
align_epi_anat.py -anat skull_strip_out+origz -epi rest_on_e00213_medn_reoriented.nii.gz  -epi_base 5 -anat_has_skull no
```

The `AddEdge` option makes a QC directory for checking skull strips
and alignment. 

```
align_epi_anat.py -anat anat+orig \
                  -epi epi_r1+orig \
		  -AddEdge -epi_base 0 -suffix _al4class 
cd AddEdge 
afni -niml -yesplugouts &
@AddEdge
```

Or if you decide you want a montage later, you can do the
following. `aiv` is AFNI's own image viewer - you could also use `eog`
or `gimp`.

```
@snapshot_volreg anat+orig epi_r1+orig edges.jpg 
aiv edges.jpg 
``` 

### Some Commands Used For Preprocessing
*`3dToutcount` gives you a list of outliers and gives you the fraction of volumes that are outliers.

*`3dDespike` hammers outliers back towards the trend.

*`3dTshift` does slice timing correction.

*`3dvolreg` registers fMRI data to a base volume (like mcflirt)

*`align_epi_anat.py` aligns fMRI data to the anatomy

*`@auto_tlrc` or `auto_warp.py` registers data to standard space (spatial normalization). `@auto_tlrc` is linear and `auto_warp.py` does nonlinear registration.

*`3dmerge` blurs and cancels noise

*`3dAutomask` masks data. It is not recommended to mask data at single-subject analysis, because there is no good reason to do so - and you can't check what happened outside the head. It is much better to know if there are artifacts outside the mask.

*`3dTstat` and `3dcalc` are used for temporal mean scaling, so that it means something across subjects and space.

### Troubleshooting Alignment
The defaults normally work, but when they don't, what can you do?
If the images start far apart, you might want to use the `-big_move`
or `-giant_move` options. The `-ginormous_move` aligns centers
first. If data are correct normally things should be ok, but if
headers are wrong you can use one of these options. Recall that the
nifti sform needs to be set correctly to use AFNI tools.

If you have poor contrast (e.g. if you can't see the CSF in your data) you will need to use a different cost function. Some options are `-cost lpa`, `-cost nmi` and `-cost lpc+ZZ` (which takes in the lpc and adds in least squares - it is a combination cost function). If you have a lot of non-uniformity in your data you can use the `-edge` or `-cost lpa` options. 


## First Level Analysis

Regressors of no interest make up the global Null Hypothesis in the
model - this is called the "baseline model" in AFNI, or signal changes that
go through time that we don't care about.

In AFNI model, the Fixed Shape HRF is called GAM. The `BLOCK(d)`
function is used to secify HRF for individual responses with a
duration `d` - it is a specific function that is a little longer than
the gam.

The HRF is scaled to have a magnitude of 1, and then the beta values represent the percent signal change. To do this specify `BLOCK(d, p)` where `p=1`. If you forget this beta values won't be so clearly interpretable!

FMRI data = baseline + drift + other effects of no interest + response1 + ... + responek + noise

To model drift, this is a polynomial. In FSL and SPM, this is a
cosine. Although you can control it, by default one polynomial order
per 150 seconds is the default.

You should check the quality of your model. First look at the design matrix report from `3dDeconvolve`. Second, look at the full F-statistis, which tests the baseline + noise model against the baseline + effects of interest + noise model.

You can also look at the determination coefficient R^2 at activated regions (using -rout in 3dDeconvolve). For a block design, this should be around ~50%, for event-related experiments it should be 10-20%. 

Why is the fixed shape HRF approach popular? It assumes a lot - that
the brain responds with the same shape across subjects, activated
regions, conditions/tasks and trials. However, it is easy to handle
and to think about, and works relatively well, especially in block
designs. In block designs, short responses get smeared together so that the shape of the HRF does not matter. But in event related designs it is murkier.

An alternative is where there is no constraint on HRF shape, modeled using basis functions, which in AFNI is called the TENT expansion (pieceline linear splines). There are also cubic splines available.

It is better (statistically) to model the hemodynamic response function at the individual level, which complicates group analysis. 


`3dREMLfit` models the temporal autocorrelation of the noise.

`stim-times` has three rows (one per each run). Each row represents the onset times for the visual reliable stimulus, in seconds. Any timepoints that need to be deleted should be done before passing to 3dDeconvolve.

`afni_proc.py` generates processing scripts, and the command along
with the AFNI version can be included in your publication for
reproducibility (at least at the single subject level). It will copy
results into a new results directory, process data, and create some QA
review scripts. Generated scripts are in `tcsh` syntax, which is a little more readable than `bash`. It is preferable to run `afni_proc.py` for each subject. 

* `-blur x` is the full width half maximum. 
* `regress_censor_motion` says to censor volumes with motion over a particular type
* `regress_est_blur_errts` estimate the blur in the data for cluster correction
* `regress_run_clustsim yes` run 3d cluster simulation as an example for single subject level

*You can pass in FreeSurfer information to generate surface
     information for SUMA. Surface information is stored in NIML data
     format (as `.dset` extensions).

After running `afni_proc.py`, some QC scripts are generated.
`@ss_review_driver` represents the minimum QC that AFNI recommends that you do.

Although `afni_proc` can do the nonlinear warping for you, of course
that is slow. So if you do that, rerunning the subject analysis will
slow the re-run script a lot.  So do the nonlinear warp before, and
supply the warping results so that `afni_proc.py` will skip doing the
warping itself. The `@SSwarper` script does skull stripping and
nonlinear warping. The base dataset that it uses is
`MNI152_2009_template.nii.gz` which is nonlinearly warped and not too
blurry. It is best to use a clear template for nonlinear registration.


## Miscellaneous Interesting Things
 For menus with a lot of items, it is better to right click on the name of the menu to get a scroll down menu.
    
`alignmentacross2sessions` reduces bias across longitudinal time points

`3dlrflip` flips image left and right. Three of the sites in the
FCONN1000 had left/right flipped between the EPI and T1. The
`-check_flip` option to `align_epi_anat.py` will test the cost function with l/r flip and tell you if it is better that way.

If you have the option to collect the first few EPI images (before steady
state is achieved) they are useful -in particular, the first image has
good contrast and can be useful for registration.



You can create a montage of the edges for the registration and view it using the built-in AFNI image viewer `aiv`.


There are scripts and stuff for handling lesions, other animals, etc.

`uber_align_test.py` 



`3dWarpDrive` align similar volumes using affine transform with 12 dof affine
`3dQwarp`, `auto_warp.py` - nonlinear alignment to template

There are a lot of specialized tools, including even a nudge plug-in (which basically never works - don't do alignment manually!)

`3dWarp` will apply nonlinear transforms
`@Align_Centers` will put centers of mass of dataset in the same place, which is important for aligning data from different scanners with different coordinate spaces
`3dTagalign` place and align volumes using fiducial markers
`imreg` align two jpg images


`cat_matvec` concatenates affine matrices

`3dAllineate` applies affine transformation and resamples (sampling can be controlled)

```3dmerge -1blur_fwhm 4.0 -doall -prefix xxxx input```
`3dABoverlap` compute overlaps between masks
`3ddot -dodice` computes Dice coeffient of masks

### Fixing Motion

There is no way to really fix the effect of
motion. Some things we can do are to regress out the motion
parameters, censor volumes, consider motion in the experimental design

The outlier plots are considered preferable to dvars - they are a lot cleaner and reflect deviation from the trend. 

`motion_FT_enorm.1D` the file that is used to set a censoring
limit. This reflects bursts of motion. First, a full X matrix is
created, and then the censored rows are removed. Slow drift over time,
unless they move far enough to change the EPI distortions, are not
considered a problem. An example of that is the subject slowly sinking
into the cushion. It is the bad volumes in motion spikes that screw up
regression.

* `3dUndump` creates ROIs
* `3dROIstats` extracts statistics from the ROIs into a table where columns are regions and rows are the dataset

Rescale each voxel to have a mean of 100 (subject to range of 0-200). This does not effect the shape of the timeseries (except for very minor truncation artifacts) but makes different voxels comparable.

### Setting up Stimulus Files 

`timing_tool`  - can convert timing files from FSL to AFNI
`3ddeconvolve` help page defines the basis functions, and you should use
`dmublock` (onset and does the scaling)
`nifti_tool` - gives nifti information 


## Group Analysis

### Overview of Group Analysis
There are five categories of group analysis techniques: Basic t-tests,
GLM, and traditional ANOVA (where there are multiple groups and one or
more within-subject factors). The fourth category is ANCOVA. Finally,
you may have complicated data (missing data) where you would like to
still use the data, and in that situation you can use linear mixed
effects models. Programs `3dttest`, `3RegAna` and `GroupAna` are obsolete.


Why do we split into individual and group level analyses? Because of complexity - individual subjects may require different QC procedures (censoring), because of computational complexity - but the big group model is a better approach.

The t statistic is the group mean divided by the standard error. We
should be presenting the % signal change as well as the t-statistic and degrees of freedom in the paper.

An ROI based approach can help with the model-building and comparison issue - use half the subjects to identify ROIs.

Nesting - when you can't be in two groups (between-subjects group).

There are three uses of covariate - these can be quantitative variables, variables of no interest that are qualitative or quantitative, or explanatory variables. Covariate does not necessarily mean that it is quantitative, depending on what software package you are using. Considering a covariate to be of no interest can be problematic from a modeling perspective - you don't know for sure that it has no interactions with your explanatory variables.

When you bring Beta value up to the group analysis, you are making an
assumption that the precision of the Beta values is the same. A
more precise measure is to pass up information from the
t-statistic and the Beta up to the higher level. Finally the best
approach is to combine all subjects into one big model.

Beta has a physical interpretation but the t-statistic is dimensionless. Furthermore the t-statistics are not gaussian.

* T-tests
    Use `3dttest++` and `3dMEMA`. `3dMEMA` takes the beta weights and t statistics up to the group level.

* Between-subjects ANOVA. There are many cases of ANOVA and each program handles different cases.
	`3dANOVA` - One way between subjects ANOVA

* Mixed-type ANOVA and others.

`3dLME` - handles all sorts of situations, except that it is computationally expensive. 

`3dMEMA` - compares two conditions using subject-level response magnitudes and estimates of error estimates.
		`3dMVM` - group analysis with multivariate modeling approach, written in R. The `-robust` option is helpful for dealing with outlier covariates.

IntraClass Correlations can be computed in AFNI. Always use ICC(3,1). This checks for a group and session effect. If there is no difference between sessions, it doesn't hurt.

Inter-Subject correlation can be used in naturalistic fMRI. Instead of doing a regression analysis, pair two subjects and do voxelwise correlation between any pair of subjects. For n subjects, this is n(n-1)/2 Inter-Subject Correlations (ISCs).

	

NBS - network based statistics - which is the permutation analysis of network-based analysis, implemented in Matlab toolbox CONN and a python package.

You can analyze subjects with `-allzero_OK` or `-GOFORIT` options to handle the situation where one EV might be missing (e.g., no incorrect trials).

`stim_times_IM k tname model` allows for calculation of many beta weights per run, noisy estimates per block that you can then examine in other ways.

Suppose you have auxiliary behavioral information (ABI), and you want to see if brain activations vary based on that. You basically create a second regressor, the hemodynamic response scaled by the ABI. This is done with option `-stim_times_AM2`. This option takes a times file where time entries are "married" to ABI values. This can be created with the `1dMarry` file.

* `uber_subject.py` generates an `afni_proc.py` command, but it is not totally recommended because it does not support all the options. But it might be a good way to get started.

* `group_gen.py` generates a group analysis script
* `uber_ttest.py` generates a group t-test.

## Standard Space
MNI-anat is shifted from MNI so that it is centered at the anterior commissure. How do you go between TLRC and MNI? There are many ways, including an exact translation of TLRC to MNI.

The Talairach Daemon has some problems - there are incorrectly defined regions that have been there forever. Be careful if using Brodmann areas defined in it. Which atlas you want to see is the `AFNI_ATLAS_COLORS` environment variable.

`file_tool` allows you to check for errors in your files, such as
incorrect (DOS) file type or problems with backslashes, etc.

`gen_group_command.py` can be used to generate the group analysis
commands, to minimize syntax errors.

## ROIs
ROIs are voxels, defined as a mask of voxels. Other packages may define ROIs as a shape, but in AFNI ROIs can be discontiguous. To create an ROI you can draw it, make it from clusters, or take it from an atlas.

*  `3dfractionize` takes a clipping fraction and converts resolution according to that fraction. `3dresample` allows you to convert sampling also, but it has fewer controls for handling partial overlaps.

* `3dmaskdump` takes all voxels within a mask and outputs them to a text file
* `3dRoistats` dumps out statistics for each cluster. Redirect output to text file.

* `whereami` extracts regions, for example:
    
```
 whereami -mask_atlas_region TT_Daemon:left:hippocampus -prefix Lhip
```

* `3dcalc` can also apply atlas masks automatically to data, and is used quite a lot!

## Resting State
Recommended steps for pre-processing can be carried out using
`afni_proc.py`. Steps are:

* despiking
* slice timing
* motion correction
* alignment to anatomy
* spatial normalization
* extract tissue based regressors  (in AFNI you can use `ANATicor`,
  which creates a tissue-based per voxel regressor)
* spatial blurring
* nuisance regression (motion parameters, wm signal, measured
  respiration)
* bandpass filtering (maybe only high pass filtering to remove
  drifts)

Note that you can't do bandpass filtering too and then regress out the
nuisance components.

`3dTproject` allows for voxel-specific regressors. 

These could be accomplished using the following blocks for `afni_proc.py`
`-blocks despike tshift align tlrc volreg blur mask regress`

To remove the mean from the motion regressors and add the temporal derivatives
`-regress_apply_mot_types demean deriv` 

### Programs for Correlating
`3dTcorr1D` correlate all times series in a dataset with time series
in text 1D file
`3dTcorrMap` correlate each voxel time series in the input with every
other voxel, combine in some way, save as a measure of connectivity
`3dAutoTcorrelate`

AFNI GUI InstaCorr is a single subject seed based correlation display that you can access by pointing and clicking.



##Looking at Stuff
`1dplot` is good for looking at 1 dimensional data, such as the X matrix which is generated from the 3dDeconvolve command `-tout` option. In the design matrix, the regressors are shown (historically) from the bottom up. 

`whereami` can provide more detailed information about the output of `3dclust`. To see all the atlases and references for them

```
whereami --show atlases
```

For example, to see overlap of ROIs with atlas-defined regions

```
whereami -omask anat_roi+tlrc
```

`afni_open` is like open on the Mac; it will look for an editor and open the file

## SUMA for Surface Mapping
PreSUMA, the setup phase, creates and corrects surfaces (using, e.g., FreeSurfer). CircumSUMA then maps volumetric data to surface.   Environment variables are specified in `~/.sumarc`. CTRL-s brings up the object controller.  

You can display data in TLRC or MNI space. @SUMA_Make_Spec_FS will bring everything back into the AFNI realm, providing the volume part as NIFTI and the Specification files that define the relationship between surfaces. 

`afni -niml` allows SUMA and AFNI to communicate. 
    
There are a lot of keyboard controls to move around to see the surface. You can link the standard axial, sagittal and coronal views to the surface, viewing the same coordinates in both.

`@SUMA_AlignToExperiment` aligns surface information to T1 data.
`3dVol2Surf` maps volume data to the surface
`SurfSmooth` smooths data on the surface (and is a good reference I
think for a program that manages the surface and knows about its
neighbors)

##Equitable Thresholding and Clustering (ETAC)
The goal is to control
the global false positive rate (FPR), or Family-Wise Error. This is
the rate of errors across the tests - i.e., when anything is found vs
the null hypotheses. This is a different approach to controllling the
FDR (false discovery rate, or the fraction of discoveries that are
errors.

There is a false non-discovery rate algorithm in AFNI, which estimates
60-90% for groups of about N=20.

Two parameters that need to be chosen by the researcher are the p
value, typically ranging from .001 to .01, and the blurring.

The old `3dClustSim` in AFNI uses brute force Monte Carlo simulation to
generate a noise-only dataset, threshold at various per value
p-values, find the largest cluster in the brain mask, repeat these
steps 10000 more times, and then pick the threshold that occurs in
only 5% of the cases.

The problem with `3dClustSim` that contributed to the Eckland paper
findings about the multiple comparison disaster is that there is an
assumption that the ACF is Gaussian. However, it has a long tail.

`3dFWHMX` now estimates a mixed model for the ACF, which is the
recommended approach.

However, the spatial ACF is not the same everywhere in the brain -
particularly it is large in the midline. A lot of this has to do with
respiration signal. This drives up the average.

Another possiblity is to take the residuals from a t-test as an
example of noise at the group analysis to determine the cluster size,
by flipping the signs of the residuals. With two groups you can
permute the groups of the residuals. Then if you rerun the t-test you
can feed those into ClustSim (`3dttest++ -Clustsim`).

Finally, ETAC is an approach that tries multiple thresholds to
accomodate different spatial ACFs. ETAC is not *less* powerful than
using a global threshold, but currently works only with `3dttest++`. [This post describes ETAC.](https://afni.nimh.nih.gov/afni/community/board/read.php?1,155528,155528)

## DTI
Use `TORTOISE` for DTI preprocessing.

OR-logic tracking - find all tracts in whole brain that go through
individual target regions. AND-logic finds tracts that go between
several ROIs.

`3dNetCorr` can be used to compute functional
maps. `FATCAT` (see demo) allows you conduct functional or structural
connectivity analyses.


## Documentation
For all help, the best place to look is in the command line help. This will be the most updated help.

[AFNI Message Board](https://afni.nimh.nih.gov/afni/community/board/list.php)
[AFNI Class Handouts]()

## Nuggets of AFNI Wisdom
Everything is controversial on twitter except cat videos.

*On an example involving* `3dDeconvolve`:
What are the odds that you'd type this and get to the end without messing it up? 

If you start working on new data and you use someone's scripts just because they've been used for 10 years, you're doomed.

You really want the program to guess. That's a great way to do your data analysis. NOT.

You cannot take data and process it in radically different ways. People will hate you. You will hate yourself. You will wake up in the middle of the night thinking, "What did I do?"

*On InstaCorr:*
This is surfing through your data. Whether it's useful or not I leave
to you, but IT IS FUN.
