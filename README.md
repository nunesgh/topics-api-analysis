# Topics API Analysis

[![DOI (v1.0)](https://zenodo.org/badge/DOI/10.5281/zenodo.11032231.svg)](https://doi.org/10.5281/zenodo.11032231)

DOI (v1.0): [10.5281/zenodo.11032231](https://doi.org/10.5281/zenodo.11032231).

This repository provides the experimental results of the paper *The Privacy-Utility Trade-off in the Topics API*.

## Usage

The notebooks were run using:

- `Python` v3.11.9
- `bvmlib` v1.0.0
- `matplotlib` 3.8.0
- `numpy` 1.24.3
- `pandas` 2.0.1
- `qif` 1.2.3
- `requests` 2.31.0
- `scipy` 1.11.3
- `tldextract` 5.1.2
- `tqdm` 4.66.1
- `urllib3` 1.26.16

Please note that [`qif`](https://github.com/chatziko/libqif), as of version 1.2.3, is not compatible with Apple Silicon processors. This is a known issue already reported on the module's GitHub repository: [Support for M1 Mac](https://github.com/chatziko/libqif/issues/6).

The datasets produced for the experimental analyses can be found on Zenodo: *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

## Notebooks

### Data treatment

The data treatment notebooks are primarily for reference and were used to generate the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)) files.

In particular, the `AOL-data-treatment.ipynb` notebook converts the original AOL dataset, i.e. the `AOL-[1-10].csv` files, to the first two datasets that are part of the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)), i.e. `AOL-treated.csv` and `AOL-treated-unique-domains.csv`. The original AOL dataset is known to be poorly sanitized for privacy protection and it is not provided as part of this artifact.

