# Elementary Cell Quality Assurance Analysis
<div align = "justify">
During my Ph.D. studies I had a chance to work on the Ring-Imaging Chrenkov (RICH) detector upgrade for the LHCb experiment at CERN. The analysis scripts used for my Ph.D. thesis were written in the Python/C++ using CERN ROOT library for the data visualization. I decided to take some part of the analysis, rewrite to be pure python code using NumPy and Pandas and the most common data visualization libraries such as: Matplotlib and Seaborn, make it Jupyter-Notebook friendly and upload it here.

## Contents
- [Signal Induced Noise Analysis](https://github.com/islazykv/data-science/blob/main/data-analysis/physics/SIN-analysis.ipynb)
- [Digital-to-Analog Converter Scan Analysis](https://github.com/islazykv/data-science/blob/main/data-analysis/physics/DAC-analysis.ipynb)
- [Dark Count Rate Analysis](https://github.com/islazykv/data-science/blob/main/data-analysis/physics/DCR-analysis.ipynb)
- [Threshold Scan Analysis](https://github.com/islazykv/data-science/blob/main/data-analysis/physics/THR-analysis.ipynb)

The main objective was to perform four analyses (as presented above) to characterize so-called Elementary Cell (picture below) - the new detection unit of the RICH detectors implemented in the latestest upgrade. An Elementary Cell is a combination of Multi-Anode Photomultiplier Tubes (MaPMTs) and front-end electronics (such as: Base-Board, Back-Board and Front-End Boards). There are two types of the Elementary Cell: R-type (left side of the picture) and H-Type (right side of the picture). R-type is used in the central regions of the RICH detectors (where the occupancy is the highest) while the H-type is used at the borders of the RICH2 detector. If you are interested in this matter, I invite you to read my Ph.D. thesis. The analysis scripts were implemented in the final automated software for the Elementary Cell quality assurance, where upon completion of a particular measurement, an analysis was performed. For every analysis, the workflow is as follows: get a specific .txt measurement file, extract essential mapping and measurement data, calculate parameters of interest, visualize it and save everything as PDF files. For the sake of the Jupyter Notebook environment, I made only the first plot visible (as there are thousands of plots generated), the rest plots can be seen in 'output' folder.

<img width=50% text-align = "center" src="materials\ECs_Picture.jpg"/>

</div>
