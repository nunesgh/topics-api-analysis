# Topics API Analysis

## Data treatment

The data treatment notebooks are primarily for reference and were used to generate the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)) files.

In particular, the `data-treatment/AOL-data-treatment.ipynb` notebook converts the original AOL dataset, i.e. the `AOL-[1-10].csv` files, to the first two datasets that are part of the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)), i.e. `AOL-treated.csv` and `AOL-treated-unique-domains.csv`. The original AOL dataset is known to be poorly sanitized for privacy protection and it is not provided as part of this artifact.

For all the other notebooks, the input files are either directly downloaded from GitHub, i.e. Citizen Lab's test lists at commit [ebd0ee8](https://github.com/citizenlab/test-lists/tree/ebd0ee8d41977b381972b2f6c471af5437d8d015/lists) and Mozilla's Public Suffix List at commit [5e6ac3a](https://github.com/publicsuffix/list/tree/5e6ac3a082505ac4cf08858bdb38382d9a912833), or can be downloaded from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

To execute the analyses notebooks, please make sure to add to the folder `data-treatment/` the respective files from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

The notebooks are listed in order of execution.

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

## License

[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/).

To understand how the various GNU licenses are compatible with each other, please refer to the GNU licenses [FAQ](https://www.gnu.org/licenses/gpl-faq.html#AllCompatibility).
