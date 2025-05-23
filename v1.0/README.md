# Aplos-NCA-Validations v1.0

The files in this repository are used by the validation protocol of Aplos NCA to confirm that the PK parameter calculations are accurate. 

> The most recent active GA (General Availability) version used for validations is dependant on the current engine number.

Over time the validations may change due to parameter updates.  These changes will be noted in a change log found [here](./CHANGELOG.md).


This repository includes 6 different tests that correspond to each of the following routes of administration and dosing frequencies:

* Test 1: Single extravascular dose
* Test 2: Single intravenous (IV) bolus dose
* Test 3: Single IV infusion dose
* Test 4: Steady-state extravascular dose
* Test 5: Steady-state IV bolus dose
* Test 6: Steady-state IV infusion dose

For each test, there is an input data file, an analysis configuration file, and the PK parameter results. The naming structures of these files are as follows:
* Input data file: `test[nn]/input.csv`
* Configuration file: `test[nn]/config.json`
* PK parameter results: `test[nn]/pk-results-expected-output.csv`

The validation protocol for Aplos NCA will import the input dataset for the first test, analyze it using the configuration file, and then compare the results of the "pk-results.csv" file with the PK parameter results included here. 

The relative difference for all numerical calculations will be compared, and any relative differences greater than 0.01% will be flagged as a test failure. If no relative differences are identified, the test will pass. Then this process will be repeated for the remaining 5 tests. If all 6 tests pass, then the Aplos NCA validation will report an overall pass in the validation report. If one or more tests fail, the Aplos NCA validation will report an overall failure.
