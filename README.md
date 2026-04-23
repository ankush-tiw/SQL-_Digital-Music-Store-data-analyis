# 🎵 Digital Music Store Data Analysis (SQL)

## 📌 Project Overview
This project involves a deep-dive exploratory data analysis (EDA) of a digital music store's database using **PostgreSQL**. The goal of this project is to answer business-critical questions regarding customer behavior, sales trends, and inventory performance to help the store optimize its growth strategy.

## 🛠️ Tech Stack
* **Database Engine:** PostgreSQL
* **Tools Used:** pgAdmin 4 / DBeaver / VS Code
* **Core Skills Applied:** Advanced Joins, Common Table Expressions (CTEs), Window Functions (`ROW_NUMBER()`), Data Type Casting, Data Cleaning, and Schema Normalization.

## 🗂️ The Dataset
The project is built on a normalized relational database schema (similar to the Chinook dataset) representing a digital media store. It includes information about:
* **Employees & Customers:** Demographics and reporting hierarchies.
* **Invoices & Invoices Lines:** Transactional sales data, billing countries, and unit prices.
* **Tracks, Albums, & Artists:** Product inventory and hierarchy.
* **Genres & Media Types:** Categorization of the music tracks.

# 🎵 Digital Music Store Data Analysis (SQL)

## 📌 Project Overview
This project involves a deep-dive exploratory data analysis (EDA) of a digital music store's database using **PostgreSQL**. The goal of this project is to answer business-critical questions regarding customer behavior, sales trends, and inventory performance to help the store optimize its growth strategy.

## 🛠️ Tech Stack
* **Database Engine:** PostgreSQL
* **Tools Used:** pgAdmin 4 / DBeaver / VS Code
* **Core Skills Applied:** Advanced Joins, Common Table Expressions (CTEs), Window Functions (`ROW_NUMBER()`), Data Type Casting, Data Cleaning, and Schema Normalization.

## 🗂️ The Dataset
The project is built on a normalized relational database schema (similar to the Chinook dataset) representing a digital media store. It includes information about:
* **Employees & Customers:** Demographics and reporting hierarchies.
* **Invoices & Invoices Lines:** Transactional sales data, billing countries, and unit prices.
* **Tracks, Albums, & Artists:** Product inventory and hierarchy.
* **Playlists:** Custom track collections and their associations.
* **Genres & Media Types:** Categorization of the music tracks.

### Database Schema
The database consists of the following primary tables:
`customer` | `employee` | `invoice` | `invoice_line` | `track` | `album` | `artist` | `genre` | `media_type` | `playlist` | `playlist_track`

---

## 🧹 Data Cleaning & Schema Normalization
Real-world data is rarely perfect. A significant portion of this project involved cleaning the imported data and fixing schema relationships to ensure query accuracy and performance.

* **Data Type Normalization:** The raw data was initially imported with generic `VARCHAR` text types. I executed a global database cleanup script to strictly type the schema:
  * Casted all Primary/Foreign Keys (`invoice_id`, `track_id`, `customer_id`, etc.) from `VARCHAR` to `INTEGER`.
  * Fixed junction tables (like `playlist_track`) to ensure both `playlist_id` and `track_id` mapped strictly to integers, allowing for flawless many-to-many joins.
  * Converted monetary columns (`unit_price`) to `NUMERIC(10,2)` to allow for accurate mathematical aggregations (`SUM`, `AVG`).
* **Data Integrity:** Resolved operator mismatch errors to ensure seamless `JOIN` operations across all 11 tables.

---

## 📊 Key Business Questions Answered

During the analysis, I wrote complex SQL queries to answer the following business questions:

1. **Who is the senior-most employee based on job title?**
2. **Which countries have the most invoices?**
3. **What are the top 3 values of total invoices?**
4. **Which city has the best customers?** (Identifying the city that generated the highest revenue to host a promotional Music Festival).
5. **Who is the best customer?** (The customer who has spent the most money).
6. **Which rock music listeners have the longest track times?**
7. **Who are the top-selling artists?** 8. **What is the most popular music genre in each country?** (Utilized CTEs and `ROW_NUMBER()` Window Functions to partition sales by country).

*(Note: You can view the actual SQL scripts and solutions in the `queries.sql` file in this repository).*

---

## 💡 Key Insights & Learnings
* **Window Functions are powerful:** Using `ROW_NUMBER() OVER(PARTITION BY ...)` was essential for pulling top categories per region without writing overly complex nested subqueries.
* **Strict Typing is crucial:** Attempting to `JOIN` text strings to integers or multiply strings by numbers will crash a pipeline. Setting up the `CREATE TABLE` schema correctly *before* importing CSV data saves hours of debugging.
* **CTE Readability:** Using `WITH` clauses (CTEs) significantly improved the readability of multi-step queries compared to traditional subqueries.

## 🚀 How to Run This Project
1. Clone this repository to your local machine.
2. Set up a local PostgreSQL server.
3. Run the `schema_setup.sql` file to create the tables with the correct data types.
4. Import the provided `.csv` files into their respective tables.
5. Run the queries in `analysis_queries.sql` to view the insights.
2. Set up a local PostgreSQL server.
3. Run the `schema_setup.sql` file to create the tables with the correct data types.
4. Import the provided `.csv` files into their respective tables.
5. Run the queries in `analysis_queries.sql` to view the insights.
