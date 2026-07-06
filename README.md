# 🏠 Nashville Housing Data Cleaning using PostgreSQL

## Project Overview

This project focuses on cleaning and preparing the **Nashville Housing** dataset using **PostgreSQL**. The objective is to transform raw housing data into a clean, standardized dataset suitable for analysis and visualization.

The project demonstrates essential SQL data-cleaning techniques including handling missing values, standardizing data formats, splitting columns, removing duplicates, and dropping unnecessary columns.

---

## Dataset

- **Dataset:** Nashville Housing Data
- **Source:** Alex The Analyst SQL Data Cleaning Project
- **Records:** 56,000+ housing records

---

## Tools Used

- PostgreSQL 18
- pgAdmin 4
- SQL

---

## 📋 Data Cleaning Steps

### 1. Standardized Date Format
- Converted the `SaleDate` column to PostgreSQL `DATE` format.
- Created a new column:
  - `SaleDateConverted`

```sql
ALTER TABLE public.nashville_housing
ADD COLUMN SaleDateConverted DATE;
```

---

### 2. Populated Missing Property Addresses

Filled missing `PropertyAddress` values by matching records having the same `ParcelID`.

Used:

- Self Join
- COALESCE()

---

### 3. Split Property Address

Separated `PropertyAddress` into:

- PropertySplitAddress
- PropertySplitCity

Using PostgreSQL function:

```sql
SPLIT_PART()
```

---

### 4. Split Owner Address

Separated `OwnerAddress` into:

- OwnerSplitAddress
- OwnerSplitCity
- OwnerSplitState

---

### 5. Standardized SoldAsVacant Values

Converted:

| Original | Updated |
|----------|---------|
| Y | Yes |
| N | No |

Using a CASE statement.

---

### 6. Removed Duplicate Records

Used the `ROW_NUMBER()` window function to identify duplicate rows based on:

- ParcelID
- PropertyAddress
- SalePrice
- SaleDate
- LegalReference

Duplicates were removed while retaining the first occurrence.

---

### 7. Removed Unused Columns

Dropped unnecessary columns after cleaning, including:

- OwnerAddress
- PropertyAddress
- TaxDistrict
- SaleDate

---

## SQL Concepts Demonstrated

- Common Table Expressions (CTEs)
- Window Functions
- ROW_NUMBER()
- CASE Statements
- COALESCE()
- Self Joins
- UPDATE
- ALTER TABLE
- DROP COLUMN
- Data Type Conversion
- String Functions
- SPLIT_PART()
- TRIM()

---

## Project Outcome

After cleaning:

- Standardized date formats
- Missing property addresses populated
- Address fields split into separate columns
- Duplicate records removed
- Inconsistent categorical values standardized
- Unnecessary columns removed
- Dataset prepared for further analysis and visualization

---

## Sample Output

Example of cleaned address columns:

| PropertySplitAddress | PropertySplitCity |
|----------------------|-------------------|
| 1808 FOX CHASE DR | GOODLETTSVILLE |

Example of Owner Address split:

| OwnerSplitAddress | OwnerSplitCity | OwnerSplitState |
|-------------------|----------------|-----------------|
| 1808 FOX CHASE DR | GOODLETTSVILLE | TN |

---

## Skills Demonstrated

- SQL Data Cleaning
- PostgreSQL
- Data Transformation
- Data Wrangling
- Window Functions
- Database Management
- Data Preparation

---



---

⭐ If you found this project useful, consider giving the repository a star!
