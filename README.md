# MeLiDos UCR GLC dataset

This repository contains the San Pedro, San José, Costa Rica site data
collected by the Universidad de Costa Rica (UCR) for the MeLiDos field study.
It is a GLC Schema 3.0.2 Data Package derived from the
[original MeLiDos dataset](https://github.com/MeLiDosProject/Sancho-SalasEtAl_Dataset_2025).

The package entry point is `datapackage.json`. Core metadata are stored in
`data/`, while the 671 participant-level CSV files referenced by
`data/datasets.json` are organized under:

- `data/files/sensor/`;
- `data/files/longitudinal-reports/`;
- `data/files/questionnaires/`; and
- `data/files/study-timing/`.

The source dataset is:

> Sancho-Salas, A., von-Breymann, H., Zauner, J., & Spitschan, M. (2025).
> *Personal light exposure dataset for San Pedro, San José, Costa Rica*
> (Version 1.0.0) [Data set]. https://doi.org/10.5281/zenodo.17289456

The refactoring converts the source repository's processed tabular RData
resources to UTF-8 CSV, separates records by participant, and supplies GLC
3.0.2 metadata. Source measurement values are otherwise preserved.

## Important preprocessing note

The chest and glasses import scripts restrict the sensor data to each
participant's trial interval before regularizing timestamp gaps. In the wrist
import script, the trial-filtered object is assigned to `data2`, but the
subsequent regularization and export operate on the original `data` object.
Consequently, the published processed wrist tables are not reliably restricted
to the participant-specific trial intervals. This upstream discrepancy is
recorded in each wrist file group's preprocessing metadata and should be fixed
when the source import pipeline is revised.

## Calibration-date note

The source metadata workbook supplies device delivery dates but no separately
identified calibration dates. Those delivery dates are used provisionally as
calibration-date proxies and must be checked against the underlying calibration
records when available.

## Validation

The package is validated against GLC Schema 3.0.2 with validator 0.5.2.
Validation also runs automatically through
`.github/workflows/validate-glc-dataset.yml`.

## License

The dataset is licensed under the Creative Commons Attribution 4.0
International License (CC BY 4.0). See `LICENSE`.
