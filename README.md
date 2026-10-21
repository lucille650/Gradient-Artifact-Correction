# Optimized Moving Average Filter

`OptimizedMovingAverageFilter.ipynb` removes the scanner gradient artifact from simultaneous EEG–fMRI and saves the cleaned EEG via an optimized moving average filter suggested by Ferreira et al. (2016).

Run the notebook from this folder. It needs Python with `mne`, `numpy`, `scipy`, and `matplotlib`.

## What it does

1. Loads `SUB2888_ses03_20241216_034412.mff` (change this path for another raw recording).
2. Keeps the first 128 EEG channels (Others are digital input).
3. Applies the optimized moving average filter.
4. Average-references the data and demeans each channel.
5. Saves `oma_cleaned_signal.mat`.

## Parameters

Set in the second cell:

- `M = 1030`: time between volume triggers, in samples.
- `J = 20000`: how strongly the filter notches that rhythm. Ferreira et al. suggest J=200,000 but J=20,000 worked best for our particular dataset.
- `L = 1`: one pass since this when the trigger timing is stable.

## Output

`oma_cleaned_signal.mat` contains `cleaned_eeg_data`, `srate`, `chanlabels`, and the `M`, `J`, and `L` values used for the run. (.mat format used because downstream BCG correction is implemented in MATLAB).

## Reference
Ferreira, J. L., Wu, Y., Besseling, R. M. H., Lamerichs, R., & Aarts, R. M. (2016). Gradient artefact correction and evaluation of the EEG recorded simultaneously with fMRI data using optimised moving-average. Journal of Medical Engineering, 2016, 9614323. https://doi.org/10.1155/2016/9614323
