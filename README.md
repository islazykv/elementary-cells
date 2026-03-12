# Elementary Cell Quality Assurance Analysis
<div align = "justify">

During my Ph.D. studies I had a chance to work on the Ring-Imaging Cherenkov (RICH) detector upgrade for the LHCb experiment at CERN. The analysis scripts used for my Ph.D. thesis were written in Python/C++ using the CERN ROOT library for data visualisation. I decided to take part of the analysis and rewrite it in pure Python. For data processing I used NumPy and Pandas, and for data visualisation I used Matplotlib and Seaborn. The Jupyter Notebook was used as the environment. Unfortunately, mathematical expressions are not rendered on GitHub — please download the files and run them locally for properly rendered equations.

## Elementary Cell QA Analyses

The main objective was to perform four analyses (listed below) to characterise the so-called Elementary Cell — the new photon detection unit of the RICH detectors implemented in the latest upgrade. An Elementary Cell is a combination of Multi-Anode Photomultiplier Tubes (MaPMTs) and front-end electronics (Base-Board, Back-Board and Front-End Boards). There are two types of Elementary Cell: R-type (left side of the picture below) used in the central regions of the RICH detectors where the occupancy is the highest, and H-type (right side) used at the borders of the RICH2 detector. If you are interested in this topic, I invite you to read my Ph.D. thesis ([link](https://islazykv.github.io/islazykv/pdfs/Ph.D.-Particle-Physics.pdf)).

The analysis scripts were implemented in the final automated software for Elementary Cell quality assurance, where upon completion of a particular measurement an analysis was performed automatically. For every analysis, the workflow is: read a specific `.txt` measurement file, extract the mapping and measurement data, calculate the parameters of interest, visualise them and save everything as PDF files. For the sake of the Jupyter Notebook environment only the first plot is shown inline; the remaining plots are saved in the `output` folder.

<div align="center"><img height="300px" style="margin-right:50px" src="materials\EC_Side_View.png"/><img height="300px" src="materials\ECs_Picture.jpg"/></div>

### Contents

- **[Signal Induced Noise Analysis](SIN-analysis.ipynb)**
  Quantifies after-pulse contamination for each MaPMT pixel by computing the SIN fraction and Signal-to-Noise (S/N) ratio from per-channel SIN spectra. The analysis also identifies three spatially distinct SIN-intensity regions on R-type ECs and reports min/max/mean values within each region. Outputs include 2D heatmaps (per MaPMT), 1D histograms and individual per-channel SIN distribution spectra.

- **[Digital-to-Analog Converter Scan Analysis](DAC-analysis.ipynb)**
  Calibrates the front-end discriminator channels by fitting DAC scan data with a translated error function (S-curve). The fit extracts two key parameters for every channel: the transition point *x_t* (threshold equivalent input charge) and the noise *σ*. Outputs include S-curve plots with fitted overlays and 1D histograms of the transition and noise distributions.

- **[Dark Count Rate Analysis](DCR-analysis.ipynb)**
  Measures the rate of thermally induced dark events (i.e. events not caused by photons) for each MaPMT pixel from a 100-second dark measurement, expressed in Hz. Outputs include 2D heatmaps showing the spatial distribution of dark counts across the MaPMT face and 1D histograms to assess overall uniformity and identify noisy pixels.

- **[Threshold Scan Analysis](THR-analysis.ipynb)**
  Determines the optimal working point *W_P* for each MaPMT channel from the above-threshold event count distribution as a function of the discriminator threshold step (0–63). The working point is set five steps above the noise edge to ensure clean signal–noise separation. Outputs include 2D heatmaps of working points, 1D histograms and per-channel threshold distribution spectra.

---

## LHCb Particle Identification

- **[LHCb Particle Identification](LHCb-particle-identification.ipynb)**
  Although not directly related to the Elementary Cell QA work above, this notebook is included here because it is set within the broader LHCb experiment context. The goal is to classify particles (electrons, muons, kaons, pions, protons and ghost tracks) recorded by the LHCb detector using a Monte Carlo dataset of 60 000 tracks described by 50 features from all sub-detector systems (tracking, RICH, calorimeters and muon chambers). Two logistic regression classifiers are trained and compared: an initial baseline and an improved model that handles RICH exit codes (−999 artefacts) via a custom `FeatureExpansion` transformer, yielding approximately 1% accuracy improvement. Quality metrics are visualised as signal efficiency vs. momentum curves per particle species.

</div>
