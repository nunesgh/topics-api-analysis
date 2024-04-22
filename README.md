# Topics API Analysis

[![DOI (v1.0)](https://zenodo.org/badge/DOI/10.5281/zenodo.11032231.svg)](https://doi.org/10.5281/zenodo.11032231)

DOI (v1.0): [10.5281/zenodo.11032231](https://doi.org/10.5281/zenodo.11032231).

This repository provides the experimental results of the paper *The Privacy-Utility Trade-off in the Topics API*.

## Usage

The notebooks were run using:
- Python v3.11.8
- bvmlib v1.0.0
- matplotlib 3.8.0
- numpy 1.24.3
- pandas 2.0.1
- qif 1.2.3
- requests 2.31.0
- scipy 1.11.3
- tldextract 5.1.2
- tqdm 4.66.1
- urllib3 1.26.16

The datasets produced for the experiments can be found on Zenodo: *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11029572](https://doi.org/10.5281/zenodo.11029572)).

## Notebooks

- Data treatment:
  - `AOL-data-treatment.ipynb`: Converts the original AOL dataset and generates the datasets `AOL-treated.csv` and `AOL-treated-unique-domains.csv`.
  - `Citizen-Lab-Classification-data-treatment.ipynb`: Converts the Citizen Lab Classification data, as of commit [ebd0ee8](https://github.com/citizenlab/test-lists/tree/ebd0ee8d41977b381972b2f6c471af5437d8d015/lists), and generates the dataset `Citizen-Lab-Classification.csv`.
  - `AOL-treated-Citizen-Lab-Classification-domain-matching.ipynb`: Matches domains from `AOL-treated-unique-domains.csv` with domains and respective topics from `Citizen-Lab-Classification.csv` and generates the dataset `AOL-treated-Citizen-Lab-Classification-domain-match.csv`.
  - `AOL-treated-Google-Topics-Classification-v1-domain-matching.ipynb`: Matches domains from `AOL-treated-unique-domains.csv` with domains and respective topics from `Google-Topics-Classification-v1.txt`, as provided by Google with the Chrome browser, and generates the dataset `AOL-treated-Google-Topics-Classification-v1-domain-match.csv`.
  - `AOL-reduced-Citizen-Lab-Classification.ipynb`: Converts the dataset `AOL-treated.csv` and generates the dataset `AOL-reduced-Citizen-Lab-Classification.csv`.
  - `AOL-reduced-Google-Topics-Classification-v1.ipynb`: Converts the dataset `AOL-treated.csv` and generates the dataset `AOL-reduced-Google-Topics-Classification-v1.csv`.
  - `AOL-experimental.ipynb`: Converts the dataset `AOL-treated.csv` and generates the dataset `AOL-experimental.csv`.
  - `AOL-experimental-Citizen-Lab-Classification.ipynb`: Converts the dataset `AOL-reduced-Citizen-Lab-Classification.csv` and generates the dataset `AOL-experimental-Citizen-Lab-Classification.csv`.
  - `AOL-experimental-Google-Topics-Classification-v1.ipynb`: Converts the dataset `AOL-reduced-Google-Topics-Classification-v1.csv` and generates the dataset `AOL-experimental-Google-Topics-Classification-v1.csv`.
- Analyses:
  - `QIF-analyses-AOL-experimental.ipynb`: QIF analyses based on the dataset `AOL-experimental.csv`.
  - `QIF-analyses-AOL-experimental-Citizen-Lab.ipynb`: QIF analyses based on the dataset `AOL-experimental-Citizen-Lab-Classification.csv`.
  - `QIF-analyses-AOL-experimental-Google-Topics-v1.ipynb`: QIF analyses based on the dataset `AOL-experimental-Google-Topics-Classification-v1.csv`.
  - `QIF-analyses-counting-experiment.ipynb`: QIF analysis for counting topics popularity using the binomial distribution. 

## License

[GNU LGPLv3](https://choosealicense.com/licenses/lgpl-3.0/).

To understand how the various GNU licenses are compatible with each other, please refer to the GNU licenses [FAQ](https://www.gnu.org/licenses/gpl-faq.html#AllCompatibility).
