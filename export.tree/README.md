Description

Here we share the main data reported in the following paper: 7T 3D-EPI PCASL with High SNR Efficiency and Robustness to Through-Plane B0 Field Gradients. Gael Saib, Alan P. Koretsky and S. Lalith Talagala. Magnetic Resonance in Medicine (2026): https://doi.org/10.1002/mrm.70491. Below we provide a brief description of the data. A detailed description of the data can be found in the paper cited above. If you have any questions about the data, please reach out to Gael Saib at saibgh@nih.gov.

This dataset contains 7 Tesla human brain MRI data from 21 subjects acquired as part of two PCASL optimization studies. Subjects sub-01 to sub-09 correspond to the labeling-duration experiment, whereas subjects sub-10 to sub-21 correspond to the mean-gradient experiment. The dataset includes MP2RAGE anatomical images, 3D-EPI PCASL acquisitions, and associated processed datasets.

------------------------------------------------Labeling Duration experiment--------------------------------------------

Dataset Organization

sub-XX/
	anat/
		sub-XX_UNIT1.nii
	perf/
		sub-XX_acq-LD500_asl.nii
		sub-XX_acq-LD1000_asl.nii
		sub-XX_acq-LD1500_asl.nii
		sub-XX_acq-LD2000_asl.nii
		sub-XX_acq-LD2500_asl.nii
		sub-XX_acq-LD3000_asl.nii
		sub-XX_acq-LD3500_asl.nii
		sub-XX_acq-LD4000_asl.nii
	derivatives/
		perfusion/
		segmentation/

Each subject folder is organized as follows:

Anatomical Data

anat/

sub-XX_UNIT1.nii

Brain-extracted MP2RAGE UNI image used as the anatomical reference for registration and tissue segmentation.

Perfusion Data

perf/

Contains the PCASL acquisitions acquired with different labeling durations.
Files follow the naming convention:

sub-XX_acq-LDXXXX_asl.nii

where LDXXXX indicates the labeling duration in milliseconds.

Acquisition label -> Labeling duration (s)
LD500 -> 0.5
LD1000 -> 1.0
LD1500 -> 1.5
LD2000 -> 2.0
LD2500 -> 2.5
LD3000 -> 3.0
LD3500 -> 3.5
LD4000 -> 4.0

Each ASL file contains one M0 image followed by alternating control and label images.

Derivatives

derivatives/perfusion/

Contains mean control-label difference image normalized by M0 derived from the corresponding ASL acquisition.
Files follow the naming convention:

sub-XX_acq-LDXXXX_ndiff.nii

These images were used for perfusion quantification and analysis.

derivatives/segmentation/

Contains tissue segmentation maps registered to perfusion image space.
Files follow the naming convention:

sub-XX_acq-LDXXXX_FAST_seg_in_perf.nii.gz

These segmentation maps were generated using FSL FAST and transformed into the corresponding perfusion image space. They provide gray matter, white matter, and cerebrospinal fluid tissue classifications for quantitative analysis.


------------------------------------------------Mean Gradient experiment--------------------------------------------

Dataset Organization

sub-XX/
	anat/
		sub-XX_UNIT1.nii
	perf/
		sub-XX_acq-Gm08_asl.nii
		sub-XX_acq-Gm06_asl.nii
		sub-XX_acq-Gm04_asl.nii
		sub-XX_acq-Gm02_asl.nii
		sub-XX_acq-G0_asl.nii
		sub-XX_acq-Gp02_asl.nii
		sub-XX_acq-Gp04_asl.nii
		sub-XX_acq-Gp06_asl.nii
		sub-XX_acq-Gp08_asl.nii
	derivatives/
		atlas/
		fmap/
		perfusion/
		segmentation/

Each subject folder is organized as follows:

Anatomical Data

anat/

sub-XX_UNIT1.nii

Brain-extracted MP2RAGE UNI image used for tissue segmentation, image registration, and anatomical reference.

Perfusion Data

perf/

Contains the PCASL perfusion images acquired under nine different mean through-plane gradient conditions.

sub-XX_acq-GYY_asl.nii

where GYY denotes the applied mean gradient condition:

Acquisition label -> Mean gradient (mT/m)
Gm08 -> −0.8
Gm06 -> −0.6
Gm04 -> −0.4
Gm02 -> −0.2
G0 -> 0.0
Gp02 -> +0.2
Gp04 -> +0.4
Gp06 -> +0.6
Gp08 -> +0.8

Each ASL file contains one M0 image followed by alternating control and label images.

Derivatives

derivatives/fmap/

Contains whole-brain B0 and flip-angle maps together with vessel masks extracted from TOF angiography.

sub-XX_B0map.mat: Whole-brain B0 field map.
sub-XX_FAmap.mat: Whole-brain flip-angle map.
sub-XX_VesselMasks.mat: Feeding artery masks extracted from TOF angiography.
sub-XX_MaskedB0_Vessels.mat: B0 values sampled within the vessel masks.
sub-XX_MaskedFA_Vessels.mat: Flip-angle values sampled within the vessel masks.

These data were used to characterize magnetic field and transmit field conditions along the feeding arteries supplying the labeling plane.

derivatives/atlas/

Contains atlas arterial labels registered to the corresponding perfusion image space.
Files follow the naming convention:

sub-XX_acq-GYY_atlas_in_perf.nii.gz

derivatives/segmentation/

Contains tissue segmentation maps generated using FSL FAST and registered to perfusion space.
Files follow the naming convention:

sub-XX_acq-GYY_FAST_seg_in_perf.nii.gz

These files provide gray matter, white matter, and cerebrospinal fluid tissue classifications aligned with the perfusion images.

derivatives/perfusion/

Contains mean control-label difference image normalized by M0 derived from the PCASL acquisitions.
Files follow the naming convention:

sub-XX_acq-GYY_ndiff.nii

These images were used for quantitative perfusion analysis and estimation of perfusion-related metrics.
