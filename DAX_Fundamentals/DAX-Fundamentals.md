# 🧠 DAX Fundamentals

Welcome to Day 1 of the DAX & Power BI Notes Series!  
In this module, you'll learn the basic building blocks of DAX, its syntax, and key foundational concepts like calculated columns, measures, and context types.

---

## 📌 What is DAX?

**DAX (Data Analysis Expressions)** is a formula language used in Power BI, Excel, and Analysis Services for data modeling and analysis.  
It allows users to create custom calculations, filters, aggregations, and KPIs.

---

## 🔤 Syntax and Structure

### ✅ Basic Rules:
- Formulas begin with an equal sign `=`
- Functions are case-insensitive but usually written in uppercase
- Arguments are passed inside parentheses `()` and separated by commas `,`

### ✅ Example:
Total Sales = SUM(Sales[Amount])

---

### ✅ Common DAX Functions:
Aggregation: SUM, AVERAGE, MAX, MIN, COUNT

Logical: IF, SWITCH, AND, OR

Text: LEFT, RIGHT, SEARCH, CONCATENATE

Date/Time: YEAR, MONTH, TODAY, NOW

---

### 🆚 Measures vs Calculated Columns

| Feature         | Measures                                | Calculated Columns                               |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| Evaluation Time | At query time                           | At data load time                                |
| Storage         | Not stored in the model                 | Stored in memory                                 |
| Performance     | More efficient                          | Can increase model size                          |
| Use Case        | Aggregation (e.g. total sales, average) | Row-level logic (e.g. category, flag)            |
| Example         | `Total = SUM(Sales[Amount])`            | `Category = IF(Sales[Amount]>1000,"High","Low")` |

---

### 🧠 Quick Summary:
| Context Type   | Applies To                    | Defined By                                   |
| -------------- | ----------------------------- | -------------------------------------------- |
| Row Context    | Calculated columns, iterators | Current row/record in evaluation             |
| Filter Context | Measures, visuals             | Filters from report visuals or `CALCULATE()` |

---

### Best Practices:
- Use measures instead of calculated columns when possible.
- Keep your data model clean and avoid unnecessary calculated columns.
- Understand context deeply — it changes how your formulas behave.
- Test your formulas with different filters to check results.

