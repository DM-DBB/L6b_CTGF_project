# L6b-CTGF Project Analysis Repository 

This repository contains the pipeline for processing, analyzing, and visualizing experimental data from the L6b-CTGF study from Christian Broberger´s Laboratory. The codebase supports and documents the computational analyses reported in the associated manuscript.

## Overview

The repository provides analytical workflows spanning multiple experimental modalities: calcium imaging for functional characterization, kinematic analyses for behavioral correlation, anatomical quantification for spatial mapping, and electrophysiological burst detection. Each analysis domain is implemented as standalone notebook or MATLAB project, enabling modular execution and reproducibility.

## Repository Structure
````
.
│   # Anatomy analyses
│   Anatomy_for density plot of TdT cortical counts.ipynb                # Quantify TdT+ cell distribution across cortical regions
│   Optogenetic patched cell_Plot cell locations.ipynb                   # Map locations of patched cells
│
│   # Calcium imaging analyses (Python notebooks)
│   Calcium Imaging_reporting dynamic range across sessions (1).ipynb                                       # Session-to-session signal variability
│   Calcium Imaging_plot S1 first 10min heatmap (2).ipynb                                                   # Visualize initial recording period activity
│   Calcium Imaging_for analysis of neuronal activity episodes and cofluctuating pairs (3).ipynb            # Co-activity patterns
│   Calcium Imaging_ for classification of response types (4).ipynb                                         # Categorize neuronal response profiles
│   Calcium Imaging_for analysis of response type stability (5).ipynb                                       # Track response consistency over time
│
│   # Locomotion/kinematic analyses
│   Kinematics_Processing mobility data from IMU (1).ipynb                     # Extract movement features from IMU sensors
│   Kinematics_Plot locomotor transition body acceleration data (2).ipynb      # Visualize acceleration during state transitions
│   Kinematics_Link and plot neuron activity and locomotor state (3).ipynb     # Correlate neural activity with movement
│
│   README.md                                                                  # Readme file for the whole project (This file)
│
├───Calcium Imaging_Autocorrelation analysis          # MATLAB: Temporal autocorrelation of Ca2+ signals
│   │   Autocorrelation_Calcium2.prj                  # MATLAB project file
│   │   README.md                                     # Submodule specific readme file
│   │
│   ├───Functions                                     # Helper functions for autocorrelation computation
│   │       autocorrelogram_freq_fft.m                # FFT-based frequency analysis
│   │       blockbootstrp.m                           # Block bootstrap resampling
│   │       data_extraction.m                         # Load and parse input data
│   │       mp_autocorrelogram.m                      # Multi-process autocorrelogram computation
│   │       polyfit_detrending.m                      # Remove polynomial trends
│   │       select_neurons.m                          # Filter neurons by criteria
│   │       shiftlinearcorr.m                         # Shifted correlation analysis
│   │       time_selection.m                          # Extract time windows
│   │
│   ├───Main
│   │       Main_Autocorrelogram_script_standard_wrapped.m  # Primary execution script
│   │
│   └───resources                                     # MATLAB project metadata (auto-generated)
│       └───project
│
└───Electrophysiology_Burst analysis                  # MATLAB: Burst detection in ephys recordings
    │   Projects.prj                                  # MATLAB project file
    │   README.md                                     # Submodule specific readme file
    │
    ├───Functions                                     # Burst analysis utilities
    │       burstfinder.m                             # Detect burst events
    │       thresholding_andrea.m                     # Apply detection thresholds
    │       trainanalyzer.m                           # Analyze spike trains
    │
    ├───Main
    │       Train_analysis.m                          # Primary burst analysis script
    │
    └───resources                                     # MATLAB project metadata (auto-generated)
        └───project
````


## Analysis Modules

### 1 - Calcium Imaging

A sequential pipeline for analyzing miniscope calcium imaging data, designed to be executed in numerical order:

#### Python Notebooks

1. `Calcium Imaging_reporting dynamic range across sessions (1).ipynb` 
    * Quantifies within session variability in calcium signal amplitude and reports dynamic range metrics

2.  `Calcium Imaging_plot S1 first 10min heatmap (2).ipynb`
    * Generates heatmap visualizations of neural activity during the initial 10-minute recording period in S1 cortex

3.  `Calcium Imaging_for analysis of neuronal activity episodes and cofluctuating pairs (3).ipynb`
    * Identifies pairwise coactivity and analyzes temporal patterns of synchronized activity episodes

4.  `Calcium Imaging_ for classification of response types (4).ipynb`
    * Categorizes neurons into distinct functional classes based on their stimulus-evoked response profiles

5.  `Calcium Imaging_for analysis of response type stability (5).ipynb`
    * Assesses the stability of neuronal response type classifications across behavioral sessions

