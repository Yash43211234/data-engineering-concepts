# Data Warehouse — Basic Concepts

## 1. What is a Data Warehouse?

A **Data Warehouse (DW)** is a central place where data from different sources is collected and stored for **analysis and reporting**.

### Simple Example

A company may have:

* Sales data → Sales Database
* Employee data → HR Database
* Customer data → CRM
* Marketing data → Files/APIs

A Data Warehouse brings this data together so the company can analyze everything in one place.

> **Interview:** A Data Warehouse is a central system that integrates data from multiple sources and is mainly used for analytics and reporting.

---

# 2. Data Warehouse vs Database

| Data Warehouse                                         | Database                           |
| ------------------------------------------------------ | ---------------------------------- |
| Mainly used for analysis                               | Mainly used for daily transactions |
| Handles large volumes of data                          | Usually handles operational data   |
| More **read-heavy**                                    | More **read/write-heavy**          |
| Historical data is important                           | Current data is more important     |
| Queries can be complex                                 | Queries are usually smaller/faster |
| Often uses column-based storage                        | Usually uses row-based storage     |
| Some data duplication is acceptable for faster queries | Data is usually highly normalized  |

### Example

**Database:**
UPI payment → money transfer → account update

The response must be very fast.

**Data Warehouse:**
"How much did we sell in the last 5 years?"

This may involve a large amount of data and complex queries.

---

# 3. Why is Data Warehouse Read-Heavy?

A Data Warehouse is mainly used for:

* `SELECT`
* Aggregations
* Reports
* Dashboards
* Business analysis

Example:

```sql
SELECT
    month,
    SUM(sales)
FROM sales
GROUP BY month;
```

So, the design focuses more on **fast reading and analysis** than frequent updates.

---

# 4. Data Warehouse and Columnar Storage

Data Warehouses commonly use **columnar storage**.

Examples:

* Parquet
* ORC

If a query needs only:

```text
customer_id
sales
```

the system can read mainly those columns instead of reading the complete row.

This can make analytical queries faster.

---

# 5. Why Data Warehouse Can Have Some Redundancy?

In a normal database, we try to avoid duplicate data.

In a Data Warehouse, some duplication can be acceptable because it can:

* Reduce the number of joins
* Make queries simpler
* Improve analytical query performance

> **Simple idea:**
> Database → reduce duplication
> Data Warehouse → some duplication is acceptable for faster analysis

---

# 6. OLTP vs OLAP

### OLTP — Online Transaction Processing

Used for **daily business transactions**.

Examples:

* UPI payment
* Placing an order
* Updating customer information

Usually uses operational databases.

### OLAP — Online Analytical Processing

Used for **analysis and reporting**.

Examples:

* Monthly sales analysis
* Customer trends
* Yearly revenue
* Business dashboards

Usually uses Data Warehouse systems.

> **Remember:**
> **OLTP → Transactions**
> **OLAP → Analysis**

---

# 7. Data Warehouse vs Spark

Both can process large amounts of data, but their main purposes are different.

### Spark

Spark is a **general-purpose distributed processing engine**.

It can work with:

* Structured data
* Semi-structured data
* Unstructured data
* Batch processing
* Streaming
* ML/AI workloads

### Data Warehouse

A Data Warehouse is mainly designed for:

* Structured data
* Analytics
* Reporting
* SQL queries
* Business intelligence

### Simple Comparison

| Spark                          | Data Warehouse                 |
| ------------------------------ | ------------------------------ |
| General-purpose processing     | Mainly analytics               |
| Batch + Streaming              | Mainly analytical workloads    |
| Structured + semi/unstructured | Mainly structured              |
| Supports ML/AI workloads       | Mainly BI/analytics            |
| More flexible                  | Easier for SQL-based analytics |

> **Interview:** Spark and Data Warehouse are not direct replacements. Spark is a processing engine, while a Data Warehouse is an analytical data platform. In real systems, they can be used together.

---

# 8. Examples of Data Warehouse

Popular Data Warehouse solutions:

* Snowflake
* Amazon Redshift
* Teradata
* Google BigQuery
* Azure Synapse Analytics

---

# 9. Rules / Characteristics of a Data Warehouse

A Data Warehouse generally has four important characteristics:

## 1. Integrated

Data comes from **multiple sources** and is brought together.

```text
Database ──┐
Database ──┤
Files ─────┼──> Data Warehouse
API ───────┘
```

> **Integrated = Data from different sources in one place**

---

## 2. Subject-Oriented

Data is organized around important **business subjects**.

Examples:

* Sales
* Customers
* Employees
* Products
* Marketing

> **Subject-oriented = Focus on business areas**

---

## 3. Time-Variant

A Data Warehouse stores **historical data**.

Example:

```text
2024 Sales
2025 Sales
2026 Sales
```

This allows us to compare data over time.

> **Time-variant = Historical data matters**

---

## 4. Non-Volatile

Once data is loaded into the Data Warehouse, it is generally **not frequently changed like an operational database**.

The main activity is:

```text
Load data → Store → Analyze
```

rather than continuously updating individual records.

> **Non-volatile = Data is relatively stable after loading**

---

# Quick Interview Revision

### Data Warehouse

> A central system that collects data from multiple sources and stores it for analysis and reporting.

### Database

> Mainly used for day-to-day transactions and fast reads/writes.

### OLTP

> Used for daily transactions.

### OLAP

> Used for analysis and reporting.

### Integrated

> Data from multiple sources is combined.

### Subject-Oriented

> Data is organized around business subjects.

### Time-Variant

> Historical data is maintained.

### Non-Volatile

> Data is relatively stable after it is loaded.

### Spark vs Data Warehouse

> Spark is a distributed processing engine; a Data Warehouse is an analytical data platform. They can work together.
