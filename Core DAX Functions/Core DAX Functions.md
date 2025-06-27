# 🔧 Core DAX Functions

Welcome to **Day 2** of the DAX & Power BI Notes Series!  
In this module, we'll explore essential DAX functions that form the foundation of most data modeling logic — from modifying filter context to performing advanced aggregations.

---

## 📌 Key Functions Covered

- `CALCULATE()`, `FILTER()`, `ALL()`, `VALUES()`
- Logical and conditional functions: `IF()`, `SWITCH()`
- Iterative aggregation: `SUMX()`, `AVERAGEX()`, `COUNTROWS()`

---

## 🧠 1. CALCULATE()

**`CALCULATE()`** modifies the filter context of an expression.

### ✅ Syntax:
CALCULATE(<expression>, <filter1>, <filter2>, ...)

✅ Example:
Total Sales 2023 = CALCULATE(SUM(Sales[Amount]), YEAR(Sales[Date]) = 2023)
✅ Why it’s powerful:
Changes or adds filters on-the-fly
Enables time intelligence, dynamic measures, conditional logic

---

### 🔍 2. FILTER()
FILTER() returns a table with rows that meet a condition. Often used inside CALCULATE().

✅ Syntax:
dax
Copy
Edit
FILTER(<table>, <condition>)
✅ Example:
dax
Copy
Edit
High Value Sales = CALCULATE(SUM(Sales[Amount]), FILTER(Sales, Sales[Amount] > 1000))
ℹ️ FILTER() allows row-by-row filtering and is more flexible than a simple filter argument.

---

# 🚫 3. ALL()
ALL() removes filters from a table or column.

✅ Syntax:
dax
Copy
Edit
ALL(<table or column>)
✅ Example:
dax
Copy
Edit
% of Total Sales = 
DIVIDE(
    SUM(Sales[Amount]),
    CALCULATE(SUM(Sales[Amount]), ALL(Sales))
)
✅ Use Cases:
Calculate grand totals

Reset slicer or visual filters

---

### 📋 4. VALUES()
VALUES() returns a unique list of values in a column.

✅ Syntax:
dax
Copy
Edit
VALUES(<column>)
✅ Example:
dax
Copy
Edit
Customer List = VALUES(Customers[CustomerID])
✅ Use Cases:
Use in CALCULATE() for context manipulation

Common with DISTINCTCOUNT() and slicer-based calculations

---

### 🔗 Logical & Conditional Functions
🔹 IF()
dax
Copy
Edit
IF(Sales[Amount] > 1000, "High", "Low")
Classic logical test

Use for flagging, categorization, condition-based logic

🔹 SWITCH()
dax
Copy
Edit
SWITCH(
    TRUE(),
    Sales[Amount] < 500, "Low",
    Sales[Amount] < 1000, "Medium",
    "High"
)
Alternative to nested IF()

Cleaner and easier to maintain

---

### ♻️ Iteration & Aggregation Functions
These iterate over rows and apply custom logic.

🔸 SUMX()
dax
Copy
Edit
SUMX(Sales, Sales[Quantity] * Sales[UnitPrice])
Row-by-row multiplication + summation

Great for calculated totals

🔸 AVERAGEX()
dax
Copy
Edit
AVERAGEX(Products, Products[Cost])
Returns average over a custom expression

🔸 COUNTROWS()
dax
Copy
Edit
CALCULATE(COUNTROWS(Sales), Sales[Amount] > 1000)
Count rows based on filter or expression

⚠️ X functions like SUMX() create row context internally.

---

🛠 Best Practices
✅ Use CALCULATE() for powerful, dynamic calculations.

✅ Use simple filters where possible; use FILTER() only when needed.

✅ Use ALL() carefully — it overrides slicers/filters.

✅ Use SWITCH() over nested IF() for clarity.

✅ Use X functions (SUMX, AVERAGEX) only when custom row-based logic is required.
