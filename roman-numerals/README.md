# Roman Numerals

Convert between Roman numerals and integers, building up to a Roman numeral calculator.

## Task 1: Basic Numerals

Write a function that converts a Roman numeral string to an integer. Start with just additive notation using these symbols:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

For now, assume numerals are additive only (no subtraction like IV).

### Examples

| Input    | Output |
| -------- | ------ |
| `"I"`    | 1      |
| `"III"`  | 3      |
| `"VII"`  | 7      |
| `"XVI"`  | 16     |
| `"LXVI"` | 66     |
| `"MDCL"` | 1650   |

---

## Task 2: Subtractive Notation

Extend your function to handle subtractive notation, where a smaller numeral before a larger one means subtraction:

| Pattern | Value |
| ------- | ----- |
| IV      | 4     |
| IX      | 9     |
| XL      | 40    |
| XC      | 90    |
| CD      | 400   |
| CM      | 900   |

### Examples

| Input       | Output |
| ----------- | ------ |
| `"IV"`      | 4      |
| `"IX"`      | 9      |
| `"XLII"`    | 42     |
| `"XCIX"`    | 99     |
| `"CDXLIV"`  | 444    |
| `"MCMXCIV"` | 1994   |
| `"MMXXVI"`  | 2026   |

---

## Task 3: Integer to Roman

Write a function that converts an integer to a Roman numeral string. Use standard form (e.g., 4 → "IV", not "IIII").

### Examples

| Input | Output        |
| ----- | ------------- |
| 1     | `"I"`         |
| 4     | `"IV"`        |
| 9     | `"IX"`        |
| 42    | `"XLII"`      |
| 99    | `"XCIX"`      |
| 1994  | `"MCMXCIV"`   |
| 2026  | `"MMXXVI"`    |
| 3999  | `"MMMCMXCIX"` |

---

## Task 4: Input Validation

Extend your Roman-to-integer function to reject invalid Roman numerals and throw an appropriate error.

Invalid cases include:

- Empty string
- Invalid characters (e.g., `"ABC"`, `"IVX2"`)
- Too many consecutive identical numerals (e.g., `"IIII"`, `"VV"`, `"XXXX"`)
- Invalid subtractive combinations (e.g., `"IL"`, `"IC"`, `"VX"`, `"LC"`)
- Numerals not in descending order where subtraction doesn't apply (e.g., `"IVI"`)

### Examples

| Input    | Result                          |
| -------- | ------------------------------- |
| `""`     | Error: empty input              |
| `"ABC"`  | Error: invalid character 'A'    |
| `"IIII"` | Error: too many consecutive I's |
| `"VV"`   | Error: V cannot be repeated     |
| `"IL"`   | Error: invalid subtractive pair |
| `"IC"`   | Error: invalid subtractive pair |

---

## Task 5: Case Insensitivity & Whitespace

Make your functions more lenient:

- Accept lowercase input (`"iv"` → 4)
- Accept mixed case (`"McmXcIv"` → 1994)
- Ignore leading/trailing whitespace (`"  XIV  "` → 14)

### Examples

| Input       | Output |
| ----------- | ------ |
| `"iv"`      | 4      |
| `"mcmxciv"` | 1994   |
| `"  XIV  "` | 14     |
| `"MmXxIi"`  | 2022   |

---

## Task 6: Roman Calculator

Build a simple calculator that can perform arithmetic on Roman numerals.

The calculator should:

- Accept expressions like `"X + V"` or `"XIV - III"`
- Support addition (`+`), subtraction (`-`), and multiplication (`*`)
- Return the result as a Roman numeral
- Handle results that go below 1 or above 3999 gracefully (Romans had no zero or negative numbers)

### Examples

| Input         | Output                    |
| ------------- | ------------------------- |
| `"X + V"`     | `"XV"`                    |
| `"XIV - III"` | `"XI"`                    |
| `"IV * III"`  | `"XII"`                   |
| `"C + L"`     | `"CL"`                    |
| `"MM + MM"`   | `"MMMM"`                  |
| `"V - X"`     | Error: result is negative |
| `"I - I"`     | Error: result is zero     |

---

## ⚠️ Task 7: Extended Notation (Stretch Goal)

_Note: This task is intentionally more than can be completed in the time available._

Implement the vinculum (overline) notation for large numbers. A bar over a numeral multiplies it by 1000:

- V̄ = 5,000
- X̄ = 10,000
- L̄ = 50,000
- C̄ = 100,000
- D̄ = 500,000
- M̄ = 1,000,000

For input, accept either Unicode overlined characters or a notation like `_X` or `X_` to represent X̄.

### Examples

| Input       | Output          |
| ----------- | --------------- |
| `"_V"`      | 5000            |
| `"_XMMXXV"` | 12025           |
| 5000        | `"V̄"` or `"_V"` |
| 1000000     | `"M̄"` or `"_M"` |

---

## Notes

- Standard Roman numerals can represent 1–3999 (I to MMMCMXCIX)
- The Romans didn't have a symbol for zero
- This exercise tests string parsing, pattern recognition, and validation logic
