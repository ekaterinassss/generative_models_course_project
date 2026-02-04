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


## Project Structure

