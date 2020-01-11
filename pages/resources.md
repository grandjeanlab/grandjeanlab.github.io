---
layout: misc
title: "Resources"
---
## Table of Contents

1. [Introduction](#introduction)
   1. [Lab vision](#lab-vision)
   2. [Working with animals](#working-with-animals)
2. [Methods](#methods)
   1. [MRI physics](#mri-physics)
   2. [Optogenetics](#optogenetics)
3. [Software](#software)
   1. [Donders HPC](#donders-hpc)
   2. [fMRI software toolkits](#fMRI-software-toolkits)
   3. [Bash](#bash)
   4. [R](#r)
   5. [Plots](#plots)
   6. [Overlays](#overlays)
   7. [Non-parametric statistics](#non-parametric-statistics)
   8. [Independent component analysis](#independent-component-analysis)
4. [Misc](#misc)
   1. [Dataset](#dataset)
   2. [Codes](#codes)
5. [Personal favorites](#personal-favorites)


## Introduction
### Lab vision
Our goals are to produce high-impact and reproducible translational research in the field of neurological and psychiatric disorders. We seek to identify vulnerable neuronal circuits in  animal models, and to test novel therapies. We focus on stress disorders and neurological disorders. We implement several technologies to achieve this goal, including in-vivo imaging, optogenetics, transgenic animal models, and database mining.

We strive to teach and develop the potential of students at all levels, and to enable carrier opportunities in science by teaching data science and statistics, as well as biomedical teachnologies.

We aim to develop an open and reproducible science. Our [datasets](#dataset) and [codes](#codes) are published online. In future studies, we seek to implement preregistration. We put an emphasis on robust and up-to-date [statistical analysis](#non-parametric-statistics) and [data representation](#plots) to highlight significant results.

### Working with animals
Working with experimental animals is a privilege. We motivate our animal research by the need to learn about disease mechanisms and to test novel therapies in a pre-clinical setting before such therapies can be applied to humans.

Neurological and psychiatric disorders are the final frontier in medicine. The toll that [Alzheimer's disease](https://www.who.int/news-room/fact-sheets/detail/dementia) or [depressive disorders](https://www.who.int/news-room/fact-sheets/detail/depression) take on our lives and that of our loved ones in our society is enormous. Yet, despite the price we pay, both emotionally and in term of healthcare, little is know about the disease mechanisms and how to effectively treat disorders of the brain. Animal models for several brain disorders exist. These animals replicate aspects of the diseases they model.

We aim to use translational imaging technologies with a one-on-one equivalence to human, such as Magnetic Resonance Imaging, to bring forward disease mechanisms and highlight biomarkers for disease status and progression.  

To offset animal usage, we pledge to make all of our data available online so that researchers world-wide can re-purpose our work without the need to use additional animals. We also invite researchers to verify our results by re-analysing our data.

We strive systematically to remain up-to-date with animal welfare, and follow strict animal guidelines. We seek to minimize animal suffering through-out our experiments. We use minimally-invasive non-terminal imaging technologies which are also found and applied in human research. Our work is approved by local and national animal welfare bodies.  

## Methods
### MRI physics
MRI physics is not simple. A basic understanding of the mechanisms leading to imaging generation is important. We refer to the following online resources for the students to learn the basics behind MRI physics.

[IMAIOS](https://www.imaios.com/en/e-Courses/e-MRI)  
[MRI questions](https://mriquestions.com/index.html)

### Optogenetics
See [Deisseroth](https://web.stanford.edu/group/dlab/optogenetics/) resource webpage.

Order viral vectors from [addgene](https://www.addgene.org/viral-service/aav-prep/optogenetics/) or from [UNC vector core](https://www.med.unc.edu/genetherapy/vectorcore/)

## Software
### Donders HPC
The Donders institute provides a high performance computer (HPC) for data analysis.

The documentation for the HPC can be found [here](https://dccn-hpc-wiki.readthedocs.io/en/latest/)

The HPC is accessed remotely using a computer console or a Virtual Network Computing (VNC) software.  
How to create a [VNC account](https://dccn-hpc-wiki.readthedocs.io/en/latest/docs/cluster_howto/index.html#accessing-the-cluster)

Projects are stores in the /project/ directory. Our project prefix are 418000.  
How to access a [project](https://dccn-hpc-wiki.readthedocs.io/en/latest/docs/project_storage/access_management.html)

The HPC allows for parallel computation which can dramatically improve the processing speed of large dataset. This is done by submitting 'jobs' to the HPC.    
How to run a [job](https://dccn-hpc-wiki.readthedocs.io/en/latest/docs/cluster_howto/compute_torque.html)

### fMRI software toolkits.
We use the following softwares routinely. All the softwares listed below are available on the HPC.  
fMRIb software library [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki)  
Analysis for Functional NeuroImages [ANFI](https://afni.nimh.nih.gov/)  
Advanced Normalisation ToolS [ANTS](https://github.com/ANTsX/ANTs)

We visualize / export image overlays with [MRIcron](https://www.nitrc.org/projects/mricron)

The following are not available on the HPC, but can be downloaded freely. They are used for advanced 3D rendering and visualization.

[MRIcroGL](https://www.nitrc.org/projects/mricrogl)  
[3dSlicer](https://www.slicer.org/)

### Bash
Most of the functions used to process MRI data are available through the use of a terminal. This is a common system in all UNIX based systems (including MacOS)

[Here](https://linuxconfig.org/bash-scripting-tutorial-for-beginners) is a tutorial for the basic Bash command lines.

### R
After data pre-processing, the remaining of the analysis (statistics, plotting, etc...) is usually performed using R language on Rstudio.

[Here](https://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf) is a tutorial to lean the basics of R.

Python and matlab are alternatives, however we have limited prior experience with python, and matlab is not a freely available software, which limits it applicability

### Plots
The preferred plotting software is through the ggplot2 package for R which uses the [grammar of graphics](https://ggplot2.tidyverse.org/).

```r
install.packages('ggplot2')
```

For improved visualization of effects, we recommend using plots from the estimation statistics [website](https://www.estimationstats.com/#/). The rational for these plots is detailed [here](https://www.nature.com/articles/s41592-019-0470-3)

### Overlays
For overlays, we prefer to use mricron (2D plots) or mricro_gl for 3D rendered images. We favor color codes which are [color-blind friendly](https://www.color-blindness.com/coblis-color-blindness-simulator/).

For 3D render, we have adapted the mosaic script from mricro_gl as follows:

```
//mricro_gl script

const
	kSegments = 7; //number of image
	BG='ABI_template_50umx10';  //the reference template should be in the mricrogl folder
	OVL1='P:\4180000.15\rest_AD\statisticsX10\REHO_restAD\rand_thr_tstat3.nii.gz'; // address to the positive overlay
	OVL2='P:\4180000.15\rest_AD\statisticsX10\REHO_restAD\rand_thr_tstat4.nii.gz'; //address to the negative overlay
	EXP='P:\4180000.15\export_FM\rest\reho_6\img';  //export image
	LTHR=1;  //lower overlay threshold
	UTHR=4;  //upper overlay threshold
var
	i: integer;
	start, thick: single;

begin
	thick := 1/kSegments;

	resetdefaults;
	backcolor(255,255,255)
	colorbarvisible(false);
	//azimuthelevation(180, 15);
	loadimage(BG);
	//clipazimuthelevation(0.5, 0, 180);
	overlayload(OVL1);
	overlayminmax(1, LTHR, UTHR);
	overlaycolorname(1,'NIH_fire');
	overlayload(OVL2);
	overlayminmax(2, LTHR, UTHR);
	overlaycolorname(2,'NIH_ice');
	overlaycolorfromzero(true);
	overlayloadsmooth(true);
	overlaymaskedbybackground(true);
	overlaytransparencyonbackground(30);
	shadername('minimal')
	//savebmp();
	azimuthelevation(150, 5);

	for i := 1 to kSegments do begin
		start := (i-1)*thick;
		clipazimuthelevation(start, 0, 180);
		cutout(0.0, 0.0, 0.0, 1.0, 1.0-start-thick, 1.0);
		savebmp(EXP+inttostr(i));
	end;
end.

```

### Non-parametric statistics
Statistics are at the core of experimental science. The amount of literature on common statistical mistakes is staggering. [Eklund's work](https://www.ncbi.nlm.nih.gov/pubmed/27357684) demonstrated that standard parametric assumptions in fMRI lead to a massive increase in false positive rate. We consequently recommend using [non-parametric alternatives](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/Randomise/UserGuide) whenever applicable.

We also look at other considerations such as [moving beyond the p-value](https://www.ncbi.nlm.nih.gov/pubmed/31217592), [data visualization](https://www.ncbi.nlm.nih.gov/pubmed/22632718) [dual-coded figures](https://github.com/spinicist/nanslice).

### Independent component analysis
Resting-state fMRI analysis is often analyzed with independent component analysis (ICA). Find a guide to how the method works [here](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/MELODIC)

## Misc
### Dataset
We make all of our dataset available freely available online alongside with the relevant publication. We have accumulated over 1000 scans (anatomical, functional, diffusion).

Dataset are available on the [openneuro](https://openneuro.org/dashboard/datasets) platform.

Previous dataset were made available on the [xnat](https://central.xnat.org/) platform.

For people interested in testing scripts or comparing dataset to theirs, we recommend [this dataset](https://openneuro.org/datasets/ds001591) to get started.

### Codes
In addition to making dataset available, we will seek to make codes available with future publications. Repositories for our lab is found [here](https://github.com/grandjeanlab).

## Personal favorites
Here are some of my favorite papers, either because of funny title / concept, or insightful and novel information that transformed how I see things.
#### Papers that made me laugh, and then made me think
[What is the most interesting part of the brain](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5323074/)  
[Monkey in the middle](https://www.frontiersin.org/articles/10.3389/fnana.2012.00029/full) (Only just because of the 90's nostalgia, intentional or not)  
[Improbable research blog and publication](https://www.improbable.com/)

#### Prof. Logothetis on everything.
Logothetis' [answer](https://www.ncbi.nlm.nih.gov/pubmed/21107378) to the original [opto-fMRI nature paper](https://www.ncbi.nlm.nih.gov/pubmed/20473285).  
Logothetis' [answer](https://www.ncbi.nlm.nih.gov/pubmed/19344685) to the electrophysiological basis for [resting-state fMRI in the monkey](Neuronal correlates of spontaneous fluctuations in fMRI signals in monkey visual cortex)

#### Statistical considerations
[Eklund's masterpiece](https://www.ncbi.nlm.nih.gov/pubmed/27357684)  
[Moving beyond the p-value](https://www.ncbi.nlm.nih.gov/pubmed/31217592)
