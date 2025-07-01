# 📊 Power BI Techniques

Welcome to the **Power BI Techniques** notes — a curated set of advanced concepts to improve your Power BI reports and dashboards. This guide is ideal for analysts, developers, and learners seeking to build efficient, scalable, and interactive Power BI solutions.

---

## 🧠 Contents

1. [Optimizing Data Models](#-optimizing-data-models)
2. [Working with Relationships and Cardinality](#-working-with-relationships-and-cardinality)
3. [Creating Dynamic Visuals with DAX](#-creating-dynamic-visuals-with-dax)
4. [Best Practices for Dashboards](#-best-practices-for-dashboards)

---

## 🔧 Optimizing Data Models

- Use **Star Schema** instead of snowflake for better performance.
- Remove **unnecessary columns and tables** to reduce model size.
- Rename columns and tables with meaningful names for clarity.
- Use **numeric** or **whole number keys** for relationships over strings.
- Set proper **data types** (date, text, decimal, etc.).
- Use **Power Query** to do heavy data transformation, not DAX.
- Turn off **Auto Date/Time** under Options → Data Load for better performance.

---

## 🔗 Working with Relationships and Cardinality

- Prefer **Single Direction** relationships unless required otherwise.
- Understand **Cardinality**:
  - **One-to-Many (1:\*)**: Most common and preferred.
  - **Many-to-Many (\*:\*)**: Use only when necessary with caution.
- Avoid circular or ambiguous relationships.
- Use **COMPOSITE MODE** to mix Import and DirectQuery for flexibility.
- Check and fix **inactive relationships** (gray dotted lines in the model view).
- Use `USERELATIONSHIP()` DAX when multiple relationships exist.

---

## 📈 Creating Dynamic Visuals with DAX

- **Measure branching**: Define base measures first, then build on them.
- Use `SELECTEDVALUE()` to detect slicer selection.
- Use `SWITCH(TRUE(), ...)` pattern for dynamic logic.
- Create **dynamic titles** using DAX:


Title = "Sales Report for " & SELECTEDVALUE(Region[RegionName], "All Regions")

---

### 📊 Best Practices for Dashboards
Start with a clear business question.

Maintain a consistent color theme and font.

Use tooltips, bookmarks, and drill-throughs for interactivity.

Avoid overcrowding visuals — use whitespace wisely.

Use KPI cards, bar/column charts, and slicers smartly.

Always test performance using Performance Analyzer in Power BI Desktop.

Ensure mobile layout is optimized.

---

### 🚀 Recommended Resources
Microsoft Power BI Docs

DAX Guide

SQLBI Articles
