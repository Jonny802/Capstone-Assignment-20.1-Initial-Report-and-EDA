# Capstone-Assignment-20.1-Initial-Report-and-EDA
Capstone project exploring predictive maintenance across two environments: supervised RUL regression on NASA’s C-MAPSS FD001 turbofan dataset and operational shutdown prediction on real-world hospital equipment telemetry, emphasizing the gap between benchmark data and practical maintenance constraints.

**UC Berkeley Executive Education – Machine Learning and Artificial Intelligence Program**  
**Author:** Jonathan O’Dea  
**Date:** February 2026 

**Overview**

This notebook represents an intermediate stage of the final capstone project and focuses on exploratory data analysis (EDA) and initial findings.

This project combines two datasets, one synthetic and one real-world, to explore the following research question:

How do machine learning techniques for predictive maintenance perform when applied to a benchmark dataset with known failure timelines compared to real-world hospital equipment telemetry where explicit failure labels are unavailable?

The project investigates how predictive maintenance and condition monitoring techniques can be applied across two contrasting data environments:

- The NASA C-MAPSS FD001 dataset, a controlled machine-degradation simulation with known failure outcomes.
- The hospital telemetry dataset, reflecting real operational monitoring without recorded failure events.

By comparing Remaining Useful Life (RUL) modeling in the C-MAPSS FD001 dataset with anomaly detection in the hospital telemetry dataset, the project aims to highlight both the capabilities and limitations of machine learning for maintenance decision-making in critical infrastructure environments.

At this stage of the project, the focus is strictly on exploratory data analysis and feature engineering. Advanced modeling techniques will be introduced in the final module. The goal here is to understand the structure, behavior, and limitations of each dataset before formal predictive modeling is applied.

As this capstone forms part of a machine learning curriculum focused primarily on supervised learning techniques, the analytical direction of the project is intentionally aligned toward regression-based modeling approaches. While many alternative analytical strategies could be applied to these datasets, the emphasis of this work is on understanding how regression models behave across both labeled and unlabeled maintenance contexts.

**Objective**

The primary objective of this exploratory analysis is to identify patterns, relationships, and potential predictive signals within each dataset.

For the NASA C-MAPSS FD001 dataset, the aim is to understand which operational settings and sensor measurements most strongly influence Remaining Useful Life (RUL).

For the hospital telemetry dataset, the objective is to identify anomalous behavior and potential early warning indicators that may suggest degradation or abnormal operating conditions, even in the absence of explicit failure labels.

As the broader goal of the capstone is to explore predictive modeling for the hospital telemetry dataset, using the NASA C-MAPSS FD001 dataset as a structured benchmark, the analytical emphasis is placed on regression-based techniques. All cleaning, feature engineering, and exploratory steps are therefore performed with downstream supervised modeling considerations in mind.

**Dataset**

This project utilizes two primary data sources.

**Dataset A — NASA C-MAPSS Turbofan Engine Degradation Simulation (FD001)**

The C-MAPSS FD001 dataset (`train_FD001.txt`) contains simulated run-to-failure time-series data from 100 turbofan engines operating under a single condition (sea level) and a single fault mode (High-Pressure Compressor (HPC) degradation).

Each engine is recorded over multiple operational cycles and includes:

- Three operational settings
- Twenty-one sensor measurements
- Engine identifier and cycle count

In the training set, engines begin in normal condition and progressively degrade until failure. In the test set, trajectories end before failure, and the objective is to predict Remaining Useful Life (RUL), defined as the number of cycles remaining before failure.

This dataset serves as a controlled benchmark for evaluating degradation behavior and understanding how sensor trends relate to failure progression.

The dataset is publicly available at: https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data

For this stage of the project, the training dataset is used for exploratory analysis.

**Dataset B — Hospital Diagnostic Imaging Equipment Telemetry**

The hospital telemetry dataset (`data_jan_2025_to_jan_2026.csv`) consists of approximately one year of real-world time-series data collected from four high-power medical imaging systems, two of which are associated with cooling units (chillers).

The dataset includes:

Average voltage
Phase currents
Equipment temperatures
Timestamped operational measurements
No explicit failure labels or structured maintenance records are available. Equipment identifiers and site-specific information have been anonymized for confidentiality.

Unlike the NASA C-MAPSS FD001 dataset, which reflects a controlled degradation scenario, the hospital telemetry dataset represents real operational complexity, including commissioning noise, maintenance downtime, environmental disturbances, and infrastructure-level electrical events.

While the C-MAPSS FD001 dataset provides a structured degradation reference, the hospital telemetry dataset reflects the practical constraints organizations face when attempting predictive maintenance without labeled failure data.

Due to the fundamentally different data-generating processes, sampling structures, and objectives of the two datasets, exploratory analysis is conducted separately for each before drawing cross-case comparisons.

**Notebook Structure**

This notebook, `Capstone_Assignment_20.1_Initial_Report_and_EDA_Jonathan_O'Dea.ipynb`, includes the following sections:

1. Business Understanding
2. Data Understanding
3. Initial assumptions
4. Data Preparation
5. Exploratory Data Analysis
   - 5.1. FD001
   - 5.2. Hospital Telemetry
6. Dataset Comparison and Conclusion
7. Findings & Recommendations
8. Minimal Baseline Models
9. Next Steps


**Summary of Findings**

The FD001 benchmark dataset shows clear run-to-failure degradation behaviour, allowing supervised regression for Remaining Useful Life (RUL) using correlated sensor features. In contrast, the hospital telemetry dataset contains real operational variability without labeled failures, with a visible commissioning/stabilization period and intermittent shutdown patterns. No degradation trajectories are observed in the hospital signals; instead, the strongest signals are episodic OFF events and isolated electrical irregularities that appear device- or period-specific.

**Next Steps for Future Modeling**

FD001: build baseline RUL regressors (Linear → Ridge/Lasso → Polynomial → SVR → Tree/Ensemble) and compare with MAE/RMSE.
Hospital telemetry: define a target aligned with available labels (e.g., shutdown prediction in next time window), engineer rolling-window features, and train baseline classifiers (Logistic Regression, Tree/Forest).
Validate whether equipment-specific anomalies are predictive (pre-OFF signatures) versus environmental/system-wide events.
Finalize model comparison narrative: benchmark (FD001) vs constrained real-world telemetry.

**How to Run**

1. The public project repository can be located at: https://github.com/Jonny802/Capstone-Assignment-20.1-Initial-Report-and-EDA
2. Download the project files `Capstone_Assignment_20.1_Initial_Report_and_EDA_Jonathan_O'Dea.ipynb`, `train_FD001.txt` and `data_jan_2025_to_jan_2026.csv` locally
3. Place the datasets inside a local /data folder
4. Run cells top-to-bottom.
