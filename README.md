# Cambodia Administrative Queries - MLMUPC Data

SQL queries and examples built on top of the **Cambodia Administrative Codes Dataset**.

This repository is for working with query examples, lookups, and data exploration using the structured MLMUPC administrative dataset.

## What is MLMUPC?

**MLMUPC** = **Ministry of Land Management, Urban Planning and Construction** (Cambodian government ministry)

The administrative codes follow the official system established by MLMUPC and the Ministry of Interior.

---

## Overview

This project uses the data prepared in my companion repository:

**`mlmupc-administrative-codes`**

That dataset contains Cambodian administrative divisions in **Khmer** and **English**, organized by:

```text
Province / Capital
└── District / Municipality / Khan
    └── Commune / Sangkat
        └── Village
```

The source data was originally extracted from a public PDF and then cleaned and structured into reusable formats.

This repository focuses on the **query side** of that data, such as:

*   SQL practice
*   administrative lookups
*   hierarchy exploration
*   data validation
*   filtering by province, district, commune, or village
*   reusable database queries for applications

***

## Related Dataset Repository

This project uses data from:

**[mlmupc-administrative-codes](https://github.com/Sopheaktra34/mlmupc-administrative-codes)**

That repository contains:

*   `MLMUPC.csv` — structured CSV dataset
*   `MLMUPC.txt` — plain-text hierarchical dataset

The dataset includes these fields:

*   `code`
*   `level`
*   `name_kh`
*   `name_en`
*   `parent_code`

***

## Purpose of This Repository

This repository is intended to store and organize queries for working with Cambodian administrative division data.

Examples of what this repository can be used for:

*   list all provinces
*   list districts under a province
*   list communes under a district
*   list villages under a commune
*   search by Khmer name
*   search by English name
*   validate hierarchical codes
*   count records by level
*   build API or application lookup logic
*   support dropdown selectors in apps

***

## Example Use Cases

### Administrative Lookup

Find all children of a given parent code.

### Data Validation

Check whether all villages belong to a valid commune and district.

### Search

Query by:

*   Khmer name
*   English transliteration
*   administrative code
*   administrative level

### Application Support

Useful for:

*   location dropdowns
*   registration systems
*   address forms
*   GIS tools
*   data integration pipelines

***

## Data Model

The queries in this repository are based on the following structure:

```text
Province
 └── District / City / Khan
      └── Commune / Sangkat
           └── Village
```

Example code flow:

```text
01         → Province
0102       → District
010201     → Commune
01020101   → Village
```

***

## Example Query Ideas

This repository may include queries such as:

### 1. Get all provinces

```sql
SELECT * FROM provinces;
```

### 2. Get all districts in a province

```sql
SELECT *
FROM districts
WHERE province_code = '01';
```

### 3. Get all communes in a district

```sql
SELECT *
FROM communes
WHERE district_code = '0102';
```

### 4. Get all villages in a commune

```sql
SELECT *
FROM villages
WHERE commune_code = '010201';
```

### 5. Count records by level

```sql
SELECT level, COUNT(*) AS total
FROM mlmupc
GROUP BY level;
```

> Adjust table names to match your own database schema.

***

## Repository Structure

The current repository is organized as follows:

```text
.
├── cambodia_admin_codes.sql    # Database schema
├── database_connection.py      # Database connection utilities
├── api_server.py              # FastAPI server application
├── admin_queries.py            # Administrative query functions
├── static/
│   ├── admin_interface.html    # Web interface
│   └── admin_lookup.js         # Frontend JavaScript
├── images/                     # Screenshots and demo images
│   ├── Screenshot 2026-04-09 145732.png
│   ├── Screenshot 2026-04-09 145747.png
│   ├── Screenshot 2026-04-09 145800.png
│   └── Screenshot 2026-04-09 145950.png
└── README.md
```

***

## Screenshots

The `images/` directory contains screenshots demonstrating the administrative lookup functionality:

### Administrative Interface
![Administrative Interface](images/Screenshot%202026-04-09%20145732.png)

### Province Selection
![Province Selection](images/Screenshot%202026-04-09%20145747.png)

### District Lookup Results
![District Lookup](images/Screenshot%202026-04-09%20145800.png)

### Commune and Village Query
![Commune Village Query](images/Screenshot%202026-04-09%20145950.png)

These screenshots show the web interface in action, demonstrating the cascading dropdown functionality for browsing Cambodia's administrative hierarchy.

***

## Important Note

This repository is **not an official government repository**.

The data used here comes from a **personally prepared OCR/text extraction and restructuring workflow** based on a public source document.

This query repository is intended for:

*   learning
*   development
*   experimentation
*   practical reuse
*   administrative data exploration

***

## Data Quality Note

Because the source material originally came from a PDF and required OCR/text extraction, some records may still contain:

*   OCR mistakes
*   transliteration inconsistencies
*   formatting issues
*   spacing or punctuation artifacts

Please validate carefully before using the data in production systems.

***

## Attribution

If you reuse this work, please consider acknowledging:

*   the original ODC-hosted public source document
*   the companion dataset repository
*   that the structured data was personally extracted and prepared for easier reuse

Suggested attribution:

> Based on a public ODC-hosted PDF of Inter-ministerial Prakas no. 052 on Cambodian administrative identification codes. Query repository built on a personally prepared OCR-extracted and structured dataset.

***

## Contributing

Contributions are welcome.

Possible improvements include:

*   better SQL query organization
*   more useful lookup queries
*   validation queries
*   performance improvements
*   query examples for MySQL / PostgreSQL
*   search and filtering enhancements

***
## Disclaimer

This repository is a practical query workspace built on a community-prepared extraction of public administrative data.

It is provided for convenience and learning purposes, and should not be considered a legally authoritative replacement for the original official publication.