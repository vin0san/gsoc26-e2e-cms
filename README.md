# GSoC 2026 - Deep Learning Inference for Mass Regression
**Organization:** ML4Sci  
**Project:** E2E Deep Learning - Mass Regression (E2E)  
**Applicant:** Vineet Kumar  
**GitHub:** [vin0san](github.com/vin0san) 
---
## Overview
This project focuses on training a CNN-based regression model to predict particle mass from CMS calorimeter images (125×125, 4 channels) and preparing it for integration into the CMSSW inference pipeline.
The work includes:
- Data reconstruction from parquet format
- Model training and evaluation
- Exploratory data analysis (EDA)
- ONNX export and validation
- CMSSW inference setup attempt
---
## Repository Structure
- `task2f/` — Mass regression model training and evaluation
- `task2g/` — CMSSW inference setup and logs
- `proposal.pdf` — Final GSoC proposal
---

## Task 2f — Results

| Attempt | Dataset | Normalization | RMSE | Rel Error |
|--------|--------|--------------|------|----------|
| 1 | 1K events | None | 114 GeV | 43% |
| 2 (Best) | 150K events | None | 91 GeV | 30.69% |
| 3 | 600K events | Clip + Norm | 112 GeV | 40.51% |

**Cross-file generalization (Attempt 2 → File 3):**  
RMSE: 114.85 GeV | Rel Error: 32.52%

---

## Key Observations

- Strong scale imbalance across channels (Track pT dominates)
- Spatial image structure carries most predictive signal
- Outliers significantly affect training stability
- Learning rate scheduler instability observed in long training runs

---

## Task 2g — CMSSW Inference

- Set up Docker + CMSSW environment  
- Built RecoE2E successfully  
- Exported model to ONNX and verified inference  
- Ran `cmsrun` with inference configuration  

**Status:**  
Pipeline initialized successfully, but execution failed due to ROOT file version incompatibility (CMSSW_12 → CMSSW_11).

---

## Notebooks

- [Main Training Notebook](https://www.kaggle.com/code/vineet0san/e2e-deep-learning-mass-regression)  
- [EDA Notebook](https://www.kaggle.com/code/vineet0san/eda-for-e2e)  

---

## Notes

Due to hardware constraints, training was performed on subsets of the dataset. The focus was on correctness of pipeline, understanding of data, and reproducibility rather than exhaustive optimization.