# Change Log

## Version 1.0

Calculation Engines:
- `aplah`
- `beta`
- `RC` (Release Candidates) 0.0.1 - 0.55.89
- `GA` (General Availability / Production) 1.0.0-1.15.25

The tests for `v1.0` can be found in this repo [here](./v1.0/) as well as in our original `validation` [repo](https://github.com/AplosAnalytics/validation)

## Version 1.1

Caculations Engines:
- `GA` 1.16.0 +

Version 1.0 contained some duplicate records in the outputs as well as corresponding duplicates in the validation files.

The following updates are reflected in the version 1.1

- Version 1.1 uses a stricter guideline and has been adapted to check all columns including `param` and `units`, as well as any additional ad-hoc carry along columns.
- Duplicates were detected and removed from the engine starting with `v1.16.0`
- Duplicates contained the same value and were repeated in all `kel_groups`.  In general they are a non-issue.  However, post processing tables which required pivots may have caused issues rendering reporting outputs.
- In the validation engine v1.1, duplicates will render a `fail` 