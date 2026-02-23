# Scripts for Article (First Submission, v23_02_2026)

This repository contains scripts used to process, analyze, and visualize datasets for an article submission focused on L6b-CTGF experiments.

## Repository contents

The project is organized as standalone notebooks grouped by analysis domain:

### Calcium imaging
- `Calcium Imaging_reporting dynamic range across sessions (1).ipynb`
- `Calcium Imaging_plot S1 first 10min heatmap (2).ipynb`
- `Calcium Imaging_for analysis of neuronal activity episodes and cofluctuating pairs (3).ipynb`
- `Calcium Imaging_ for classification of response types (4).ipynb`
- `Calcium Imaging_for analysis of response type stability (5).ipynb`

### Kinematics / locomotion
- `Kinematics_Processing mobility data from IMU (1).ipynb`
- `Kinematics_Plot locomotor transition body acceleration data (2).ipynb`
- `Kinematics_Link and plot neuron activity and locomotor state (3).ipynb`

### Anatomy / cell mapping
- `Anatomy_for density plot of TdT cortical counts.ipynb`
- `Optogenetic patched cell_Plot cell locations.ipynb`
- All else related to full brain mapping refer to ABBA paper: Chiaruttini, N.; Castoldi, C.; Requie L. et al. ABBA+BraiAn, an integrated suite for whole-brain mapping, reveals brain-wide differences in immediate-early genes induction upon learning, Cell Reports (2025). https://doi.org/10.1016/j.celrep.2025.115876
- All else related to segmentation of cells, fibers or synaptic puncta (see manuscript methods) refer to QuPath paper: Bankhead, P. et al. QuPath: Open source software for digital pathology image analysis. Scientific Reports (2017). https://doi.org/10.1038/s41598-017-17204-5 

## Requirements

- Python 3.x
- Jupyter Notebook or JupyterLab
- Standard scientific Python stack (commonly: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy`)

> Note: each notebook may require additional project-specific input files and package versions depending on the original analysis environment. When present the version used is stated within the files.

## How to use

1. Clone the repository.
2. Launch Jupyter Notebook or JupyterLab in the project directory.
3. Open the notebook that corresponds to your analysis goal.
4. Update file paths and parameters in the notebook cells to match your local data layout.
5. Run cells sequentially.

## Suggested workflow

For analyses that include numbered notebook filenames, run them in ascending numeric order (for example, `(1)` to `(5)`) to follow the original pipeline stages as reported in the manuscript. Scripts that do not contain numbers were used as stand alone.

## Reproducibility notes

- Keep raw data outside version control unless approved for sharing.
- Record package versions (for example with `pip freeze > requirements.txt`) when reproducing results.

## Citation and attribution

If you reuse these notebooks in publications or derivative analyses, please cite the associated article/manuscript and acknowledge the original analysis author(s).
