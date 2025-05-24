# Aplos-NCA-Validations

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

The validation protocol for Aplos NCA will import the input dataset for the first test, analyze it using the configuration file, and then compare the results of the `pk-results.csv` file with the PK parameter results (`pk-results-expected-output.csv`) for the corresponding test. 

The compare tool, looks for exact matches for both text and numerical values.  
- Text values are case sensitive.
- Numeric values look for exact matches
    - Due to different operating systems we allow a .01% variance between the expected value and an engine value. See the **.01% Variance** section below.



## .01% Variance:

**Why We Allow a Small Variance in Numeric Comparisons**

Without a small tolerance for numeric differences, you may encounter validation failures due to slight variations in floating-point calculations. These can stem from differences in how the original expected results were generated (e.g., Code Library  & version (Python, R, C#, Java, etc), the OS (MacOS, Linux, Windows), or hardware architecture).

**Example**:

* **Expected**: `0.23389496666471427`
* **Engine**: `0.23389496666471424`

- <span style="color:green">0.2338949666647142</span><span style="color:red">7</span>
- <span style="color:green">0.2338949666647142</span><span style="color:red">4</span>

Although these values differ at the 17th decimal place, the **percent variance** is only:

```
~0.0000000000000158%
```

This is *many orders of magnitude* smaller than our default tolerance of `0.01%`, which is intentionally generous to account for such platform-level differences. These two values are effectively equivalent in all practical contexts.

Without this tolerance, even cases like the one below would be marked as a failure:

```json
{
"subject": 1,
"paramcd": "kel",
"value": "0.23389496666471427",
"kel_group": 9,
"param": "Terminal rate constant",
"units": "1 hr",
"validation": "fail",
"validation_reason": "Mismatch in 'value': expected='0.23389496666471427' vs engine='0.23389496666471424';"
}
```