For all the other notebooks, the input files are either directly downloaded from GitHub, i.e. Citizen Lab's test lists at commit [ebd0ee8](https://github.com/citizenlab/test-lists/tree/ebd0ee8d41977b381972b2f6c471af5437d8d015/lists) and Mozilla's Public Suffix List at commit [5e6ac3a](https://github.com/publicsuffix/list/tree/5e6ac3a082505ac4cf08858bdb38382d9a912833), or can be downloaded from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

1. `data-treatment/AOL-data-treatment.ipynb`:
    - Converts the original AOL dataset (which is not provided as part of this artifact).
    - Treats inconsistencies; Randomly remaps `AnonID` to `RandID`; Defines domains from URLs; and Filters domains by eTLD using `tldextract` and Mozilla's Public Suffix List, as of commit [5e6ac3a](https://github.com/publicsuffix/list/tree/5e6ac3a082505ac4cf08858bdb38382d9a912833), extended by the discontinued TLDs: .bg.ac.yu, .ac.yu, .cg.yu, .co.yu, .edu.yu, .gov.yu, .net.yu, .org.yu, .yu, .or.tp, .tp, and .an.
    - Generates the datasets `AOL-treated.csv` and `AOL-treated-unique-domains.csv`.
        - The dataset `AOL-treated.csv` can be used for analyses of browsing history vulnerability and utility, as enabled by third-party cookies.
        - This dataset contains singletons (individuals with only one domain in their browsing histories) and one outlier (one user with 150.802 domain visits in three months) that are dropped in some analyses.
2. `data-treatment/Citizen-Lab-Classification-data-treatment.ipynb`:
    - Converts the Citizen Lab Classification data, as of commit [ebd0ee8](https://github.com/citizenlab/test-lists/tree/ebd0ee8d41977b381972b2f6c471af5437d8d015/lists).
    - Treats inconsistencies; Defines domains from URLs; Filters domains by eTLD using `tldextract` and Mozilla's Public Suffix List, as of commit [5e6ac3a](https://github.com/publicsuffix/list/tree/5e6ac3a082505ac4cf08858bdb38382d9a912833), extended by the discontinued TLDs: .bg.ac.yu, .ac.yu, .cg.yu, .co.yu, .edu.yu, .gov.yu, .net.yu, .org.yu, .yu, .or.tp, .tp, and .an; and Merges classifications by domain.
    - Generates the dataset `Citizen-Lab-Classification.csv`.
3. `data-treatment/AOL-treated-Citizen-Lab-Classification-domain-matching.ipynb`:
    - Matches domains from `AOL-treated-unique-domains.csv` with domains and respective topics from `Citizen-Lab-Classification.csv`.
    - Generates the dataset `AOL-treated-Citizen-Lab-Classification-domain-match.csv`.
4. `data-treatment/AOL-treated-Google-Topics-Classification-v1-domain-matching.ipynb`:
    - Matches domains from `AOL-treated-unique-domains.csv` with domains and respective topics from `Google-Topics-Classification-v1.txt`, as provided by Google with the Chrome browser.
    - Generates the dataset `AOL-treated-Google-Topics-Classification-v1-domain-match.csv`.
5. `data-treatment/AOL-reduced-Citizen-Lab-Classification.ipynb`:
    - Converts the dataset `AOL-treated.csv`.
    - Reduces the dataset `AOL-treated.csv` according to the dataset `AOL-treated-Citizen-Lab-Classification-domain-match.csv`.
    - Generates the dataset `AOL-reduced-Citizen-Lab-Classification.csv`.
        - The dataset `AOL-reduced-Citizen-Lab-Classification.csv` can be used for analyses of browsing history vulnerability and utility, as enabled by third-party cookies, and for analyses of topics of interest vulnerability and utility, as enabled by the Topics API.
        - This dataset contains singletons and the outlier that are dropped in some analyses.
        - This dataset can be used for analyses including the (data-dependent) randomness of trimming-down or filling-up the top-s sets of topics for each individual so each set has s topics.
        - Privacy results for Generalization and utility results for Generalization, Bounded Noise, and Differential Privacy are expected to slightly vary with each run of the analyses over this dataset.
6. `data-treatment/AOL-reduced-Google-Topics-Classification-v1.ipynb`:
    - Converts the dataset `AOL-treated.csv`.
    - Reduces the dataset `AOL-treated.csv` according to the dataset `AOL-treated-Google-Topics-Classification-v1-domain-match.csv`.
    - Generates the dataset `AOL-reduced-Google-Topics-Classification-v1.csv`.
        - The dataset `AOL-reduced-Google-Topics-Classification-v1.csv` can be used for analyses of browsing history vulnerability and utility, as enabled by third-party cookies, and for analyses of topics of interest vulnerability and utility, as enabled by the Topics API.
        - This dataset contains singletons and the outlier that are dropped in some analyses.
        - This dataset can be used for analyses including the (data-dependent) randomness of trimming-down or filling-up the top-s sets of topics for each individual so each set has s topics.
        - Privacy results for Generalization and utility results for Generalization, Bounded Noise, and Differential Privacy are expected to slightly vary with each run of the analyses over this dataset.
7. `data-treatment/AOL-experimental.ipynb`:
    - Converts the dataset `AOL-treated.csv`.
    - Drops singletons (individuals with only one domain in their browsing histories) and one outlier (one user with 150.802 domain visits in three months); and Defines browsing histories.
    - Generates the dataset `AOL-experimental.csv`.
        - The dataset `AOL-experimental.csv` can be used to empirically verify code correctness.
        - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.
8. `data-treatment/AOL-experimental-Citizen-Lab-Classification.ipynb`:
    - Converts the dataset `AOL-reduced-Citizen-Lab-Classification.csv`.
    - Generates the dataset `AOL-experimental-Citizen-Lab-Classification.csv`.
        - The dataset `AOL-experimental-Citizen-Lab-Classification.csv` can be used to empirically verify code correctness.
        - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.
9. `data-treatment/AOL-experimental-Google-Topics-Classification-v1.ipynb`:
    - Converts the dataset `AOL-reduced-Google-Topics-Classification-v1.csv`.
    - Generates the dataset `AOL-experimental-Google-Topics-Classification-v1.csv`.
        - The dataset `AOL-experimental-Google-Topics-Classification-v1.csv` can be used to empirically verify code correctness.
        - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.

### Analyses

To execute the analyses notebooks, please make sure to add to the folder `analyses/` the respective file from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

1. `analyses/QIF-analyses-AOL-treated.ipynb`:
    - QIF analyses based on the dataset `AOL-treated.csv`.
    - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.
2. `analyses/QIF-analyses-AOL-reduced-Citizen-Lab.ipynb`:
    - QIF analyses based on the dataset `AOL-reduced-Citizen-Lab-Classification.csv`.
    - Privacy results for Generalization and utility results for Generalization, Bounded Noise, and Differential Privacy are expected to slightly vary with each run of the analyses over this dataset.
3. `analyses/QIF-analyses-AOL-reduced-Google-Topics-v1.ipynb`:
    - QIF analyses based on the dataset `AOL-reduced-Google-Topics-Classification-v1.csv`.
    - Privacy results for Generalization and utility results for Generalization, Bounded Noise, and Differential Privacy are expected to slightly vary with each run of the analyses over this dataset.
4. `analyses/QIF-analyses-counting-experiment.ipynb`:
    - QIF analysis for counting topics popularity using the binomial distribution.
5. `analyses/QIF-analyses-AOL-experimental.ipynb`:
    - QIF analyses based on the dataset `AOL-experimental.csv`.
    - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.
6. `analyses/QIF-analyses-AOL-experimental-Citizen-Lab.ipynb`:
    - QIF analyses based on the dataset `AOL-experimental-Citizen-Lab-Classification.csv`.
    - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.
7. `analyses/QIF-analyses-AOL-experimental-Google-Topics-v1.ipynb`:
    - QIF analyses based on the dataset `AOL-experimental-Google-Topics-Classification-v1.csv`.
    - All privacy and utility results are expected to remain the same with each run of the analyses over this dataset.

## License

[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/).

To understand how the various GNU licenses are compatible with each other, please refer to the GNU licenses [FAQ](https://www.gnu.org/licenses/gpl-faq.html#AllCompatibility).
