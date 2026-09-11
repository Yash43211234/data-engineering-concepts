# Data Lake Architecture

## 1. Problem with Data Warehouse

Traditional Data Warehouse usually follows:

**Extract → Transform → Load (ETL) → Data Warehouse**

Before loading data, we need to:

* Define the schema
* Decide transformations
* Transform the data

### Problems

1. **High data volume** → difficult to transform everything fast.
2. **High data velocity** → data is generated faster than we can process it.
3. **Different data types** → structured, semi-structured, unstructured data.
4. **Higher cost**
5. **Vertical scaling has limits** → CPU, RAM and storage cannot increase forever.

---

# 2. Why Data Lake?

A Data Lake allows us to **store data first and transform it later**.

### Basic flow

**Source → Data Lake → Transform → Data Warehouse / BI**

Instead of:

**Source → Transform → Data Warehouse**

So, raw data can be stored immediately without waiting for transformation.

### Simple idea

> **Data Lake = Store first, process later.**

It can act as a **central dumping/storage area for raw data**.

---

# 3. Data Lake Storage

Common storage systems:

* Amazon S3
* Azure Blob Storage / ADLS
* HDFS

These support **horizontal scaling**.

### Horizontal vs Vertical Scaling

**Vertical Scaling**

* Increase the power of one machine.
* More CPU, RAM, storage.
* Has a hardware limit.

**Horizontal Scaling**

* Add more machines/servers.
* Combine them into a cluster.
* Can scale much further.

> Data Lake systems commonly use horizontally scalable storage.

---

# 4. Modern Data Lake Architecture

A modern Data Lake can be divided into layers:

**Source Systems**
→ **Ingestion Layer**
→ **Processing Layer**
→ **Processed/Consumer Layer**
→ **BI / Business Users**

### 1. Ingestion Layer

* Stores data in **raw form**.
* Data is kept almost as it arrives.
* Ingestion tools may add audit columns.

### 2. Processing Layer

* Data Engineers process and transform the raw data.
* Requires compute resources such as CPU and RAM.

### 3. Processed / Consumer Layer

* Contains cleaned and processed data.
* Business users/consumers get access here.
* Access is controlled for security.

### 4. Data Warehouse / Data Mart

* **Optional**
* Processed data can be moved here if the organization needs a traditional DW.
* BI tools can then use the DW.

Modern systems may also allow:

**Data Lake → BI directly**

without requiring a separate Data Warehouse.

---

# 5. Data Lake vs Data Warehouse

| Data Lake                                   | Data Warehouse                       |
| ------------------------------------------- | ------------------------------------ |
| Structured + Semi-structured + Unstructured | Mainly Structured                    |
| Schema-on-Read                              | Schema-on-Write                      |
| Store first, transform later                | Transform before storing             |
| ELT is common                               | ETL is common                        |
| Cheaper storage                             | More expensive                       |
| Horizontally scalable                       | Traditionally more vertically scaled |
| Good for raw/big data                       | Good for structured analytics        |
| Flexible                                    | More predefined/modelled             |

### Schema-on-Write

Schema is defined **before writing data**.

**Transform → Define schema → Write**

### Schema-on-Read

Data is stored first. Schema is applied **when reading/using the data**.

**Store → Read → Apply schema**

---

# 6. ETL vs ELT

### ETL

**Extract → Transform → Load**

Commonly associated with Data Warehouse.

### ELT

**Extract → Load → Transform**

Commonly used with Data Lake/cloud data platforms.

---

# 7. Interview Answer

### Why do we need a Data Lake?

> A Data Lake allows us to store large volumes of raw data from different sources without requiring a predefined schema or immediate transformation. It provides flexible and cost-effective storage and allows us to process the data later based on business requirements.

### Data Lake vs Data Warehouse — One Line

> **Data Lake is flexible and designed for storing large amounts of raw data, while Data Warehouse is structured and optimized for analytical queries and reporting.**

---

## Remember

**Data Warehouse:**

> Transform → Structure → Store → Analyze

**Data Lake:**

> Store → Process when needed → Analyze

**Most important reason Data Lake became popular:**
**Huge volume + high-speed data generation + variety of data.**
