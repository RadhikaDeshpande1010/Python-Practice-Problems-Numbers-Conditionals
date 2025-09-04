<h2><sub><img src="https://github.com/RadhikaDeshpande1010/icon-library/blob/main/python-icon/python-icon.png" height="25" width="25"></sub> Python Practice Problems — Numbers & Conditionals </h2>
<img src="https://github.com/RadhikaDeshpande1010/Python-Practice-Problems-Numbers-Conditionals/blob/main/Numbers-Conditionals.png">

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

rem = 0
list1=[]
while num1 != 0:
    rem = num1 % 10
    list1.append(rem)
    num1 = num1//10
list1.reverse()
print(list1)
num1 = 5

Output:
[7, 8, 7, 6, 1]
```

---

## Q2. Armstrong (Narcissistic) number check

**Task:** Check whether a number equals the sum of its own digits each raised to the power of the number of digits. (For `153`: `1^3 + 5^3 + 3^3 = 153`.)

```python
# armstrong_number.py

num1 = 153
sum = 0
num2 = num1
while num1 != 0:
    rem = num1 % 10
    sum = sum + (rem**3)
    num1 = num1//10
print(sum)
if sum == num2:
    print("Armstrong Number")
else:
    print("Not an Armstrong Number")

Output:
Armstrong Number
```

> Your original code called this a **Corrosion number**; the standard term is **Armstrong** (or **Narcissistic**) number.

---

## Q3. Compare counts of even digits in two numbers

Count even **digits** (not whether the whole number is even) and compare.

```python
# compare_even_digit_counts.py

num1 = 567
num2 = 234
even_count = 0
even_count1 = 0
while num1 != 0:
    if num1 % 2 == 0:
        even_count = even_count + 1
    num1 = num1//10
while num2 != 0:
    if num2 % 2 == 0:
        even_count1 = even_count1 + 1
    num2 = num2//10
print("even count for num1: ",even_count)
print("even count for num2: ",even_count1)

if even_count == even_count1:
    print("Even count is same")
else:
    print("Even count is not same")

Output:
even count for num1:  1
even count for num2:  2
Even count is not same
```

---

## Q4. Unique digits sorted descending

From a number, collect unique digits and print them in descending order.
**Example:** `787615641 → [8, 7, 6, 5, 4, 1, 0?]`

```python
# unique_sorted_digits_desc.py

num1 = 787615641
coun1 = 0
list1 = []
while num1 != 0:
    rem = num1 % 10 # 1
    list1.append(rem)
    num1 = num1 // 10
print(list1)
list2 = []
for i in list1:
    if i not in list2:
        list2.append(i)
list2.sort(reverse=True)
print(list2)

Output:
[1, 4, 6, 5, 1, 6, 7, 8, 7]
[8, 7, 6, 5, 4, 1]
```

---

## Q5. Loan eligibility checker

**Rule:** 
**Age:** `≥ 21`
**Employed:** `boolean`
**Credit Score:** `> 650`.

```python
# loan_eligibility.py

age = int(input("Enter Age: "))
employed = input("Enter Empolyed: ")
credit_score = int(input("Enter Credit Score: "))
if (age > 21 and employed == 'true' and credit_score > 650):
    print("Person is eligible for loan")
else:
    print("Person is not eligible for loan")

User Input:
Enter Age:  26
Enter Empolyed:  true
Enter Credit Score:  670

Output:
Person is eligible for loan
```

---

## Q6. Exam result evaluator

**Pass if:** `All three subjects ≥ 40` **and** `average ≥ 50`.

```python
# exam_result.py

subject1 = int(input("Enter marks of subject1: "))
subject2 = int(input("Enter marks of subject2: "))
subject3 = int(input("Enter marks of subject3: "))
average = 0
if subject1 >= 40 and subject2 >= 40 and subject3 >= 40:
    average = (subject1 + subject2 + subject3) / 3
    print("Student is passed with average marks of: ",average)
else:
    print("Student is failed with average marks of: ",average)

User Input:
Enter marks of subject1:  45
Enter marks of subject2:  62
Enter marks of subject3:  58

Output:
Student is passed with average marks of:  55.0
```

---

## Q7. Electricity bill calculator (tiered)

**Rates:**

* First 100 units → ₹1.5/unit
* Next 100 units → ₹2.5/unit (i.e., units 101–200)
* Above 200 units → ₹4/unit

```python
# electricity_bill.py

units = int(input("Enter the units:"))
if units > 0 and units <= 100:
    result = units * 1.5
    print(int(result))
if units > 100 and units <= 200:
    result = units - 100
    price = (100*1.5) + result * 2.5
    print(price) 
else:
    result = units - 200
    price = (100*1.5) + (100*2.5) + result * 4
    print("Total electricity bill is:",price)

User Input:
Enter the units: 450

Output:
Total electricity bill is: 1400.0
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

num = 246135
str1 = str(num)
sum = 0
for i in str1:
    if (int(i) % 2 == 0):
        sum = sum + int(i)
print(sum)

Output:
12
```

---

## Q9. Move all zeros to the end

Maintain the order of non‑zero elements.

```python
ls = [0, 1, 0, 3, 12]
ls1 = []
ls2 = []
for i in ls:
    if i == 0:
        ls1.append(i)
    else:
        ls2.append(i)
print(ls1)
print(ls2)
print(ls2 + ls1)

Output:
[0, 0]
[1, 3, 12]
[1, 3, 12, 0, 0]
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

price = int(input("Annual Income:"))
if price > 0 and price <= 250000:
    print("No Tax")
elif price > 250000 and price <= 500000:
    tax = price * 0.05
    print(int(tax))
elif price > 500000 and price <= 1000000:
    tax = price * 0.2
    print(int(tax))
else:
    tax = price * 0.3
    print(int(tax))

User Input:
Annual Income: 400000

Output:
20000
```

---

## Conclusion

This repository gathers small, practical Python exercises to build confidence with numbers, loops, and conditional logic. Each problem can be run independently and serves as a step toward mastering core programming fundamentals.

