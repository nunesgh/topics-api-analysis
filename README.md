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

## Data treatment

The data treatment notebooks are primarily for reference and were used to generate the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)) files.

To execute the analyses notebooks, please make sure to add to the folder `data-treatment/` the respective files from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

## Analyses

To execute the analyses notebooks, please make sure to add to the folder `analyses/` the respective files from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

## License

[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/).

To understand how the various GNU licenses are compatible with each other, please refer to the GNU licenses [FAQ](https://www.gnu.org/licenses/gpl-faq.html#AllCompatibility).