#### MATLAB Submodule: `Calcium Imaging_Autocorrelation analysis/`

Complementary stand-alone MATLAB implementation for temporal autocorrelation analysis of calcium signals with simple block bootstrap statistical validation. For a detailed explanation see: `Calcium Imaging_Autocorrelation analysis/README.md`


### 2 - Kinematics / locomotion

Inertial measurement unit (IMU) data processing and neural-behavioral correlation pipeline, executed sequentially:

#### Python Notebooks

1. `Kinematics_Processing mobility data from IMU (1).ipynb`
    * Extracts kinematic features from raw IMU sensor data
2.  `Kinematics_Plot locomotor transition body acceleration data (2).ipynb`
    * Visualizes acceleration profiles during locomotor state transitions
3.  `Kinematics_Link and plot neuron activity and locomotor state (3).ipynb`
    * Aligns Calcium imaging signals to classified locomotor transitions

### 3 - Anatomy / cell mapping
Spatial distribution analysis of neuron location

#### Python Notebooks
* `Anatomy_for density plot of TdT cortical counts.ipynb`
    * Quantifies the regional distribution of TdT+ cells across cortical areas and generates density heatmaps
* `Optogenetic patched cell_Plot cell locations.ipynb`
    * Maps the 3D coordinates of patch-clamped cells for anatomical registration

#### External tools referenced: 

* Whole-brain mapping: See ABBA paper — Chiaruttini, N.; Castoldi, C.; Requie L. et al. "ABBA+BraiAn, an integrated suite for whole-brain mapping, reveals brain-wide differences in immediate-early genes induction upon learning," Cell Reports (2025). https://doi.org/10.1016/j.celrep.2025.115876

* Cell/fiber segmentation: See QuPath paper — Bankhead, P. et al. "QuPath: Open source software for digital pathology image analysis," Scientific Reports (2017). https://doi.org/10.1038/s41598-017-17204-5

### 4 - Electrophysiology

#### MATLAB submodule: `Electrophysiology_Burst analysis/`

Automated stand-alone detection and characterization of multispike firing patterns in electrophysiological recordings. For a detailed explanation see: `Electrophysiology_Burst analysis/README.md`

## Requirements

### Python Environment
- Python 3.9 or later
- Jupyter Notebook or JupyterLab
- Core scientific Python stack ( `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy`, `scikit-image`)

> Note: each notebook may require additional project-specific input files and package versions. 

## MATLAB Project
- MATLAB 2023a or later
- Signal Processing Toolbox
- Statistics and Machine Learning Toolbox

## How to use

### Jupyter Notebooks

1. Clone the repository.
2. Launch Jupyter Notebook or JupyterLab in the project directory.
3. Open the notebook that corresponds to your analysis goal.
4. Update file paths and parameters in the notebook cells to match your local data layout.
5. Run cells sequentially.

### MATLAB projects

1. Clone the repository or download the relevant submodule folder (`Calcium Imaging_Autocorrelation analysis/` or `Electrophysiology_Burst analysis/`).
2. Open MATLAB (2023a or later) and navigate to the submodule directory.
3. Double-click the .prj file to open the MATLAB project. This will automatically set up the correct paths.
4. Open the main script located in the `Main/` subfolder.
5. Update the analysis parameters at the top of the script to match your local data layout.
6. Run the script section by section or in full.
7. Refer to the submodule-specific `README.md` for detailed parameter descriptions and expected input/output formats.

### Suggested workflow

For analyses that include numbered notebook filenames, run them in ascending numeric order (for example, `(1)` to `(5)`) to follow the original pipeline stages as reported in the manuscript. Scripts that do not contain numbers were used as standalone.

The MATLAB submodules (`Calcium Imaging_Autocorrelation analysis/` and `Electrophysiology_Burst analysis/`) are standalone projects and can be run independently of the Python notebooks and of each other. Refer to their respective `README.md` files for guidance on execution order and required inputs.

## Citation and attribution

### Original code authors:

* Debora Masini - Python/Jupyter Notebook analyses (calcium imaging, kinematics, anatomy)
* Andrea Locarno - MATLAB projects (calcium imaging autocorrelation, electrophysiology burst detection)

### Cite as 

* Debora Masini and Andrea Locarno (2026): https://github.com/DM-DBB/Scripts-for-article_first-submission_V23_02_2026.git.

* Please cite also the associated manuscript/article: Khalid, R., Masini, D., Locarno, A. et al. <!-- Title--> <!-- Journal--> <!-- DOI-->

## Contact

For questions regarding the codebase, please contact:
* Debora Masini — debora.masini@dbb.su.se
* Andrea Locarno — andrea.locarno@dbb.su.se 

