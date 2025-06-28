# 📅 Time Intelligence in DAX – Power BI Notes

This section explains how to work with **Time Intelligence functions** in DAX for Power BI. These are essential for building insightful reports that deal with trends over time — such as **year-to-date**, **rolling averages**, and **comparing current and previous years**.

---

## 🔧 Key Time Intelligence Functions

### ✅ `DATESYTD()`

- Returns a **set of dates** from the beginning of the year to the latest date in the current context.
- **Syntax**:
  ```dax
  DATESYTD(<dates>, [year_end_date])

Example:-
TOTAL_SALES_YTD = CALCULATE(SUM(Sales[Amount]), DATESYTD(Date[Date]))

---

### ✅ TOTALYTD()
Calculates the year-to-date value of an expression using a date column.

Wrapper around CALCULATE() + DATESYTD().

Syntax:

dax
Copy
Edit
TOTALYTD(<expression>, <dates>, [filter], [year_end_date])
Example:

dax
Copy
Edit
SALES_YTD = TOTALYTD(SUM(Sales[Amount]), Date[Date])

---

### ✅ SAMEPERIODLASTYEAR()
Returns a date column shifted back exactly one year, keeping the same period length.

Syntax:

dax
Copy
Edit
SAMEPERIODLASTYEAR(<dates>)
Example:

dax
Copy
Edit
SALES_LAST_YEAR = CALCULATE(SUM(Sales[Amount]), SAMEPERIODLASTYEAR(Date[Date]))

---

### 🔁 Rolling Averages and Moving Totals
✅ 3-Month Rolling Average
dax
Copy
Edit
Rolling_3_Month_Avg = 
AVERAGEX(
    DATESINPERIOD(Date[Date], MAX(Date[Date]), -3, MONTH),
    CALCULATE(SUM(Sales[Amount]))
)

---

### ✅ 6-Month Moving Total
dax
Copy
Edit
Rolling_6_Month_Total = 
CALCULATE(
    SUM(Sales[Amount]),
    DATESINPERIOD(Date[Date], MAX(Date[Date]), -6, MONTH)
)
These are helpful to identify trends while reducing short-term fluctuations.

---

### 📆 Custom Date Tables
To use Time Intelligence functions properly, create a custom Date Table that:

Covers the full date range with no gaps.

Is marked as a Date Table in Power BI.

Contains extra columns like Year, Month, Quarter for filtering.

Example Date Table
dax
Copy
Edit
DateTable = 
ADDCOLUMNS(
    CALENDAR(DATE(2015, 1, 1), DATE(2025, 12, 31)),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month", FORMAT([Date], "MMMM"),
    "Quarter", "Q" & FORMAT([Date], "Q")
)
✅ Remember to mark the table as a Date Table under Model View → Mark as Date Table.

---

### 🧠 Tips
Always create relationships between your custom Date Table and Fact Table using the Date column.

Avoid using auto date/time hierarchies from Power BI — use your custom Date Table instead.

---

### 📂 Related DAX Functions
DATEADD()

PARALLELPERIOD()

FIRSTDATE(), LASTDATE()

PREVIOUSYEAR(), NEXTYEAR()

---

### 📘 Summary
| Function               | Purpose                                 |
| ---------------------- | --------------------------------------- |
| `DATESYTD()`           | Gets YTD date range                     |
| `TOTALYTD()`           | Calculates YTD total                    |
| `SAMEPERIODLASTYEAR()` | Compare with same period last year      |
| `DATESINPERIOD()`      | Helps with rolling calculations         |
| `CALCULATE()`          | Core function to apply filters like YTD |
