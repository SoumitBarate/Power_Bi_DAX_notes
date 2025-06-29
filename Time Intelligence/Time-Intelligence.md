# ⏳ DAX Time Intelligence Notes

Welcome to the **Time Intelligence** section of my DAX and Power BI learning notes! These functions help analyze data over time — such as Year-to-Date totals, rolling averages, and comparing data to previous periods.

---

## 📅 Key Time Intelligence Functions

### 🔹 `DATESYTD(<dates>, [year_end_date])`
- Returns a table that contains a column of the dates from the beginning of the year to the latest date in the specified column.
- Useful for calculating Year-To-Date (YTD) values.
- **Example:**
  ```dax
  Sales YTD = CALCULATE(SUM(Sales[Amount]), DATESYTD(Date[Date]))

---

###🔹 TOTALYTD(<expression>, <dates>, [filter], [year_end_date])
Calculates the year-to-date value of the given expression.

Automatically filters dates and applies the aggregation.

Example:

dax
Copy
Edit
Sales Total YTD = TOTALYTD(SUM(Sales[Amount]), Date[Date])

### 🔹 SAMEPERIODLASTYEAR(<dates>)
Returns a table that contains a column of the dates from the same period in the previous year.

Useful for YoY (Year-over-Year) comparisons.

Example:

dax
Copy
Edit
Sales LY = CALCULATE(SUM(Sales[Amount]), SAMEPERIODLASTYEAR(Date[Date]))

### 🔁 Rolling Averages and Moving Totals
These techniques help smooth out short-term fluctuations and highlight longer-term trends.

### 🟠 7-Day Rolling Average
dax
Copy
Edit
7-Day Rolling Avg = 
AVERAGEX(
    DATESINPERIOD(Date[Date], LASTDATE(Date[Date]), -7, DAY),
    CALCULATE(SUM(Sales[Amount]))
)

### 🟠 3-Month Moving Total
dax
Copy
Edit
3-Month Moving Total = 
CALCULATE(
    SUM(Sales[Amount]),
    DATESINPERIOD(Date[Date], LASTDATE(Date[Date]), -3, MONTH)
)

### 📆 Custom Date Tables
To use Time Intelligence functions correctly, you must have a proper date table with a continuous range of dates.

---

### 🔹 Requirements:
One row per date

No missing dates

Mark as Date Table in Power BI

---

### 🔹 Creating a Date Table
Date = 
ADDCOLUMNS(
    CALENDAR(DATE(2020,1,1), DATE(2025,12,31)),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Quarter", "Q" & FORMAT([Date], "Q")
)

---

### 🔹 Mark as Date Table:
Go to Model View → right-click on the table → Mark as Date Table → select the date column.

---

### 📌 Summary
| Function               | Purpose                       |
| ---------------------- | ----------------------------- |
| `DATESYTD()`           | Returns YTD dates             |
| `TOTALYTD()`           | Calculates YTD total          |
| `SAMEPERIODLASTYEAR()` | Last year's same period dates |
| `DATESINPERIOD()`      | Used for rolling aggregations |
