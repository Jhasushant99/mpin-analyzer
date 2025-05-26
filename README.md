# MPIN-analyzer

## Background

Mobile Personal Identification Numbers (MPINs) are commonly used to access mobile banking apps securely. However, many users choose MPINs that are easily guessable, which poses a security risk. Common reasons why MPINs are weak include:

1. The MPIN is a **commonly used** one (e.g., `1122`, `0000`, `2580`).
2. The MPIN is derived from **user demographics** such as:
   - Date of Birth (DOB)
   - Wedding Anniversary
   - Spouse's Date of Birth
   
For example, if a user's DOB is `02-Jan-1998`, common MPINs might be `0201`, `9802`, or `0198` (combinations of day, month, year). These demographics may be used alone or in combination, making such MPINs weak and guessable.

---

## Problem Statement and Project Parts

### Part A: Common MPINs Check (4-digit MPIN)

- Write a program to check if a given 4-digit MPIN is among commonly used MPINs.
- If the MPIN is common, it should be flagged as **WEAK**.
- Ignore demographics in this part.

### Part B: MPIN Strength with Demographics Input (4-digit MPIN)

- Extend the program to accept user demographic inputs:
  - Date of Birth (DOB)
  - Wedding Anniversary
  - Spouse's Date of Birth
- The program should analyze the MPIN against these demographics.
- Output the MPIN strength as **WEAK** or **STRONG**.

### Part C: Detailed Reasons for Weak MPINs (4-digit MPIN)

- Further enhance the program to provide:
  - MPIN Strength: **WEAK** or **STRONG**
  - Reasons for weakness (if any), as an array containing one or more of the following:
    - `COMMONLY_USED`
    - `DEMOGRAPHIC_DOB_SELF`
    - `DEMOGRAPHIC_DOB_SPOUSE`
    - `DEMOGRAPHIC_ANNIVERSARY`
  - If the MPIN is strong, the reasons array should be empty.

### Part D: Support for 6-digit MPINs

- Extend all previous functionality to handle both 4-digit and 6-digit MPINs.
- Apply common checks and demographic combinations appropriately.

---

## Implementation Overview

The solution is implemented as a single Jupyter Notebook `Sushant_MPIN.ipynb`, containing:

- A **list of commonly used MPINs** for 4-digit and 6-digit PINs.
- Functions to **extract demographic date combinations** (day, month, year, reversed year, and their concatenations).
- A main function to **check MPIN strength** based on common usage and demographics.
- Detailed output including **strength and reasons** for weakness.
- A comprehensive **test suite** with at least 20 test cases covering various scenarios.

---

## How to Use

1. Open the Jupyter notebook `Sushant_MPIN.ipynb`.
2. Input your MPIN and demographic data such as DOB, Spouse DOB, and Wedding Anniversary in the designated cells.
3. Run the notebook cells to execute the MPIN strength check.
4. The output will display the strength (`WEAK` or `STRONG`) and reasons (if any).

---

## Example Usage

```python
PIN = "1122"
DOB = "02-01-1998"
Spouse_DOB = "10-12-1990"
Wedding_Anniversary = "15-06-2015"

strength, reasons = check_strength_reason(PIN, DOB, Spouse_DOB, Wedding_Anniversary)

print(f"Strength: {strength}")
print(f"Reasons: {reasons}")
Output:
Strength: WEAK
Reasons: ['COMMONLY_USED']
tests = [
    ('0000', None, None, None, "WEAK", ["COMMONLY_USED"]),
    ('2580', None, None, None, "WEAK", ["COMMONLY_USED"]),
    ('4321', None, None, None, "WEAK", ["COMMONLY_USED"]),
    ('112233', None, None, None, "WEAK", ["COMMONLY_USED"]),
    ('930284', None, None, None, "STRONG", []),
    # Add more test cases as needed
]

for i, (pin, dob, spouse_dob, anniversary, exp_strength, exp_reasons) in enumerate(tests, 1):
    strength, reasons = check_strength_reason(pin, dob, spouse_dob, anniversary)
    assert strength == exp_strength, f"Test {i} failed on strength check"
    assert sorted(reasons) == sorted(exp_reasons), f"Test {i} failed on reasons"
Author:-
Sushant Shekhar
Email: sushant62044@gmail.com
LinkedIn: www.linkedin.com/in/sushantshekhar09/

