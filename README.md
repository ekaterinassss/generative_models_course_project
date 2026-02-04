# Generative Models for Financial Time Series

## Project Overview

This project investigates the stability and performance of generative models for synthesizing financial time series data using cryptocurrency market data.

The goal is to evaluate whether modern generative models can reproduce the statistical properties of real financial returns and generate realistic synthetic data for downstream ML applications.

## Dataset

The dataset consists of historical cryptocurrency market data:

- Assets: BTC, ETH, BNB
- Time period: last 730 days
- Frequency: hourly data

### Preprocessing steps:
- Computation of log-returns
- Normalization of time series
- Data cleaning and outlier handling
- Creation of fixed-length training windows (length = 64)



## Exploratory Data Analysis

The following properties of financial time series were studied:

- Price dynamics
- Distribution of log-returns
- Fat tails (high kurtosis)
- Volatility clustering
- Correlation between assets
- Skewness and asymmetry
- Leverage effect

These stylized facts serve as evaluation criteria for generated data quality.


## Models Implemented

### 1. GAN (LSTM + CNN)

- Generator: LSTM-based architecture
- Discriminator: 1D CNN
- Goal: Generate synthetic return sequences


### 2. TimeGAN

Implementation of TimeGAN architecture including:

- Embedding network
- Recovery network
- Generator network
- Discriminator network
- Supervised loss for temporal dynamics preservation


### 3. MTSS-GAN

Multi-time-scale sequence GAN designed to capture dependencies across different temporal scales.


## Evaluation

Generated time series were evaluated using:

### Statistical Metrics
- Mean and variance comparison
- Skewness
- Kurtosis
- Distribution similarity

### Stylized Facts Verification
- Fat-tail behaviour
- Volatility clustering
- Autocorrelation of squared returns
- Cross-asset correlations

Results were summarized in evaluation tables and visual comparison plots.


## Tech Stack

- Python
- PyTorch
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

## How to Run

### 1) Clone repository
```bash
git clone https://github.com/ekaterinassss/generative_models_course_project.git
cd generative_models_course_project
```

### 2) Create virtual environment
```bash
python -m venv .venv
source .venv/bin/activate  # macOS/Linux
# .venv\Scripts\activate   # Windows
```

### 3) Install dependencies
```bash
pip install -U pip
pip install -r requirements.txt
```

### 4) Launch notebook
```bash
jupyter lab
```

## Presentation

Project presentation is available here:
[presentation/Generative_models_presentation.pptx](presentation/Generative_models_presentation.pptx)


## Results

### Statistical Comparison of Generative Models

| Metric | Original | GAN | TimeGAN | MTSS-GAN | Diffusion | Previous Day Baseline |
|----------|------------|-----------|--------------|---------------|--------------|------------------------|
| Explained Variance | 0.001124 | -0.035098 | -0.010216 | -0.291834 | -0.003617 | -1.012976 |
| Max Error | 37.877058 | 37.698592 | 38.816030 | 36.970141 | 37.748598 | 38.335285 |
| Mean Absolute Error | 1.486249 | 1.530270 | 1.491838 | 1.763139 | 1.489851 | 2.156618 |
| Mean Squared Error | 5.176035 | 5.368649 | 5.291030 | 6.728434 | 5.226372 | 10.427247 |
| Mean Squared Log Error | 0.004859 | 0.004990 | 0.004973 | 0.005869 | 0.004904 | 0.009474 |
| Median Absolute Error | 0.991743 | 1.034137 | 0.989556 | 1.224650 | 0.988109 | 1.455725 |
| R² Score | 0.000768 | -0.036416 | -0.021431 | -0.298922 | -0.008949 | -1.012976 |


### Key Observations

- Diffusion model demonstrates the best overall performance across most statistical metrics.
- MTSS-GAN shows larger errors but captures regime dynamics.
- All generative models outperform the naive "previous day" baseline.


