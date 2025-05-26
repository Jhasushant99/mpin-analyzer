# MPIN Analyzer

#

A structured solution to identify weak MPINs (Mobile Personal Identification Numbers) based on common patterns and user-specific data like DOB, spouse DOB, and anniversary.

---

## 🅐️ A. Problem Statement

In a world where security is paramount, many users still opt for predictable MPINs such as:

* `1234`, `0000`, `2580`
* Their own or loved one's birthdate

These are easily guessable and thus vulnerable to brute-force attacks. This tool was developed to **automatically evaluate** the strength of a given PIN and suggest reasons if it's considered weak.

---

## 🅑️ B. Objective

To implement a robust Python-based MPIN checker that:

* Flags commonly used PINs
* Detects PINs based on date combinations from user’s personal life
* Categorizes MPINs as `WEAK` or `STRONG`
* Provides meaningful reasons for a weak classification

---

## 🅒️ C. Solution Overview

The project is modularized into the following components:

```plaintext
Sushant_MPIN_Project/
├── A. common.py           # 📌 Contains common PINs (4-digit & 6-digit)
├── B. combinations.py     # 🗕️ Extracts combinations from DOB, etc.
├── C. checker.py          # 🔍 Core logic to check PIN strength
├── D. test_cases.py       # ✅ Automated test validation
├── E. Sushant_MPIN.ipynb  # 📓 Full implementation in Jupyter Notebook
└── README.md              # 📘️ Project documentation
```

---

## 🅓️ D. How It Works

1. **Common PIN Match**
   Compares input against a database of widely used 4- and 6-digit PINs.

2. **Date-Based Match**
   Generates permutations of DD/MM/YY from:

   * User's DOB
   * Spouse's DOB
   * Wedding anniversary
     Then compares them with the PIN.

3. **Result Generation**
   Outputs:

   * `WEAK` → with reasons like `COMMONLY_USED`, `DEMOGRAPHIC_DOB_SELF`, etc.
   * `STRONG` → when PIN is unique and unrelated

---

## 🅔️ E. Sample Test Output

```text
Test 1: PIN=0000, Strength=WEAK, Reasons=['COMMONLY_USED'] -> Passed ✅
Test 6: PIN=150896, Strength=WEAK, Reasons=['DEMOGRAPHIC_DOB_SELF'] -> Passed ✅
Test 12: PIN=930284, Strength=STRONG, Reasons=[] -> Passed ✅
```

---

## 🚀 Get Started

1. Clone the repo:

   ```bash
   git clone https://github.com/your-username/Sushant_MPIN_Project.git
   cd Sushant_MPIN_Project
   ```

2. Run the main logic:

   ```bash
   python checker.py
   ```

3. Run test cases:

   ```bash
   python test_cases.py
   ```

4. Or explore visually in notebook:

   ```bash
   jupyter notebook Sushant_MPIN.ipynb
   ```

---

## 👤 Author

**Sushant Shekhar**\\

---

