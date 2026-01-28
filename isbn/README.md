# ISBN Validator

Validate and work with ISBN (International Standard Book Number) codes.

They have a feature where the last digit is a 'check' digit calculated from the preceding digits. Its useful for error detection (e.g., typos, incorrect scans, etc).

In this task you will implement functions to validate ISBN-10 and ISBN-13 codes, convert between them, and optionally look up book information via an API.

## Task 1: Validate ISBN-10

Write a function that validates an ISBN-10 number.

An ISBN-10 consists of 10 digits (the last digit can be 'X' representing 10).

### Validation Algorithm

1. Multiply each of the first 9 digits by its position (1-9)
2. Sum all the products
3. The check digit (10th character) should make the total divisible by 11

**Formula:** `(1×d₁ + 2×d₂ + 3×d₃ + ... + 9×d₉ + 10×d₁₀) mod 11 = 0`

### Examples

**Valid ISBN-10: `0306406152`**

```
(1×0) + (2×3) + (3×0) + (4×6) + (5×4) + (6×0) + (7×6) + (8×1) + (9×5) + (10×2)
= 0 + 6 + 0 + 24 + 20 + 0 + 42 + 8 + 45 + 20
= 165
165 mod 11 = 0 ✓
```

| Input          | Valid? |
| -------------- | ------ |
| `"0306406152"` | true   |
| `"0471958697"` | true   |
| `"080442957X"` | true   |
| `"0306406153"` | false  |
| `"1234567890"` | false  |

---

## Task 2: Handle Formatting

Extend your validator to accept ISBN-10s with hyphens or spaces.

ISBNs are often formatted with separators to show the group, publisher, and title portions.

### Examples

| Input             | Valid? |
| ----------------- | ------ |
| `"0-306-40615-2"` | true   |
| `"0 306 40615 2"` | true   |
| `"0-471-95869-7"` | true   |
| `"0-8044-2957-X"` | true   |
| `"0-306-40615-3"` | false  |

Also handle:

- Mixed separators (`"0-306 40615-2"`)
- Leading/trailing whitespace
- Lowercase 'x' for check digit

---

## Task 3: Validate ISBN-13

Write a function that validates an ISBN-13 number.

ISBN-13 uses a different algorithm:

### Validation Algorithm

1. Multiply digits at odd positions (1st, 3rd, 5th, etc.) by 1
2. Multiply digits at even positions (2nd, 4th, 6th, etc.) by 3
3. Sum all products
4. The result should be divisible by 10

**Formula:** `(d₁ + 3×d₂ + d₃ + 3×d₄ + ... + d₁₃) mod 10 = 0`

### Examples

**Valid ISBN-13: `9780306406157`**

```
9 + (3×7) + 8 + (3×0) + 3 + (3×0) + 6 + (3×4) + 0 + (3×6) + 1 + (3×5) + 7
= 9 + 21 + 8 + 0 + 3 + 0 + 6 + 12 + 0 + 18 + 1 + 15 + 7
= 100
100 mod 10 = 0 ✓
```

| Input                 | Valid? |
| --------------------- | ------ |
| `"9780306406157"`     | true   |
| `"978-0-306-40615-7"` | true   |
| `"9780470059029"`     | true   |
| `"9780306406158"`     | false  |

---

## Task 4: Auto-Detect ISBN Type

Write a unified validation function that:

- Automatically detects whether the input is ISBN-10 or ISBN-13
- Validates using the appropriate algorithm
- Returns an object/dictionary with the type and validity

### Examples

| Input                 | Result                              |
| --------------------- | ----------------------------------- |
| `"0306406152"`        | `{ type: "ISBN-10", valid: true }`  |
| `"9780306406157"`     | `{ type: "ISBN-13", valid: true }`  |
| `"978-0-306-40615-7"` | `{ type: "ISBN-13", valid: true }`  |
| `"0306406153"`        | `{ type: "ISBN-10", valid: false }` |
| `"12345"`             | `{ type: "unknown", valid: false }` |

---

## Task 5: Convert ISBN-10 to ISBN-13

Write a function to convert a valid ISBN-10 to ISBN-13.

### Conversion Rules

1. Remove the ISBN-10 check digit
2. Prepend `978`
3. Calculate the new ISBN-13 check digit

### Examples

| ISBN-10        | ISBN-13           |
| -------------- | ----------------- |
| `"0306406152"` | `"9780306406157"` |
| `"0471958697"` | `"9780471958697"` |
| `"080442957X"` | `"9780804429573"` |

If the input ISBN-10 is invalid, throw an error.

---

## Task 6: Calculate Check Digits

Write functions to calculate the correct check digit for an incomplete ISBN.

Given the first 9 digits of an ISBN-10 or first 12 digits of an ISBN-13, return the complete valid ISBN.

### Examples

| Input (incomplete) | Output (complete) |
| ------------------ | ----------------- |
| `"030640615"`      | `"0306406152"`    |
| `"047195869"`      | `"0471958697"`    |
| `"008044295"`      | `"008044295X"`    |
| `"978030640615"`   | `"9780306406157"` |
| `"978047095802"`   | `"9780470958025"` |

---

## ⚠️ Task 7: Book Lookup API (Stretch Goal)

_Note: This task is intentionally more than can be completed in the time available._

Integrate with the Open Library API to look up book information from an ISBN.

**API Endpoint:** `https://openlibrary.org/api/books?bibkeys=ISBN:{isbn}&format=json&jscmd=data`

### Function Requirements

Given a valid ISBN, return:

- Title
- Author(s)
- Publisher
- Publication year
- Cover image URL (if available)

### Examples

**Input:** `"9780140449136"`

**Output:**

```json
{
  "title": "The Brothers Karamazov",
  "authors": ["Fyodor Dostoevsky"],
  "publisher": "Penguin Classics",
  "year": 2003,
  "cover": "https://covers.openlibrary.org/b/id/8231856-L.jpg"
}
```

Handle:

- Invalid ISBNs (validate before lookup)
- ISBNs not found in the database
- API errors/timeouts

---

## ⚠️ Task 8: ISBN CLI Tool (Stretch Goal)

_Note: This task is intentionally more than can be completed in the time available._

Build a command-line tool that:

- Validates ISBNs from arguments or stdin
- Converts between ISBN-10 and ISBN-13
- Looks up book information
- Batch processes multiple ISBNs from a file

### Example Usage

```bash
$ isbn validate 9780306406157
✓ Valid ISBN-13

$ isbn validate 0306406152
✓ Valid ISBN-10

$ isbn convert 0306406152
ISBN-10: 0306406152 → ISBN-13: 9780306406157

$ isbn lookup 9780140449136
Title: The Brothers Karamazov
Author: Fyodor Dostoevsky
Publisher: Penguin Classics (2003)

$ isbn batch books.txt
Processing 50 ISBNs...
✓ 47 valid
✗ 3 invalid (lines 12, 28, 41)
```

---

## Notes

- ISBN-10 was the standard until 2007; ISBN-13 (starting with 978 or 979) is now used
- 'X' only appears as a check digit in ISBN-10, never in ISBN-13
- This exercise tests string manipulation, modular arithmetic, and API integration
- The `979` prefix ISBNs (ISBN-A) cannot be converted back to ISBN-10
