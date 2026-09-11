# Data Mart

## 1. What is Data Mart?

**Data Mart = A focused subset of data designed for a specific business area or department.**

Examples:

* HR Data Mart
* Sales Data Mart
* Finance Data Mart
* Marketing Data Mart

### Simple idea

**Data Warehouse → Data Mart → Business/BI**

A Data Mart contains only the data needed by a particular department or business use case.

---

## 2. Why Do We Need Data Mart?

Without Data Mart:

**BI → Data Warehouse → Find required data**

With Data Mart:

**BI → Specific Data Mart → Get required data**

### Benefits

* **Faster queries** → less data to scan.
* **Department-focused** → only required data.
* **Better security** → departments can access only their data.
* **More control** → unnecessary columns/data can be removed.
* **Smaller data size** → often contains summarized/filtered data.

Example:

A Sales Data Mart may contain **sales by product, store, month**, instead of billions of detailed records.

---

# 3. Data Mart Characteristics

* Highly **subject/department specific**
* Usually a **subset of Data Warehouse**
* Can contain a **specific time period**

  * DW → 10 years
  * Data Mart → last 1–2 years
* Often contains **summarized data**
* Faster query performance
* Better departmental data security
* Uses **dimensional modeling** (Fact + Dimension tables)

---

# 4. Disadvantages

* Additional system to build and maintain.
* Additional ETL/ELT pipelines.
* Data may be duplicated across multiple Data Marts.
* More storage may be required.
* Multiple Data Marts can increase maintenance complexity.

---

# 5. Simple Analogy

Think of:

**Source System → Supplier**

**Data Warehouse → Wholesaler**

**Data Mart → Retailer**

The Data Warehouse contains a large amount of data, while Data Marts provide **focused data to specific users/departments**.

> This is only an analogy, not an exact architecture.

---

# 6. Types of Data Mart

There are two common types:

### 1. Dependent Data Mart

**Source → Data Warehouse → Data Mart**

The Data Mart depends on the Data Warehouse.

If the Data Warehouse doesn't exist, this Data Mart cannot be created from it.

> **No Data Warehouse → No Dependent Data Mart**

### 2. Independent Data Mart

**Source → Data Mart**

There is **no Data Warehouse** in between.

Data is directly extracted from source systems and loaded into the Data Mart.

**Source → ETL → Data Mart**

---

# 7. Independent Data Mart vs Data Warehouse

The difference can be blurry.

| Data Warehouse         | Independent Data Mart           |
| ---------------------- | ------------------------------- |
| Broader business scope | Specific business/subject scope |
| More data sources      | Usually fewer data sources      |
| Larger volume          | Small to medium volume          |
| Enterprise-wide        | Department/use-case focused     |
| Dimensional modeling   | Dimensional modeling            |
| ETL is commonly used   | ETL is commonly used            |

The main difference is **scope**.

---

# 8. Data Warehouse vs Data Mart

**Data Warehouse**

> Central, enterprise-level data store for multiple business areas.

**Data Mart**

> Smaller, focused data store for a specific department or business requirement.

### Example

```text
                 Data Warehouse
                       |
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
    Sales DM        HR DM        Finance DM
        ↓              ↓              ↓
    Sales Team      HR Team      Finance Team
```

---

# 9. Interview Questions

### What is a Data Mart?

> A Data Mart is a focused subset of data designed for a specific department, subject area, or business use case.

### Why do we need a Data Mart?

> To provide focused, secure, and faster access to the data required by a particular department or business use case.

### Types of Data Mart?

> Dependent Data Mart and Independent Data Mart.

### When do we use Data Warehouse vs Data Mart?

**Data Warehouse:**
When multiple departments need a centralized enterprise-wide view of data.

**Data Mart:**
When a specific department or business area needs focused and optimized data.

---

## Remember

**Data Warehouse = Whole business**

**Data Mart = Specific part of the business**

**Dependent:**
`Source → DW → Data Mart`

**Independent:**
`Source → Data Mart`
