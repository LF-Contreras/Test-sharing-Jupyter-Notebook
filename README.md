# BayCal_NS-5 v0 and BayCal_NS-7 v0<br>Bayesian Calibration of NorSand Model - 5 and 7 parameter versions

# Notes on BayCal_NS-5 and BayCal_NS-7
These Jupiter Notebooks includes the Python code used to run the 5-parameter and 7-parameter model examples presented in the paper:
- Contreras, L.F., Rojas-Huaroto, H., Halliday, A. and Llano-Serna, M. (2025). Bayesian calibration of NorSand Model parameters using triaxial test data, *Australian Geomechanics*, Special Edition, September 2025.  

## LEGAL
This software is written in Python code and is © 2025 Luis-Fernando Contreras, Humberto Rojas-Huaroto, Alexandra Haliday & Marcelo Llano-Serna.

Although copyrighted, it is offered as free software ("freeware"); you can redistrubute it and/or modfy it under the terms of the GNU General Public Licenese Version 2 as published by the Free Software Foundation.  This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.
## Purpose
The code is structured into two main parts: **NorSand model implementation** (cells [1] to [10]) and **parameter calibration** (cells [11] to [25]).

The **first part** focuses on simulating a set of drained and undrained triaxial tests and comparing the model’s predictions with actual laboratory testing results.

The **second part** performs Bayesian calibration of five or seven NorSand parameters (depending on the model version) to minimise the difference between model predictions and observed data. The parameters inferred include the elasticity parameters (Gref, m, ν) and the plastic hardening parameters (H0, Hy) for the five-parameter model version, and additionally the two plasticity parameters (N, χtc) for the seven-parameter model version.
## Architecture
To run the code, a **Jupyter Notebook** installation with **Python 3.8** is required, along with the necessary Python packages. The required packages are specified in cells [1] and [11] for Parts 1 and 2, respectively.

The **first part** of the code simulates a set of triaxial tests using predefined NorSand parameter values, including the five parameters targeted for inference. The input NorSand parameters are specified in cell [3], while the actual triaxial test results used for comparison are provided in a CSV file read in cell [5]. This file must be stored in the same directory as the notebook, and the test data should be sorted alphabetically, following the format of ‘tx_data_FRS_12tests.csv’, which contains Fraser River Sand data for the example case. The model’s predictions are then compared against test data through the graphs generated in cell [10].

The **second part** of the code calibrates the targeted NorSand parameters for inference (Gref, m, ν, H0, Hy) or (Gref, m, ν, H0, Hy, N, χtc) by minimising the difference between model predictions and observed data. The valid parameter ranges (priors) and standard deviation bounds for the errors are defined in cell [13], while the input parameters for the Markov Chain Monte Carlo (MCMC) sampling process are specified in cell [15]. A progress bar is displayed during the MCMC analysis (cell [16]), and upon completion, the acceptance rate and processing time are reported. The sampling chains and corner plots of the inferred parameters are displayed in cell [17], followed by tabulated results in cell [19]. Graphs comparing the calibrated model predictions with test data for all the tests are generated in cell [20], while uncertainty bands for H vs. ψ0 and G vs. p’0 are shown in cell [22]. Finally, summary graphs of the calibrated model predictions and experimental data are produced in cells [23] and [24].

The Jupyter Notebooks provide a general description of each part of the code, with extensive comments explaining the content of individual cells. The complete set of results from the calibration examples discussed in the paper is also included. The programming approach prioritizes methodological clarity over computational efficiency. Some elements of the plots, such as axis scales and color palettes, are tailored to the 12-test example dataset and may require adjustments when using different datasets.
