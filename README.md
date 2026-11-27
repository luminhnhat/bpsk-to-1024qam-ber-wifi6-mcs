# bpsk-to-1024qam-ber-wifi6-mcs
# BER Performance of BPSK to 1024-QAM over AWGN and MCS Selection for Wi-Fi 6

Project for the Communication Systems course, Faculty of Electronics and Telecommunications, VNU-HCMUS.

## Overview
This project studies the bit error rate (BER) of square M-QAM, from BPSK up to 1024-QAM, in an additive white Gaussian noise (AWGN) channel, then uses the results to select the optimal modulation and coding scheme (MCS) for Wi-Fi 6 (IEEE 802.11ax).

- Analytical BER of Gray-coded square QAM, cross-checked against MATLAB's `berawgn`
- Monte Carlo simulation (145 points, all within the confidence interval)
- MCS selection by maximizing goodput, for uncoded and approximated coded models (12 HE MCS)
- Effect of transmitter error vector magnitude (EVM) limits on the usable MCS, including 1024-QAM
- Gap to the Shannon limit

## Key results
- **BER verification:** Monte Carlo simulation (145 points) lies entirely within the confidence interval of the exact Cho–Yoon formula and matches MATLAB's `berawgn`.
- **Required Eb/N0 for BER = 1e-5:** rises from 9.59 dB (BPSK) to 37.47 dB (1024-QAM), about +6 dB for every 4x increase in constellation size, while the nominal rate gain shrinks from +100% to +25%.
- **Gap to Shannon limit:** 7.4–7.8 dB for QAM (4-QAM to 1024-QAM).
- **Uncoded model:** with the 802.11ax EVM limit, 1024-QAM is never selected.
- **Coded model (12 HE MCS):** MCS10–11 remain usable, with switching thresholds of 34.1 / 36.1 dB (EVM = -35 dB) instead of 31.5 / 32.5 dB (ideal).
- **Effect of EVM on MCS11:** at EVM = -32 dB, MCS11 is no longer available and peak goodput drops by about 14% (143.4 to 123.1 Mbps).

**Limitations:** AWGN channel only, and coding gain is approximated by an SNR shift, so thresholds are mainly useful for relative comparison.

## Repository structure
- `src/` : MATLAB simulation code
- `results/` : figures
- `report/` : full report 

## How to run
Requirements: MATLAB [version R2026b] with Communications Toolbox (for `berawgn`).

1. Clone the repository and open the `src/` folder in MATLAB.
2. Run `[main_script_name].m` to reproduce the BER curves and the MCS selection results.
3. Figures are saved to `results/`:
   - BER: simulation vs. theory for BPSK to 1024-QAM
   - Spectral efficiency vs. Shannon limit
   - Goodput per MCS and the optimal envelope
   - Effect of transmitter EVM on the coded model

## My contribution
- Implemented the Monte Carlo BER simulation and verified it against the analytical formula.
- Built the MCS selection model (goodput maximization, 12 HE MCS)
- Analyzed the effect of transmitter EVM on MCS availability
- Wrote the report


## References
See the report for the full reference list.
