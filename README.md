# AST402 Mid-Term Project  
## Stellar Hβ Line Analysis and Stellar Parameter Determination

## Overview

This project performs a complete analysis of an observed stellar spectrum around the Hβ absorption line (4861.33 Å). The workflow includes:

1. Observed spectrum acquisition and preparation
2. Radial velocity correction
3. Continuum normalization
4. Hβ line profile extraction
5. Sérsic profile fitting
6. PHOENIX stellar atmosphere model grid preparation
7. Synthetic Hβ profile comparison
8. χ²-based stellar parameter determination
9. Uncertainty estimation
10. Physical interpretation and critical discussion

The analysis was performed using Python, Astropy, NumPy, SciPy, Pandas, and Matplotlib.

---

# Project Structure

```
AST402_MidTerm_Project/

│
├── notebooks/
│   │
│   ├── 01.setup-environment.ipynb
│   ├── 02.observed-spectrum-acquisition.ipynb
│   ├── 04.Hβ_line_profile_fitting.ipynb
│   ├── 04.phoenix-grid-final.ipynb
│   ├── 05.stellar-parameter-determination.ipynb
│   └── 06.physical-interpretation-discussion.ipynb
│
│
├── data/
│   │
│   └── PHOENIX/
│       │
│       ├── raw/
│       │       Original downloaded PHOENIX spectra
│       │
│       ├── processed/
│       │       Processed/interpolated spectra
│       │
│       ├── final_grid/
│       │       Final PHOENIX model grid used for fitting
│       │
│       ├── interpolated/
│       │       Wavelength-matched synthetic spectra
│       │
│       ├── representative_subset/
│       │       Five PHOENIX spectra nearest the best-fit solution
│       │
│       └── hbeta_sersic_results.csv
│               Sérsic fitting results for synthetic Hβ profiles
│
│
├── plots/
│       Generated figures from the analysis
│
│
├── scripts/
│       Helper scripts for downloading and processing data
│
│
├── requirements.txt
│       Python package dependencies
│
└── README.md
```

---

# Software Requirements

Python version:

```
Python 3.x
```

Required packages:

- numpy
- scipy
- pandas
- matplotlib
- astropy
- tqdm

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Execution Order

The notebooks should be executed in the following order.

---

## 1. Environment Setup

Notebook:

```
01.setup-environment.ipynb
```

Purpose:

- Install required packages
- Verify Python environment
- Configure project directories

---

## 2. Observed Spectrum Acquisition

Notebook:

```
02.observed-spectrum-acquisition.ipynb
```

Purpose:

- Download observed stellar spectrum
- Read FITS data
- Extract wavelength and flux arrays
- Inspect spectral coverage
- Identify Hβ region

Output:

Prepared observed spectrum for further analysis.

---

## 3. Hβ Line Profile Preparation and Sérsic Fitting

Notebook:

```
04.Hβ_line_profile_fitting.ipynb
```

Purpose:

- Apply radial velocity correction
- Extract Hβ region (4820–4900 Å)
- Perform continuum normalization
- Estimate uncertainty array
- Fit Sérsic line profile
- Calculate equivalent width
- Analyze residuals and reduced χ²

Output:

- Best-fit Sérsic parameters
- Hβ equivalent width
- Observed line profile plots

---

## 4. PHOENIX Grid Preparation

Notebook:

```
04.phoenix-grid-final.ipynb
```

Purpose:

- Download PHOENIX-ACES model spectra
- Construct stellar atmosphere grid
- Load wavelength array
- Convolve models to observed resolution
- Normalize synthetic spectra

PHOENIX grid parameters:

```
Teff:
5000 K – 7000 K
step = 500 K

log(g):
3.5 – 5.0 dex
step = 0.5 dex

[Fe/H]:
-0.5 – +0.5 dex
step = 0.5 dex
```

Total grid size:

```
5 × 4 × 3 = 60 spectra
```

---

## 5. Stellar Parameter Determination

Notebook:

```
05.stellar-parameter-determination.ipynb
```

Purpose:

- Fit synthetic Hβ profiles
- Compute χ² between observed and PHOENIX spectra
- Determine best-fit:

```
Teff
log(g)
[Fe/H]
```

- Perform χ² interpolation
- Estimate uncertainties
- Compare with literature values

Output:

Final stellar atmospheric parameters.

---

## 6. Physical Interpretation and Discussion

Notebook:

```
06.physical-interpretation-discussion.ipynb
```

Purpose:

- Estimate stellar radius
- Estimate luminosity
- Place star on H–R diagram
- Discuss:

  - LTE assumptions
  - Alternative temperature diagnostics
  - Limitations of Sérsic fitting

Output:

Physical interpretation figures and discussion material.

---

# PHOENIX Data

The PHOENIX-ACES model atmosphere spectra were obtained from:

```
https://phoenix.astro.physik.uni-goettingen.de/
```

The final fitting grid contains spectra covering:

```
Teff = 5000–7000 K
logg = 3.5–5.0 dex
[Fe/H] = -0.5–+0.5 dex
```

A representative subset of five spectra nearest to the best-fit solution is stored in:

```
data/PHOENIX/representative_subset/
```

These files allow reproduction of the final comparison without downloading the complete grid.

---

# Reproducibility

To reproduce the analysis:

1. Clone the repository:

```bash
git clone https://github.com/fardinabdullah/AST402_MidTerm_Project.git
```

2. Create the Python environment:

```bash
python -m venv .venv
```

3. Activate environment:

Windows:

```bash
.venv\Scripts\activate
```

Linux/macOS:

```bash
source .venv/bin/activate
```

4. Install dependencies:

```bash
pip install -r requirements.txt
```

5. Execute notebooks sequentially:

```
01 → 02 → 04(Hβ) → 04(PHOENIX) → 05 → 06
```

---

# Final Results Summary

The analysis determines stellar atmospheric parameters from Hβ line fitting using PHOENIX stellar atmosphere models and χ² minimisation.

Measured quantities include:

- Effective temperature (Teff)
- Surface gravity (log g)
- Metallicity ([Fe/H])
- Stellar radius
- Stellar luminosity
- Hβ equivalent width

The final interpretation compares the derived stellar properties with theoretical expectations and literature values.

---

# Academic Integrity

All analysis code, figures, and written explanations were prepared specifically for this project.

External resources used include:

- PHOENIX-ACES stellar atmosphere models
- SIMBAD astronomical database
- Astropy documentation

