# Econometrics Project – Oil Price Dynamics and Futures Market Positioning

## Project Overview

This project analyzes the determinants of short-term movements in crude oil prices using econometric methods.

The objective is to test whether changes in positions held by different types of traders in the oil futures market help explain weekly movements in **WTI crude oil prices**.

Modern oil markets are highly financialized. While global physical consumption is around **100 million barrels per day**, financial trading in oil derivatives can reach **several billion barrels per day**. This suggests that financial flows may play a significant role in oil price formation.

The project therefore investigates the following question:

> Can changes in trader positioning in the oil futures market explain variations in WTI oil prices?

---

## Data Sources

The analysis combines two main datasets.

### CFTC Disaggregated Futures Data

The **CFTC Disaggregated Futures-and-Options report** provides weekly information about positions held by different types of traders in the futures market.

The dataset focuses on:

**WTI – NYMEX (WTI-PHYSICAL - NEW YORK MERCANTILE EXCHANGE)**

For each week we compute **net positions (long – short)** for the following trader categories:

- Managed Money (hedge funds and CTAs)
- Producer/Merchant/Processor/User (physical hedgers)
- Swap Dealers (banks and financial intermediaries)
- Other Reportables (other institutional participants)

These variables capture the evolution of market positioning across different types of traders.

---

### Market Price Data

Market data was obtained through **Yahoo Finance** using Python.

The main asset used in the analysis is:

**WTI crude oil futures (CL=F)**

From this series we compute **weekly changes in oil prices** to match the frequency of the CFTC positioning data.

---

## Econometric Methodology

The core of the project relies on **Ordinary Least Squares (OLS) regressions**.

The baseline econometric model explains weekly oil price changes using variations in trader positions:

ΔOilₜ = β₀ + β₁ΔHFₜ + β₂ΔSwapₜ + β₃ΔProdₜ + β₄ΔOtherₜ + εₜ

Where:

- ΔOilₜ = weekly change in WTI price  
- ΔHFₜ = change in hedge fund positions (Managed Money)  
- ΔSwapₜ = change in swap dealer positions  
- ΔProdₜ = change in producer hedging positions  
- ΔOtherₜ = change in positions of other institutions  

Robust standard errors (**HC1**) were used to ensure reliable statistical inference.

---

## Extended Analysis

To test the robustness of the results, additional models include **macro-financial variables**, such as:

- S&P 500 Index
- U.S. Dollar Index
- VIX Volatility Index
- U.S. 10-Year Treasury Yield

These variables allow us to test whether oil price movements are driven primarily by:

- futures market positioning (trading flows)
- broader macro-financial conditions

---

## Key Findings

The regression results indicate that trader positioning explains a significant share of oil price movements.

The main regression achieves an **R² of approximately 0.54**, meaning that around **54% of weekly oil price variation** can be explained by changes in trader positions.

The results support the idea that **financial flows play an important role in oil price dynamics**, particularly through speculative traders such as hedge funds.

This finding is consistent with the broader literature suggesting that commodity markets are increasingly influenced by **financial trading activity** in addition to traditional supply and demand fundamentals.

---

## Technical Implementation

The analysis was conducted using **Python**, with the following libraries:

- pandas
- yfinance
- statsmodels
- matplotlib

The workflow consists of:

1. Importing CFTC positioning data
2. Downloading oil price data from Yahoo Finance
3. Aligning datasets on a weekly frequency
4. Computing changes in trader positions
5. Running OLS regressions
6. Interpreting the econometric results

---

## Repository Structure
