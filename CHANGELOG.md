# Change Log

## Version 3.101

Calculation Engines:
- `GA` 3.101.0 +

The following updates are reflected in version 3.101:

- **CLss unit fix**: Corrected the units for the two `CLss` fields in the steady-state test outputs.

---

## Version 3.0

Calculation Engines:
- `GA` 3.0.0 +

> Version 2.x was skipped. The v1.x platform used a mix of v1 and v2 libraries internally. Version 3.0 centralizes on the new platform and versioning standard.

The following updates are reflected in version 3.0:

- **New platform version**: Aligned validation files with the v3.0 calculation engine and unified library stack.
- **Configuration structure update**: The analysis configuration is now wrapped in a top-level `"configuration"` key (e.g., `{ "configuration": { ... } }`).
- **Cleaner config separation**: Removed extraneous fields (`tau`, `infusion`) from non-infusion test configurations.
- **Expected output file renamed**: `pk-results-expected-output.csv` → `pk-results-expected.csv`
- **New `maxp_value` column**: Expected results now include a `maxp_value` column containing the full (max precision) calculated value. The `value` column contains the rounded/formatted result using the significant figures logic in the analysis engine.
- **New `pk-results-all-expected.csv`**: An additional expected output file containing results for all kel groups (tests 1–5).
- **New `test_config.json` per test**: Each test directory now includes a `test_config.json` file with test metadata, file references, and test options.

---

## Version 1.1

Calculation Engines:
- `GA` 1.16.0 +

Version 1.0 contained some duplicate records in the outputs as well as corresponding duplicates in the validation files.

The following updates are reflected in the version 1.1

- Version 1.1 uses a stricter guideline and has been adapted to check all columns including `param` and `units`, as well as any additional ad-hoc carry along columns.
- Duplicates were detected and removed from the engine starting with `v1.16.0`
- Duplicates contained the same value and were repeated in all `kel_groups`.  In general they are a non-issue.  However, post processing tables which required pivots may have caused issues rendering reporting outputs.
- In the validation engine v1.1, duplicates will render a `fail` 

---

## Version 1.0

Calculation Engines:
- `alpha`
- `beta`
- `RC` (Release Candidates) 0.0.1 - 0.55.89
- `GA` (General Availability / Production) 1.0.0-1.15.25

The tests for `v1.0` can be found in this repo [here](./v1.0/) as well as in our original `validation` [repo](https://github.com/AplosAnalytics/validation)