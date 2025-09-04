<h2><sub><img src="https://github.com/RadhikaDeshpande1010/icon-library/blob/main/python-icon/python-icon.png" height="25" width="25"></sub> Python Practice Problems — Numbers & Conditionals </h2>
<img src="https://github.com/RadhikaDeshpande1010/Python-Conditions-and-If-statements/blob/main/If%20and%20Conditions.png">

A collection of beginner‑friendly Python exercises focused on numbers, loops, and conditional logic. Each problem includes a short description, inputs/outputs, and a clean, runnable solution.

> **Python version:** 3.8+

---

## How to Run

1. **Clone** this repository and open the folder in your editor/terminal.
2. Run any script directly with Python:

   ```bash
   python path/to/script.py
   ```
3. When prompted, enter the inputs shown in each example.

> Tip: You can also copy any solution function into your notebook/REPL to experiment quickly.

---

## Contents

* [Q1. Extract digits to a list (in order)](#q1-extract-digits-to-a-list-in-order)
* [Q2. Armstrong (Narcissistic) number check](#q2-armstrong-narcissistic-number-check)
* [Q3. Compare counts of even digits in two numbers](#q3-compare-counts-of-even-digits-in-two-numbers)
* [Q4. Unique digits sorted descending](#q4-unique-digits-sorted-descending)
* [Q5. Loan eligibility checker](#q5-loan-eligibility-checker)
* [Q6. Exam result evaluator](#q6-exam-result-evaluator)
* [Q7. Electricity bill calculator (tiered)](#q7-electricity-bill-calculator-tiered)
* [Q8. Sum only even digits](#q8-sum-only-even-digits)
* [Q9. Move all zeros to the end](#q9-move-all-zeros-to-the-end)
* [Q10. Income tax calculator (simplified)](#q10-income-tax-calculator-simplified)

---

## Q1. Extract digits to a list (in order)

**Input:** `78761`
**Output:** `[7, 8, 7, 6, 1]`

```python
# extract_digits.py

def digits_in_order(n: int) -> list[int]:
    if n == 0:
        return [0]
    out = []
    while n != 0:
        out.append(n % 10)
        n //= 10
    out.reverse()
    return out

if __name__ == "__main__":
    num = int(input("Enter a number: "))
    print(digits_in_order(num))
```

---

## Q2. Armstrong (Narcissistic) number check

**Task:** Check whether a number equals the sum of its own digits each raised to the power of the number of digits. (For `153`: `1^3 + 5^3 + 3^3 = 153`.)

```python
# armstrong_number.py

def is_armstrong(n: int) -> bool:
    s = str(n)
    p = len(s)
    return sum(int(ch) ** p for ch in s) == n

if __name__ == "__main__":
    num = int(input("Enter a number: "))
    print("Armstrong Number" if is_armstrong(num) else "Not an Armstrong Number")
```

> Your original code called this a **Corrosion number**; the standard term is **Armstrong** (or **Narcissistic**) number.

---

## Q3. Compare counts of even digits in two numbers

Count even **digits** (not whether the whole number is even) and compare.

```python
# compare_even_digit_counts.py

def even_digit_count(n: int) -> int:
    if n == 0:
        return 1  # digit '0' is even
    cnt = 0
    while n != 0:
        d = n % 10
        if d % 2 == 0:
            cnt += 1
        n //= 10
    return cnt

if __name__ == "__main__":
    a = int(input("Enter first number: "))
    b = int(input("Enter second number: "))
    c1, c2 = even_digit_count(a), even_digit_count(b)
    print("Even digits in first:", c1)
    print("Even digits in second:", c2)
    print("Even count is same" if c1 == c2 else "Even count is not same")
```

---

## Q4. Unique digits sorted descending

From a number, collect unique digits and print them in descending order.
**Example:** `787615641 → [8, 7, 6, 5, 4, 1, 0?]`

```python
# unique_sorted_digits_desc.py

def unique_desc_digits(n: int) -> list[int]:
    digits = set(int(ch) for ch in str(n))
    return sorted(digits, reverse=True)

if __name__ == "__main__":
    num = int(input("Enter a number: "))
    print(unique_desc_digits(num))
```

---

## Q5. Loan eligibility checker

**Rule:** Age ≥ 21, employed, and credit score > 650.

```python
# loan_eligibility.py

def parse_bool(s: str) -> bool:
    return s.strip().lower() in {"true", "t", "yes", "y", "1"}

def eligible(age: int, employed: bool, credit_score: int) -> bool:
    return age >= 21 and employed and credit_score > 650

if __name__ == "__main__":
    age = int(input("Enter Age: "))
    employed = parse_bool(input("Employed (true/false): "))
    score = int(input("Enter Credit Score: "))
    print("Eligible for Loan" if eligible(age, employed, score) else "Not Eligible for Loan")
```

---

## Q6. Exam result evaluator

**Pass if:** All three subjects ≥ 40 **and** average ≥ 50.

```python
# exam_result.py

def evaluate(s1: int, s2: int, s3: int) -> tuple[str, float]:
    avg = (s1 + s2 + s3) / 3
    ok = all(x >= 40 for x in (s1, s2, s3)) and avg >= 50
    return ("Pass", avg) if ok else ("Fail", avg)

if __name__ == "__main__":
    s1 = int(input("Subject 1: "))
    s2 = int(input("Subject 2: "))
    s3 = int(input("Subject 3: "))
    status, avg = evaluate(s1, s2, s3)
    print(status, "with average:", avg)
```

---

## Q7. Electricity bill calculator (tiered)

**Rates:**

* First 100 units → ₹1.5/unit
* Next 100 units → ₹2.5/unit (i.e., units 101–200)
* Above 200 units → ₹4/unit

```python
# electricity_bill.py

def bill(units: int) -> float:
    if units <= 0:
        return 0.0
    cost = 0.0
    slab = min(units, 100)
    cost += slab * 1.5
    units -= slab
    if units > 0:
        slab = min(units, 100)
        cost += slab * 2.5
        units -= slab
    if units > 0:
        cost += units * 4.0
    return cost

if __name__ == "__main__":
    u = int(input("Enter units: "))
    print(int(bill(u)) if bill(u).is_integer() else bill(u))
```

**Examples**

* 80 → `80 × 1.5 = 120`
* 170 → `100 × 1.5 + 70 × 2.5 = 325`
* 300 → `100 × 1.5 + 100 × 2.5 + 100 × 4 = 800`

---

## Q8. Sum only even digits

**Input:** `246135` → **Output:** `2+4+6 = 12`

```python
# sum_even_digits.py

def sum_even_digits(n: int) -> int:
    return sum(int(ch) for ch in str(n) if int(ch) % 2 == 0)

if __name__ == "__main__":
    num = int(input("Enter a number: "))
    print(sum_even_digits(num))
```

---

## Q9. Move all zeros to the end

Maintain the order of non‑zero elements.

```python
# move_zeroes.py

def move_zeroes(nums: list[int]) -> list[int]:
    write = 0
    for read in range(len(nums)):
        if nums[read] != 0:
            nums[write], nums[read] = nums[read], nums[write]
            write += 1
    return nums

if __name__ == "__main__":
    arr = [0, 1, 0, 3, 12]
    print(move_zeroes(arr))  # [1, 3, 12, 0, 0]
```

---

## Q10. Income tax calculator (simplified)

**Brackets:**

* Up to ₹2.5 lakh → **No tax**
* ₹2.5–5 lakh → **5%** (flat on total income for this exercise)
* ₹5–10 lakh → **20%**
* Above ₹10 lakh → **30%**

> Note: This is a **simplified** exercise, not a real tax computation.

```python
# income_tax.py

def simple_tax(income: int) -> int:
    if income <= 250_000:
        return 0
    elif income <= 500_000:
        return int(income * 0.05)
    elif income <= 1_000_000:
        return int(income * 0.20)
    else:
        return int(income * 0.30)

if __name__ == "__main__":
    inc = int(input("Annual income (₹): "))
    tax = simple_tax(inc)
    print("No Tax" if tax == 0 else tax)
```

---

## Conclusion

This repository gathers small, practical Python exercises to build confidence with numbers, loops, and conditional logic. Each problem can be run independently and serves as a step toward mastering core programming fundamentals.

