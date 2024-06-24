# Topics API Analysis

## Analyses

To execute the analyses notebooks, please make sure to add to the folder `analyses/` the respective files from the *AOL Dataset for Browsing History and Topics of Interest* (DOI: [10.5281/zenodo.11229615](https://doi.org/10.5281/zenodo.11229615)).

The notebooks are listed in order of execution.

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
