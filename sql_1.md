Name - Harshal Patil
Roll No. - 26271002

SQL PRACTICE SET – RETAIL EVENTS DATASET
20 QUESTIONS | EASY → MEDIUM → HARD

DATASET OVERVIEW
================

This practice set uses the retail_events_db database.

Main tables:

1. dim_campaigns
   - campaign_id
   - campaign_name
   - start_date
   - end_date

2. dim_products
   - product_code
   - product_name
   - category

3. dim_stores
   - store_id
   - city

4. fact_events
   - event_id
   - store_id
   - campaign_id
   - product_code
   - base_price
   - promo_type
   - quantity_sold(before_promo)
   - quantity_sold(after_promo)

The fact_events table stores product-level promotional event information.
Use the dimension tables to obtain campaign, product and store details.

IMPORTANT:
- Use MySQL syntax.
- Column names containing parentheses may need backticks.
  Example:
  `quantity_sold(before_promo)`
  `quantity_sold(after_promo)`
- Do not modify the data.
- Write a separate SQL query for each question.
- Questions are arranged from easy to hard.
- Focus especially on JOINs, GROUP BY, HAVING, CASE, CTEs and window functions.

============================================================
EASY QUESTIONS
============================================================

Q1. Basic Filtering – High-Value Products
Find all event records where the base_price is greater than 1,000.

Display:
- event_id
- store_id
- product_code
- base_price
- promo_type

Concepts:
SELECT, WHERE, comparison operators.

Query - 
use `retail_events_db`;

-- Q1 
SELECT event_id, 
	store_id, 
    product_code, 
    base_price,
    promo_type 
FROM fact_events 
where base_price > 1000;

Query Answer - 

| event_id | store_id | product_code | base_price | promo_type |
|---|---|---|---|---|
| a1503f | STCBE-1 | P15 | 3000 | 500 Cashback |
| 6b2afc | STCBE-4 | P08 | 1190 | BOGOF |
| 8f25a6 | STHYD-6 | P15 | 3000 | 500 Cashback |
| 0f422c | STBLR-0 | P14 | 1020 | BOGOF |
| 7fc923 | STTRV-0 | P08 | 1190 | BOGOF |
| ca7298 | STCBE-2 | P15 | 3000 | 500 Cashback |
| bf33ae | STMYS-0 | P14 | 1020 | BOGOF |
| 4f0587 | STMDU-0 | P08 | 1190 | BOGOF |
| fa5b45 | STVJD-1 | P08 | 1190 | BOGOF |
| 7e9777 | STVJD-1 | P08 | 1190 | BOGOF |
| 761785 | STBLR-4 | P14 | 1020 | BOGOF |
| eb3bea | STVSK-2 | P15 | 3000 | 500 Cashback |
| 627200 | STCBE-4 | P14 | 1020 | BOGOF |
| c8ce63 | STMDU-0 | P15 | 3000 | 500 Cashback |
| 57a7bc | STHYD-5 | P14 | 1020 | BOGOF |
| 70e65e | STCBE-0 | P15 | 3000 | 500 Cashback |
| 32efe6 | STVSK-3 | P08 | 1190 | BOGOF |
| d834f0 | STMYS-3 | P08 | 1190 | BOGOF |
| 268ca2 | STVJD-0 | P15 | 3000 | 500 Cashback |
| 1548f8 | STVSK-4 | P15 | 3000 | 500 Cashback |
| 873333 | STMLR-0 | P15 | 3000 | 500 Cashback |
| f856b9 | STMLR-2 | P15 | 3000 | 500 Cashback |
| b00eeb | STCHE-0 | P08 | 1190 | BOGOF |
| 6436da | STMDU-1 | P08 | 1190 | BOGOF |
| 57576d | STBLR-5 | P08 | 1190 | BOGOF |
| 582098 | STMYS-1 | P14 | 1020 | BOGOF |
| 71a7a0 | STCHE-6 | P14 | 1020 | BOGOF |
| fd2628 | STBLR-8 | P15 | 3000 | 500 Cashback |
| 7b187a | STVSK-1 | P14 | 1020 | BOGOF |
| 345b49 | STMDU-2 | P14 | 1020 | BOGOF |
| c381ea | STMLR-1 | P08 | 1190 | BOGOF |
| a0d919 | STMDU-1 | P08 | 1190 | BOGOF |
| ff18f2 | STVSK-3 | P15 | 3000 | 500 Cashback |
| cf734f | STHYD-4 | P08 | 1190 | BOGOF |
| 413f48 | STVSK-0 | P14 | 1020 | BOGOF |
| 8cbaa3 | STHYD-2 | P08 | 1190 | BOGOF |
| 34a266 | STMLR-0 | P08 | 1190 | BOGOF |
| 7014a8 | STBLR-8 | P14 | 1020 | BOGOF |
| 61b929 | STVSK-2 | P14 | 1020 | BOGOF |
| e39703 | STBLR-9 | P08 | 1190 | BOGOF |
| d2b963 | STVJD-0 | P14 | 1020 | BOGOF |
| 2e3393 | STCHE-3 | P14 | 1020 | BOGOF |
| 4b3df6 | STTRV-1 | P14 | 1020 | BOGOF |
| ca1e8f | STHYD-1 | P08 | 1190 | BOGOF |
| e8aca2 | STCBE-4 | P08 | 1190 | BOGOF |
| c8670a | STCHE-0 | P15 | 3000 | 500 Cashback |
| c99d18 | STCHE-7 | P08 | 1190 | BOGOF |
| 5b357f | STMDU-1 | P15 | 3000 | 500 Cashback |
| c48008 | STBLR-2 | P14 | 1020 | BOGOF |
| 4f255c | STHYD-1 | P08 | 1190 | BOGOF |
| a37f93 | STVSK-3 | P14 | 1020 | BOGOF |
| 38b760 | STMDU-0 | P14 | 1020 | BOGOF |
| 9.57E+11 | STHYD-1 | P15 | 3000 | 500 Cashback |
| 5aa413 | STCHE-1 | P08 | 1190 | BOGOF |
| 6c7601 | STCBE-2 | P14 | 1020 | BOGOF |
| 14f1e9 | STBLR-4 | P08 | 1190 | BOGOF |
| 1f5ed3 | STVSK-1 | P08 | 1190 | BOGOF |
| 8b1147 | STVSK-0 | P15 | 3000 | 500 Cashback |
| 5f0a89 | STBLR-3 | P15 | 3000 | 500 Cashback |
| f1b7e9 | STCHE-3 | P14 | 1020 | BOGOF |
| 333b7d | STHYD-6 | P08 | 1190 | BOGOF |
| 2b0db4 | STMLR-2 | P14 | 1020 | BOGOF |
| 6.88E+10 | STVJD-0 | P08 | 1190 | BOGOF |
| 41b8f8 | STBLR-0 | P08 | 1190 | BOGOF |
| a9ee19 | STBLR-1 | P08 | 1190 | BOGOF |
| a55960 | STBLR-1 | P08 | 1190 | BOGOF |
| 6f3e24 | STHYD-6 | P15 | 3000 | 500 Cashback |
| 79a95a | STHYD-3 | P15 | 3000 | 500 Cashback |
| 27bc6e | STCBE-2 | P14 | 1020 | BOGOF |
| fc376a | STHYD-0 | P14 | 1020 | BOGOF |
| d6ff76 | STMDU-2 | P14 | 1020 | BOGOF |
| 6a1a5a | STVSK-0 | P15 | 3000 | 500 Cashback |
| 361cfb | STMLR-0 | P14 | 1020 | BOGOF |
| e7bdad | STMLR-1 | P14 | 1020 | BOGOF |
| aac58d | STBLR-6 | P08 | 1190 | BOGOF |
| c1cdb5 | STCHE-0 | P15 | 3000 | 500 Cashback |
| b44f0e | STHYD-2 | P15 | 3000 | 500 Cashback |
| 99482c | STBLR-8 | P08 | 1190 | BOGOF |
| f98db5 | STBLR-2 | P15 | 3000 | 500 Cashback |
| f8e037 | STHYD-2 | P08 | 1190 | BOGOF |
| 2db607 | STCBE-1 | P14 | 1020 | BOGOF |
| b78191 | STBLR-3 | P14 | 1020 | BOGOF |
| 7b1d41 | STMYS-2 | P14 | 1020 | BOGOF |
| d78c78 | STCHE-0 | P14 | 1020 | BOGOF |
| 17537 | STMDU-2 | P08 | 1190 | BOGOF |
| 9.33E+11 | STBLR-3 | P08 | 1190 | BOGOF |
| 5f2c41 | STCHE-6 | P08 | 1190 | BOGOF |
| 66050c | STCHE-6 | P08 | 1190 | BOGOF |
| e12c11 | STCHE-1 | P14 | 1020 | BOGOF |
| 177b80 | STMLR-0 | P14 | 1020 | BOGOF |
| ef6d6d | STBLR-2 | P14 | 1020 | BOGOF |
| c55ec9 | STBLR-1 | P15 | 3000 | 500 Cashback |
| 6bbadf | STHYD-1 | P14 | 1020 | BOGOF |
| d3f755 | STCBE-1 | P08 | 1190 | BOGOF |
| 911349 | STHYD-0 | P15 | 3000 | 500 Cashback |
| 3c3c49 | STCBE-2 | P08 | 1190 | BOGOF |
| 6a7668 | STCHE-4 | P15 | 3000 | 500 Cashback |
| c5f80e | STCHE-1 | P14 | 1020 | BOGOF |
| 3.56E+10 | STMDU-3 | P08 | 1190 | BOGOF |
| 17df71 | STHYD-0 | P08 | 1190 | BOGOF |
| 342d35 | STCBE-3 | P08 | 1190 | BOGOF |
| d8f51c | STMYS-1 | P15 | 3000 | 500 Cashback |
| d88318 | STCHE-5 | P08 | 1190 | BOGOF |
| 333ef0 | STHYD-0 | P14 | 1020 | BOGOF |
| 5a6ad7 | STBLR-9 | P14 | 1020 | BOGOF |
| c3c9e3 | STVSK-1 | P15 | 3000 | 500 Cashback |
| 95792f | STMDU-2 | P15 | 3000 | 500 Cashback |
| fc2170 | STCBE-3 | P08 | 1190 | BOGOF |
| 1d651c | STCHE-5 | P15 | 3000 | 500 Cashback |
| 06c981 | STHYD-2 | P14 | 1020 | BOGOF |
| 6c1493 | STVJD-1 | P15 | 3000 | 500 Cashback |
| 4f7c26 | STCBE-4 | P15 | 3000 | 500 Cashback |
| c4dae9 | STHYD-0 | P08 | 1190 | BOGOF |
| c1debe | STCHE-3 | P15 | 3000 | 500 Cashback |
| 5c6465 | STHYD-5 | P08 | 1190 | BOGOF |
| 335090 | STMYS-0 | P15 | 3000 | 500 Cashback |
| fc8d10 | STMLR-0 | P08 | 1190 | BOGOF |
| 8d5095 | STCBE-2 | P15 | 3000 | 500 Cashback |
| efd0d2 | STMYS-2 | P15 | 3000 | 500 Cashback |
| 4ca177 | STVSK-4 | P14 | 1020 | BOGOF |
| fa1dd3 | STCHE-3 | P15 | 3000 | 500 Cashback |
| 4ff977 | STVSK-4 | P15 | 3000 | 500 Cashback |
| f8b215 | STBLR-4 | P14 | 1020 | BOGOF |
| 9d9a6c | STCBE-1 | P15 | 3000 | 500 Cashback |
| e2f806 | STMDU-1 | P14 | 1020 | BOGOF |
| 221da2 | STCBE-3 | P15 | 3000 | 500 Cashback |
| e98f37 | STBLR-3 | P08 | 1190 | BOGOF |
| 716a3b | STCHE-5 | P14 | 1020 | BOGOF |
| c32fcd | STHYD-3 | P08 | 1190 | BOGOF |
| 26a18a | STVSK-3 | P15 | 3000 | 500 Cashback |
| d3d574 | STMLR-2 | P08 | 1190 | BOGOF |
| 9d3d1f | STCHE-6 | P15 | 3000 | 500 Cashback |
| 7d9576 | STBLR-7 | P15 | 3000 | 500 Cashback |
| 59f792 | STCHE-4 | P15 | 3000 | 500 Cashback |
| 86206 | STHYD-1 | P14 | 1020 | BOGOF |
| 457639 | STCHE-4 | P08 | 1190 | BOGOF |
| 420258 | STVSK-3 | P14 | 1020 | BOGOF |
| 642b50 | STMYS-1 | P14 | 1020 | BOGOF |
| eb967c | STMYS-1 | P15 | 3000 | 500 Cashback |
| 417902 | STMDU-0 | P08 | 1190 | BOGOF |
| 380a4f | STCHE-1 | P08 | 1190 | BOGOF |
| 8c13bb | STBLR-5 | P08 | 1190 | BOGOF |
| d70dcb | STCBE-4 | P15 | 3000 | 500 Cashback |
| 49057f | STHYD-0 | P15 | 3000 | 500 Cashback |
| ac0b1c | STMYS-3 | P14 | 1020 | BOGOF |
| e5db3d | STCBE-0 | P08 | 1190 | BOGOF |
| 0c0926 | STMDU-3 | P08 | 1190 | BOGOF |
| 1f0eaf | STBLR-6 | P15 | 3000 | 500 Cashback |
| 95f061 | STMYS-3 | P15 | 3000 | 500 Cashback |
| 4ca50a | STHYD-3 | P08 | 1190 | BOGOF |
| d3d442 | STBLR-5 | P15 | 3000 | 500 Cashback |
| cf0ccd | STVSK-1 | P08 | 1190 | BOGOF |
| 68c31e | STBLR-7 | P08 | 1190 | BOGOF |
| 4b411a | STVJD-0 | P15 | 3000 | 500 Cashback |
| 7.83E+87 | STMDU-3 | P14 | 1020 | BOGOF |
| 6a1564 | STMDU-3 | P15 | 3000 | 500 Cashback |
| 1cfaa8 | STBLR-2 | P08 | 1190 | BOGOF |
| e74698 | STBLR-5 | P14 | 1020 | BOGOF |
| ce3c11 | STHYD-4 | P14 | 1020 | BOGOF |
| 6.20E+94 | STMYS-0 | P08 | 1190 | BOGOF |
| 3080c6 | STVSK-4 | P14 | 1020 | BOGOF |
| 8a219d | STBLR-8 | P08 | 1190 | BOGOF |
| 0690d9 | STHYD-3 | P15 | 3000 | 500 Cashback |
| c7f28c | STBLR-0 | P15 | 3000 | 500 Cashback |
| 8f9cc5 | STMLR-1 | P08 | 1190 | BOGOF |
| 608271 | STMDU-0 | P15 | 3000 | 500 Cashback |
| e2f6b2 | STCHE-1 | P15 | 3000 | 500 Cashback |
| 2b8abd | STCHE-2 | P14 | 1020 | BOGOF |
| d58c29 | STVSK-2 | P08 | 1190 | BOGOF |
| 5.00E+300 | STVJD-1 | P14 | 1020 | BOGOF |
| 3d8361 | STMYS-1 | P08 | 1190 | BOGOF |
| 9fcb92 | STMDU-2 | P15 | 3000 | 500 Cashback |
| d0356d | STCHE-0 | P08 | 1190 | BOGOF |
| 60170c | STHYD-4 | P08 | 1190 | BOGOF |
| e7769b | STHYD-5 | P15 | 3000 | 500 Cashback |
| 4a42f9 | STBLR-7 | P08 | 1190 | BOGOF |
| 686a37 | STBLR-0 | P14 | 1020 | BOGOF |
| c16abb | STCHE-7 | P08 | 1190 | BOGOF |
| ef7122 | STMLR-1 | P15 | 3000 | 500 Cashback |
| 8.31E+08 | STCBE-2 | P08 | 1190 | BOGOF |
| 0894b7 | STCHE-3 | P08 | 1190 | BOGOF |
| e23132 | STVJD-0 | P08 | 1190 | BOGOF |
| d76198 | STCHE-4 | P08 | 1190 | BOGOF |
| e2c229 | STTRV-1 | P15 | 3000 | 500 Cashback |
| 171bbb | STTRV-0 | P15 | 3000 | 500 Cashback |
| cb43c4 | STCHE-0 | P14 | 1020 | BOGOF |
| c95efb | STBLR-7 | P15 | 3000 | 500 Cashback |
| f9d2c6 | STBLR-9 | P14 | 1020 | BOGOF |
| 0b38d9 | STMYS-3 | P08 | 1190 | BOGOF |
| f013a9 | STMYS-2 | P14 | 1020 | BOGOF |
| f41256 | STMLR-1 | P15 | 3000 | 500 Cashback |
| f94f2f | STTRV-1 | P08 | 1190 | BOGOF |
| 802b3c | STBLR-1 | P15 | 3000 | 500 Cashback |
| bea96f | STVSK-2 | P14 | 1020 | BOGOF |
| b7f012 | STMYS-2 | P15 | 3000 | 500 Cashback |
| a9d059 | STCHE-7 | P14 | 1020 | BOGOF |
| 1c7c7f | STBLR-8 | P14 | 1020 | BOGOF |
| cfeac1 | STHYD-6 | P14 | 1020 | BOGOF |
| 8e6e77 | STBLR-0 | P08 | 1190 | BOGOF |
| 63a2d2 | STCHE-3 | P08 | 1190 | BOGOF |
| 5947fb | STBLR-9 | P15 | 3000 | 500 Cashback |
| eb4f04 | STMLR-0 | P15 | 3000 | 500 Cashback |
| c4006c | STCBE-3 | P15 | 3000 | 500 Cashback |
| 8e1636 | STBLR-4 | P15 | 3000 | 500 Cashback |
| fe1a8b | STBLR-8 | P15 | 3000 | 500 Cashback |
| 0312a8 | STCHE-7 | P15 | 3000 | 500 Cashback |
| d0daaa | STMDU-1 | P14 | 1020 | BOGOF |
| 75f30e | STCHE-2 | P15 | 3000 | 500 Cashback |
| 7b49ce | STVJD-1 | P15 | 3000 | 500 Cashback |
| 4858ab | STBLR-7 | P14 | 1020 | BOGOF |
| bf49bf | STCHE-4 | P14 | 1020 | BOGOF |
| 5bc324 | STTRV-1 | P14 | 1020 | BOGOF |
| c3b511 | STCBE-3 | P14 | 1020 | BOGOF |
| de6e7e | STVSK-1 | P15 | 3000 | 500 Cashback |
| bb83e5 | STMDU-2 | P08 | 1190 | BOGOF |
| be3489 | STHYD-3 | P14 | 1020 | BOGOF |
| a6276f | STCHE-4 | P14 | 1020 | BOGOF |
| da99ec | STCHE-5 | P14 | 1020 | BOGOF |
| 9c2c14 | STVSK-0 | P14 | 1020 | BOGOF |
| 29411f | STBLR-6 | P08 | 1190 | BOGOF |
| 918a17 | STVSK-1 | P14 | 1020 | BOGOF |
| 7d89b1 | STVSK-3 | P08 | 1190 | BOGOF |
| e96e9d | STHYD-1 | P15 | 3000 | 500 Cashback |
| 6a7fa1 | STVJD-1 | P14 | 1020 | BOGOF |
| fc7056 | STBLR-2 | P08 | 1190 | BOGOF |
| 092c09 | STHYD-5 | P08 | 1190 | BOGOF |
| 2b50e0 | STBLR-6 | P15 | 3000 | 500 Cashback |
| 4ad12b | STBLR-4 | P15 | 3000 | 500 Cashback |
| 6ec0eb | STCHE-2 | P15 | 3000 | 500 Cashback |
| deea3e | STMLR-1 | P14 | 1020 | BOGOF |
| 35e1c7 | STBLR-1 | P14 | 1020 | BOGOF |
| fd5855 | STVSK-4 | P08 | 1190 | BOGOF |
| 30bacd | STBLR-3 | P14 | 1020 | BOGOF |
| c3b647 | STCHE-5 | P08 | 1190 | BOGOF |
| 9d63a7 | STHYD-6 | P08 | 1190 | BOGOF |
| 9fae1c | STHYD-2 | P15 | 3000 | 500 Cashback |
| 7cf0d8 | STMDU-0 | P14 | 1020 | BOGOF |
| fc9ab7 | STCBE-1 | P08 | 1190 | BOGOF |
| cf6323 | STTRV-0 | P15 | 3000 | 500 Cashback |
| 4f75fe | STMYS-2 | P08 | 1190 | BOGOF |
| ee68d9 | STCHE-1 | P15 | 3000 | 500 Cashback |
| e411c6 | STHYD-4 | P15 | 3000 | 500 Cashback |
| 49706e | STMDU-3 | P15 | 3000 | 500 Cashback |
| 40baa1 | STCBE-0 | P08 | 1190 | BOGOF |
| 0e96b4 | STCBE-4 | P14 | 1020 | BOGOF |
| 3ea7d6 | STMYS-0 | P15 | 3000 | 500 Cashback |
| fb508c | STBLR-9 | P15 | 3000 | 500 Cashback |
| 33da9a | STHYD-5 | P14 | 1020 | BOGOF |
| 7c8fd1 | STMYS-3 | P15 | 3000 | 500 Cashback |
| 4cd232 | STVJD-0 | P14 | 1020 | BOGOF |
| 496b80 | STHYD-4 | P15 | 3000 | 500 Cashback |
| 5.23E+42 | STCHE-5 | P15 | 3000 | 500 Cashback |
| 3adeb2 | STMYS-0 | P14 | 1020 | BOGOF |
| a40872 | STBLR-7 | P14 | 1020 | BOGOF |
| 5dda21 | STCBE-0 | P14 | 1020 | BOGOF |
| 349c73 | STCHE-2 | P14 | 1020 | BOGOF |
| 6af3e0 | STBLR-6 | P14 | 1020 | BOGOF |
| 6b74c8 | STBLR-5 | P15 | 3000 | 500 Cashback |
| 691b63 | STCHE-6 | P15 | 3000 | 500 Cashback |
| 8cee6d | STCBE-3 | P14 | 1020 | BOGOF |
| 6d153f | STHYD-5 | P15 | 3000 | 500 Cashback |
| adf52a | STBLR-6 | P14 | 1020 | BOGOF |
| 4fc1b2 | STCHE-2 | P08 | 1190 | BOGOF |
| 69a3d2 | STTRV-1 | P08 | 1190 | BOGOF |
| 886ef2 | STMLR-2 | P08 | 1190 | BOGOF |
| a937e8 | STMDU-3 | P14 | 1020 | BOGOF |
| e2c5f7 | STTRV-0 | P08 | 1190 | BOGOF |
| bb77b1 | STMYS-3 | P14 | 1020 | BOGOF |
| 583386 | STBLR-9 | P08 | 1190 | BOGOF |
| 48d526 | STCHE-7 | P15 | 3000 | 500 Cashback |
| 716abd | STMYS-1 | P08 | 1190 | BOGOF |
| e17280 | STVSK-2 | P08 | 1190 | BOGOF |
| 108d5a | STCBE-0 | P14 | 1020 | BOGOF |
| 613571 | STTRV-1 | P15 | 3000 | 500 Cashback |
| 34395c | STBLR-0 | P15 | 3000 | 500 Cashback |
| d134e0 | STBLR-3 | P15 | 3000 | 500 Cashback |
| fc3573 | STMYS-2 | P08 | 1190 | BOGOF |
| 85e08f | STVSK-4 | P08 | 1190 | BOGOF |
| 73f158 | STHYD-2 | P14 | 1020 | BOGOF |
| 141aea | STCHE-7 | P14 | 1020 | BOGOF |
| 6562df | STCBE-1 | P14 | 1020 | BOGOF |
| 536fbf | STMLR-2 | P15 | 3000 | 500 Cashback |
| 021d48 | STMLR-2 | P14 | 1020 | BOGOF |
| 80be79 | STBLR-4 | P08 | 1190 | BOGOF |
| 879d9a | STBLR-2 | P15 | 3000 | 500 Cashback |
| dc23bb | STVSK-0 | P08 | 1190 | BOGOF |
| 87bb82 | STCBE-0 | P15 | 3000 | 500 Cashback |
| 7641 | STBLR-1 | P14 | 1020 | BOGOF |
| 4236be | STTRV-0 | P14 | 1020 | BOGOF |
| a617b5 | STHYD-4 | P14 | 1020 | BOGOF |
| 7bb8ed | STCHE-2 | P08 | 1190 | BOGOF |
| 1130ea | STHYD-6 | P14 | 1020 | BOGOF |
| 35418e | STTRV-0 | P14 | 1020 | BOGOF |
| 59effd | STBLR-5 | P14 | 1020 | BOGOF |
| a42141 | STMDU-1 | P15 | 3000 | 500 Cashback |
| fb2c04 | STVSK-0 | P08 | 1190 | BOGOF |
| 04f19c | STMYS-0 | P08 | 1190 | BOGOF |
| 3bcf8b | STCHE-6 | P14 | 1020 | BOGOF |
| ffb109 | STVSK-2 | P15 | 3000 | 500 Cashback |
| 11578 | STHYD-3 | P14 | 1020 | BOGOF |


---

Q2. Sorting Promotional Events
Display all events where quantity sold after the promotion was greater than 100.

Display:
- event_id
- product_code
- promo_type
- quantity_sold(before_promo)
- quantity_sold(after_promo)

Sort by quantity_sold(after_promo) in descending order.

Concepts:
WHERE, ORDER BY, DESC.

Query - 
-- Q2
SELECT event_id, 
product_code, 
promo_type, 
`quantity_sold(before_promo)`, 
`quantity_sold(after_promo)`
FROM fact_events 
where `quantity_sold(after_promo)` > 100
order by `quantity_sold(after_promo)` DESC;

Query Answer - 
| event_id | product_code | promo_type | quantity_sold(before_promo) | quantity_sold(after_promo) |
|---|---|---|---|---|
| e93b62 | P04 | BOGOF | 513 | 2067 |
| 1a1a02 | P04 | BOGOF | 465 | 2064 |
| fe94ae | P04 | BOGOF | 450 | 1984 |
| 4eb35e | P04 | BOGOF | 483 | 1907 |
| fe7b5d | P03 | BOGOF | 472 | 1902 |
| 0efde2 | P03 | BOGOF | 448 | 1895 |
| 07e4ea | P04 | BOGOF | 486 | 1890 |
| 855f49 | P04 | BOGOF | 481 | 1890 |
| 0c9f61 | P03 | BOGOF | 433 | 1883 |
| 6d65d2 | P04 | BOGOF | 480 | 1867 |
| 4a8c38 | P04 | BOGOF | 469 | 1861 |
| 84a2f4 | P04 | BOGOF | 423 | 1801 |
| 693708 | P03 | BOGOF | 454 | 1788 |
| 05e55f | P03 | BOGOF | 415 | 1759 |
| 726ac4 | P04 | BOGOF | 454 | 1756 |
| 368ca0 | P04 | BOGOF | 432 | 1736 |
| caa1e1 | P03 | BOGOF | 432 | 1736 |
| 572031 | P03 | BOGOF | 423 | 1734 |
| 141d98 | P03 | BOGOF | 387 | 1695 |
| 284539 | P03 | BOGOF | 384 | 1678 |
| 49e9ea | P04 | BOGOF | 415 | 1672 |
| 4001c4 | P04 | BOGOF | 402 | 1652 |
| 7704c2 | P04 | BOGOF | 382 | 1638 |
| edaef4 | P03 | BOGOF | 416 | 1630 |
| 20618e | P04 | BOGOF | 379 | 1622 |
| 3c0536 | P03 | BOGOF | 415 | 1622 |
| 61089e | P04 | BOGOF | 412 | 1615 |
| 90110c | P04 | BOGOF | 412 | 1615 |
| 480431 | P04 | BOGOF | 408 | 1607 |
| aa96fc | P04 | BOGOF | 379 | 1603 |
| 19d7b5 | P03 | BOGOF | 382 | 1596 |
| 7b51be | P04 | BOGOF | 403 | 1587 |
| c9fa13 | P04 | BOGOF | 403 | 1567 |
| 59f792 | P15 | 500 Cashback | 448 | 1545 |
| 34395c | P15 | 500 Cashback | 434 | 1514 |
| bfc9da | P04 | BOGOF | 387 | 1509 |
| dee3e9 | P03 | BOGOF | 384 | 1509 |
| d81627 | P04 | BOGOF | 355 | 1508 |
| d8f51c | P15 | 500 Cashback | 449 | 1499 |
| 620715 | P03 | BOGOF | 340 | 1485 |
| 7c8fd1 | P15 | 500 Cashback | 416 | 1472 |
| bb62b3 | P03 | BOGOF | 378 | 1459 |
| 1b0022 | P04 | BOGOF | 370 | 1457 |
| 4e42b9 | P03 | BOGOF | 376 | 1447 |
| c24879 | P04 | BOGOF | 370 | 1439 |
| 6e79d3 | P04 | BOGOF | 373 | 1439 |
| 45512d | P04 | BOGOF | 336 | 1434 |
| 8f512d | P04 | BOGOF | 364 | 1434 |
| fd48ff | P04 | BOGOF | 367 | 1423 |
| 4dcb0e | P03 | BOGOF | 360 | 1414 |
| cbf0ad | P03 | BOGOF | 358 | 1410 |
| 8cd89f | P03 | BOGOF | 363 | 1408 |
| 1490b8 | P04 | BOGOF | 361 | 1397 |
| c95efb | P15 | 500 Cashback | 416 | 1389 |
| 0312a8 | P15 | 500 Cashback | 393 | 1375 |
| d134e0 | P15 | 500 Cashback | 442 | 1365 |
| f3ac85 | P03 | BOGOF | 348 | 1350 |
| 5c2d1f | P03 | BOGOF | 304 | 1340 |
| b46d32 | P04 | BOGOF | 337 | 1337 |
| 2b50e0 | P15 | 500 Cashback | 390 | 1318 |
| fd2628 | P15 | 500 Cashback | 437 | 1306 |
| c1debe | P15 | 500 Cashback | 381 | 1303 |
| da1969 | P03 | BOGOF | 322 | 1291 |
| 691b63 | P15 | 500 Cashback | 432 | 1291 |
| 388a78 | P03 | BOGOF | 307 | 1277 |
| efd0d2 | P15 | 500 Cashback | 486 | 1273 |
| ce5851 | P03 | BOGOF | 318 | 1265 |
| 317699 | P03 | BOGOF | 310 | 1246 |
| 4ad12b | P15 | 500 Cashback | 407 | 1245 |
| e0ef00 | P03 | BOGOF | 309 | 1226 |
| c8ce63 | P15 | 500 Cashback | 369 | 1221 |
| 911349 | P15 | 500 Cashback | 397 | 1214 |
| ace471 | P04 | BOGOF | 273 | 1201 |
| bb974d | P03 | BOGOF | 307 | 1200 |
| 5.23E+42 | P15 | 500 Cashback | 388 | 1187 |
| 9fae1c | P15 | 500 Cashback | 400 | 1176 |
| 86ec8d | P04 | BOGOF | 303 | 1172 |
| 2fe1bb | P04 | BOGOF | 460 | 1168 |
| a6e691 | P03 | BOGOF | 294 | 1134 |
| 6f3e24 | P15 | 500 Cashback | 388 | 1129 |
| 41d6bd | P03 | BOGOF | 424 | 1127 |
| ab6327 | P04 | BOGOF | 444 | 1123 |
| 870b25 | P04 | BOGOF | 418 | 1116 |
| c6693c | P04 | BOGOF | 413 | 1102 |
| 800f42 | P03 | BOGOF | 273 | 1097 |
| 6b74c8 | P15 | 500 Cashback | 379 | 1095 |
| 9bc176 | P04 | BOGOF | 416 | 1085 |
| 0690d9 | P15 | 500 Cashback | 418 | 1082 |
| 6ec0eb | P15 | 500 Cashback | 369 | 1073 |
| fb508c | P15 | 500 Cashback | 358 | 1070 |
| c8670a | P15 | 500 Cashback | 343 | 1056 |
| 291ddf | P03 | BOGOF | 267 | 1054 |
| e7769b | P15 | 500 Cashback | 357 | 1046 |
| 93118f | P03 | BOGOF | 261 | 1041 |
| 6a1564 | P15 | 500 Cashback | 334 | 1022 |
| 4.47E+06 | P04 | BOGOF | 253 | 1017 |
| b999c5 | P03 | BOGOF | 406 | 1015 |
| 9ce293 | P03 | BOGOF | 255 | 1009 |
| 802b3c | P15 | 500 Cashback | 369 | 1007 |
| a1503f | P15 | 500 Cashback | 329 | 1000 |
| 8724c8 | P04 | BOGOF | 363 | 990 |
| 4dca21 | P04 | BOGOF | 252 | 985 |
| 5b357f | P15 | 500 Cashback | 322 | 985 |
| 9fcb92 | P15 | 500 Cashback | 315 | 976 |
| e411c6 | P15 | 500 Cashback | 323 | 965 |
| a7fecb | P03 | BOGOF | 361 | 963 |
| e96e9d | P15 | 500 Cashback | 362 | 959 |
| 70e65e | P15 | 500 Cashback | 320 | 937 |
| 400cab | P02 | 33% OFF | 642 | 918 |
| 879d9a | P15 | 500 Cashback | 318 | 915 |
| fd4e7e | P03 | BOGOF | 336 | 913 |
| d61f6f | P03 | BOGOF | 331 | 903 |
| f725c0 | P03 | BOGOF | 228 | 898 |
| 6ee2af | P02 | 33% OFF | 595 | 892 |
| 1dd472 | P04 | BOGOF | 220 | 886 |
| c649ca | P02 | 33% OFF | 595 | 886 |
| a02f06 | P04 | BOGOF | 226 | 881 |
| c3c9e3 | P15 | 500 Cashback | 301 | 869 |
| 8a7e7e | P03 | BOGOF | 333 | 869 |
| e2f6b2 | P15 | 500 Cashback | 316 | 859 |
| b0cc1e | P02 | 33% OFF | 610 | 847 |
| 8d5095 | P15 | 500 Cashback | 234 | 840 |
| 136c14 | P03 | BOGOF | 328 | 833 |
| 0d853d | P02 | 33% OFF | 594 | 819 |
| 4f7c26 | P15 | 500 Cashback | 316 | 818 |
| 269cec | P02 | 33% OFF | 532 | 813 |
| 4cc388 | P02 | 33% OFF | 526 | 799 |
| 4f560f | P02 | 33% OFF | 514 | 791 |
| dbd453 | P03 | BOGOF | 195 | 776 |
| 8ff468 | P03 | BOGOF | 193 | 773 |
| 8564bb | P04 | BOGOF | 291 | 762 |
| b526b4 | P02 | 33% OFF | 525 | 756 |
| 6a1a5a | P15 | 500 Cashback | 250 | 755 |
| 21006 | P03 | BOGOF | 192 | 754 |
| af100a | P03 | BOGOF | 190 | 752 |
| 508621 | P02 | 33% OFF | 508 | 751 |
| 4ff977 | P15 | 500 Cashback | 292 | 750 |
| db8aa8 | P03 | BOGOF | 193 | 746 |
| f2d468 | P03 | BOGOF | 190 | 741 |
| ab3517 | P04 | BOGOF | 190 | 733 |
| 9953ec | P04 | BOGOF | 187 | 733 |
| 4692bf | P04 | BOGOF | 267 | 731 |
| c4006c | P15 | 500 Cashback | 243 | 724 |
| 4f40ed | P02 | 33% OFF | 564 | 721 |
| 607c9d | P02 | 33% OFF | 556 | 711 |
| 18810a | P02 | 33% OFF | 395 | 711 |
| 315542 | P03 | BOGOF | 183 | 710 |
| c15780 | P04 | BOGOF | 183 | 708 |
| b7286f | P02 | 33% OFF | 507 | 704 |
| b58c2d | P02 | 33% OFF | 499 | 703 |
| 19352c | P02 | 33% OFF | 501 | 701 |
| 99ce6a | P03 | BOGOF | 250 | 687 |
| 7b49ce | P15 | 500 Cashback | 224 | 685 |
| ff18f2 | P15 | 500 Cashback | 260 | 681 |
| d7798b | P02 | 33% OFF | 484 | 677 |
| 4aa530 | P02 | 33% OFF | 465 | 674 |
| 335090 | P15 | 500 Cashback | 262 | 673 |
| 4b411a | P15 | 500 Cashback | 218 | 673 |
| 3bf731 | P04 | BOGOF | 265 | 673 |
| 240703 | P02 | 33% OFF | 471 | 659 |
| 536fbf | P15 | 500 Cashback | 217 | 659 |
| 02b894 | P02 | 33% OFF | 477 | 658 |
| c6ca4d | P02 | 33% OFF | 465 | 646 |
| ffdcb8 | P02 | 33% OFF | 454 | 644 |
| 3459ec | P02 | 33% OFF | 468 | 636 |
| 5729c0 | P04 | BOGOF | 240 | 636 |
| 2b41a0 | P02 | 33% OFF | 450 | 634 |
| 0da7fd | P02 | 33% OFF | 408 | 632 |
| 0dfaac | P02 | 33% OFF | 434 | 629 |
| 9c2777 | P02 | 33% OFF | 463 | 629 |
| 096adc | P02 | 33% OFF | 441 | 626 |
| 0013db | P02 | 33% OFF | 435 | 622 |
| 874377 | P02 | 33% OFF | 365 | 616 |
| ef7122 | P15 | 500 Cashback | 211 | 614 |
| 0f750a | P02 | 33% OFF | 451 | 613 |
| 1c9eaa | P02 | 33% OFF | 367 | 612 |
| 53bb94 | P02 | 33% OFF | 402 | 611 |
| 1e5c85 | P01 | 33% OFF | 341 | 606 |
| 04da18 | P03 | BOGOF | 223 | 604 |
| 1768c2 | P02 | 33% OFF | 367 | 601 |
| 5a4d9d | P02 | 33% OFF | 468 | 599 |
| 09d857 | P02 | 33% OFF | 386 | 594 |
| fbab9b | P01 | 33% OFF | 334 | 591 |
| ffb109 | P15 | 500 Cashback | 204 | 589 |
| b5b0f5 | P02 | 33% OFF | 399 | 586 |
| 6909d3 | P02 | 33% OFF | 390 | 585 |
| 107747 | P02 | 33% OFF | 488 | 580 |
| f8b6ac | P02 | 33% OFF | 400 | 580 |
| 84aa9b | P02 | 33% OFF | 424 | 580 |
| 3ea719 | P02 | 33% OFF | 336 | 577 |
| 32c24e | P02 | 33% OFF | 392 | 568 |
| 3f2255 | P02 | 33% OFF | 381 | 563 |
| bfb2b4 | P13 | BOGOF | 133 | 559 |
| 3153d6 | P02 | 33% OFF | 396 | 558 |
| 742ad5 | P02 | 33% OFF | 357 | 549 |
| 2cc7f0 | P02 | 33% OFF | 457 | 548 |
| cf6323 | P15 | 500 Cashback | 190 | 547 |
| 3bcf8b | P14 | BOGOF | 138 | 547 |
| fad26a | P01 | 33% OFF | 369 | 546 |
| 6.24E+11 | P03 | BOGOF | 206 | 541 |
| fd5955 | P02 | 33% OFF | 313 | 541 |
| 4f757f | P13 | BOGOF | 129 | 540 |
| 96a556 | P02 | 33% OFF | 358 | 537 |
| 5.40E+190 | P02 | 33% OFF | 362 | 535 |
| df45ee | P01 | 33% OFF | 309 | 534 |
| 70c312 | P13 | BOGOF | 135 | 534 |
| 160abb | P02 | 33% OFF | 336 | 534 |
| d180ef | P01 | 33% OFF | 341 | 531 |
| 0953d7 | P02 | 33% OFF | 387 | 530 |
| ed2257 | P01 | 33% OFF | 358 | 529 |
| c8035e | P13 | BOGOF | 122 | 529 |
| 440bd9 | P13 | BOGOF | 129 | 528 |
| a05e82 | P13 | BOGOF | 124 | 527 |
| e5e244 | P02 | 33% OFF | 351 | 526 |
| f63299 | P02 | 33% OFF | 301 | 526 |
| ee63b3 | P02 | 33% OFF | 362 | 521 |
| e5804e | P01 | 33% OFF | 316 | 521 |
| f22294 | P01 | 33% OFF | 345 | 520 |
| d4fced | P13 | BOGOF | 132 | 520 |
| 003e8d | P02 | 33% OFF | 371 | 519 |
| 87be33 | P13 | BOGOF | 120 | 516 |
| 42b041 | P01 | 33% OFF | 357 | 514 |
| 716a3b | P14 | BOGOF | 130 | 514 |
| 4858ab | P14 | BOGOF | 124 | 514 |
| 613571 | P15 | 500 Cashback | 168 | 514 |
| 873333 | P15 | 500 Cashback | 196 | 509 |
| 144c17 | P02 | 33% OFF | 411 | 509 |
| c4123e | P02 | 33% OFF | 336 | 507 |
| 62e500 | P01 | 33% OFF | 346 | 505 |
| 9bd616 | P01 | 33% OFF | 330 | 504 |
| 4fa17c | P01 | 33% OFF | 327 | 503 |
| cfa879 | P13 | BOGOF | 114 | 502 |
| 1271 | P13 | BOGOF | 121 | 500 |
| f95092 | P13 | BOGOF | 124 | 500 |
| 141aea | P14 | BOGOF | 111 | 493 |
| 7a22bc | P01 | 33% OFF | 283 | 492 |
| a0a2ec | P01 | 33% OFF | 346 | 491 |
| f30579 | P02 | 33% OFF | 337 | 488 |
| ad9ba5 | P01 | 33% OFF | 337 | 485 |
| 371e1a | P01 | 33% OFF | 322 | 483 |
| 546cc3 | P01 | 33% OFF | 312 | 483 |
| 635862 | P02 | 33% OFF | 348 | 480 |
| f2bdcc | P01 | 33% OFF | 337 | 478 |
| dc2bb1 | P02 | 33% OFF | 400 | 476 |
| 761785 | P14 | BOGOF | 121 | 474 |
| bf49bf | P14 | BOGOF | 111 | 473 |
| 348fe6 | P01 | 33% OFF | 332 | 471 |
| 9387d1 | P02 | 33% OFF | 329 | 470 |
| 407f1c | P13 | BOGOF | 117 | 469 |
| 1e2a0e | P01 | 33% OFF | 329 | 467 |
| 53b2fd | P01 | 33% OFF | 320 | 467 |
| 8376c6 | P01 | 33% OFF | 336 | 467 |
| 0a8543 | P01 | 33% OFF | 304 | 465 |
| 6f3721 | P13 | BOGOF | 118 | 464 |
| 97ad03 | P02 | 33% OFF | 379 | 462 |
| 2e3393 | P14 | BOGOF | 112 | 460 |
| 3cb389 | P01 | 33% OFF | 309 | 460 |
| 73f158 | P14 | BOGOF | 118 | 459 |
| c6e3ae | P13 | BOGOF | 117 | 457 |
| 003c65 | P13 | BOGOF | 114 | 457 |
| f741af | P01 | 33% OFF | 333 | 456 |
| 58ce38 | P13 | BOGOF | 118 | 455 |
| 9c5d5a | P02 | 33% OFF | 308 | 455 |
| dbaf92 | P01 | 33% OFF | 301 | 454 |
| 2ba1ba | P13 | BOGOF | 106 | 454 |
| c4a484 | P01 | 33% OFF | 295 | 454 |
| 582098 | P14 | BOGOF | 109 | 453 |
| 261bd6 | P02 | 33% OFF | 308 | 452 |
| eccfbe | P02 | 33% OFF | 364 | 451 |
| a1624e | P02 | 33% OFF | 351 | 449 |
| bac74e | P01 | 33% OFF | 319 | 449 |
| a4fb0b | P02 | 33% OFF | 318 | 448 |
| 03b653 | P02 | 33% OFF | 266 | 446 |
| 166a02 | P13 | BOGOF | 111 | 445 |
| 792708 | P13 | BOGOF | 115 | 445 |
| 6af3e0 | P14 | BOGOF | 103 | 444 |
| 95f061 | P15 | 500 Cashback | 160 | 443 |
| 67f756 | P13 | BOGOF | 111 | 441 |
| 3952a0 | P13 | BOGOF | 114 | 441 |
| db76f3 | P01 | 33% OFF | 294 | 438 |
| aabcfb | P02 | 33% OFF | 345 | 438 |
| a10402 | P02 | 33% OFF | 295 | 436 |
| ac6273 | P01 | 33% OFF | 281 | 435 |
| 1d8f76 | P01 | 33% OFF | 301 | 433 |
| 7d1872 | P02 | 33% OFF | 283 | 430 |
| 2ef46d | P02 | 33% OFF | 278 | 430 |
| f9d2c6 | P14 | BOGOF | 111 | 429 |
| fe68f2 | P01 | 33% OFF | 304 | 428 |
| 6422b4 | P01 | 33% OFF | 255 | 425 |
| cb43c4 | P14 | BOGOF | 106 | 424 |
| d41d53 | P01 | 33% OFF | 334 | 424 |
| 5f65df | P13 | BOGOF | 105 | 423 |
| fc376a | P14 | BOGOF | 106 | 422 |
| ce68be | P01 | 33% OFF | 310 | 421 |
| 29687a | P02 | 33% OFF | 298 | 420 |
| d953a5 | P01 | 33% OFF | 297 | 418 |
| f3a7b2 | P01 | 33% OFF | 306 | 416 |
| 69a46e | P01 | 33% OFF | 320 | 416 |
| a26b45 | P01 | 33% OFF | 287 | 413 |
| a617b5 | P14 | BOGOF | 102 | 410 |
| 2b8abd | P14 | BOGOF | 105 | 407 |
| 36968d | P02 | 33% OFF | 289 | 404 |
| 60229b | P01 | 33% OFF | 241 | 404 |
| dcaa89 | P13 | BOGOF | 100 | 403 |
| 2f3e5d | P01 | 33% OFF | 333 | 402 |
| c5ba9b | P01 | 33% OFF | 279 | 401 |
| 8ef678 | P01 | 33% OFF | 311 | 398 |
| 830e9a | P01 | 33% OFF | 325 | 396 |
| d3d442 | P15 | 500 Cashback | 166 | 396 |
| cfeac1 | P14 | BOGOF | 100 | 396 |
| cc5ed4 | P03 | 25% OFF | 444 | 395 |
| 21a8a0 | P01 | 33% OFF | 286 | 394 |
| 4b515c | P02 | 33% OFF | 274 | 394 |
| 31c430 | P01 | 33% OFF | 312 | 393 |
| 57a7bc | P14 | BOGOF | 100 | 391 |
| bcbc28 | P02 | 33% OFF | 253 | 389 |
| c873b4 | P02 | 33% OFF | 267 | 389 |
| 2ba228 | P02 | 33% OFF | 316 | 388 |
| 77435f | P01 | 33% OFF | 277 | 387 |
| cefb49 | P02 | 33% OFF | 322 | 386 |
| 7014a8 | P14 | BOGOF | 97 | 385 |
| a1e541 | P01 | 33% OFF | 311 | 385 |
| 1f0eaf | P15 | 500 Cashback | 147 | 385 |
| d1bfe5 | P02 | 33% OFF | 301 | 385 |
| eb967c | P15 | 500 Cashback | 133 | 383 |
| b78a4f | P13 | BOGOF | 99 | 383 |
| cf4f71 | P01 | 33% OFF | 250 | 382 |
| f682ec | P01 | 33% OFF | 273 | 382 |
| 59effd | P14 | BOGOF | 97 | 380 |
| c1e0b6 | P01 | 33% OFF | 273 | 379 |
| 8b729b | P02 | 33% OFF | 319 | 379 |
| 459bc3 | P13 | BOGOF | 97 | 378 |
| b41e58 | P02 | 33% OFF | 255 | 377 |
| f94d7b | P13 | BOGOF | 96 | 377 |
| 9d7bd2 | P03 | 25% OFF | 413 | 375 |
| 494f1b | P13 | BOGOF | 94 | 374 |
| c7f28c | P15 | 500 Cashback | 144 | 374 |
| 9a1d69 | P01 | 33% OFF | 292 | 373 |
| 7151bb | P13 | BOGOF | 98 | 372 |
| 463205 | P02 | 33% OFF | 215 | 371 |
| 6ae240 | P13 | BOGOF | 94 | 371 |
| 581ca5 | P13 | BOGOF | 90 | 371 |
| 18c9f4 | P03 | 25% OFF | 385 | 369 |
| b68b77 | P01 | 33% OFF | 244 | 368 |
| fa1dd3 | P15 | 500 Cashback | 127 | 367 |
| 0d70f7 | P01 | 33% OFF | 210 | 367 |
| 386fdc | P01 | 33% OFF | 257 | 364 |
| 0eb41f | P01 | 33% OFF | 232 | 364 |
| 406a98 | P01 | 33% OFF | 264 | 361 |
| b78191 | P14 | BOGOF | 91 | 361 |
| 6a54d2 | P01 | 33% OFF | 303 | 360 |
| 72eed8 | P04 | 25% OFF | 376 | 360 |
| 13d333 | P01 | 33% OFF | 256 | 358 |
| 1bb04d | P01 | 33% OFF | 240 | 355 |
| 41cb8f | P03 | 25% OFF | 402 | 353 |
| 686a37 | P14 | BOGOF | 85 | 350 |
| 7cf0d8 | P14 | BOGOF | 79 | 349 |
| a929ed | P03 | 25% OFF | 358 | 347 |
| fb70b4 | P03 | 25% OFF | 355 | 347 |
| a937e8 | P14 | BOGOF | 87 | 347 |
| ef6d6d | P14 | BOGOF | 88 | 346 |
| 5760fd | P13 | BOGOF | 87 | 346 |
| b017e0 | P02 | 33% OFF | 276 | 345 |
| 7d9576 | P15 | 500 Cashback | 120 | 345 |
| 72f6b4 | P02 | 33% OFF | 241 | 344 |
| 4f76ac | P04 | 25% OFF | 383 | 344 |
| 32b8a7 | P03 | 25% OFF | 378 | 343 |
| 608271 | P15 | 500 Cashback | 122 | 342 |
| f7aec5 | P13 | BOGOF | 87 | 341 |
| 250dee | P01 | 33% OFF | 237 | 341 |
| a692dc | P01 | 33% OFF | 270 | 340 |
| f32df2 | P04 | 25% OFF | 390 | 339 |
| 1e9a06 | P13 | BOGOF | 84 | 338 |
| af2b25 | P13 | BOGOF | 85 | 338 |
| 79577d | P03 | 25% OFF | 348 | 337 |
| fe72b2 | P13 | BOGOF | 133 | 337 |
| 6c7601 | P14 | BOGOF | 78 | 334 |
| fcf54a | P04 | 25% OFF | 348 | 334 |
| 1fc58f | P01 | 33% OFF | 244 | 334 |
| 0e888c | P02 | 33% OFF | 274 | 334 |
| 4a77da | P02 | 33% OFF | 243 | 332 |
| 0f5588 | P03 | 25% OFF | 378 | 332 |
| 07ee94 | P03 | 25% OFF | 369 | 332 |
| 48d526 | P15 | 500 Cashback | 115 | 332 |
| a34aa4 | P03 | 25% OFF | 369 | 332 |
| ac0b1c | P14 | BOGOF | 78 | 331 |
| a37110 | P04 | 25% OFF | 367 | 330 |
| 46d57b | P13 | BOGOF | 94 | 329 |
| acf9c2 | P01 | 33% OFF | 235 | 329 |
| 3164ea | P01 | 33% OFF | 265 | 328 |
| 66b7cc | P13 | BOGOF | 82 | 328 |
| 58df9b | P02 | 33% OFF | 183 | 327 |
| 2dd3f7 | P03 | 25% OFF | 341 | 327 |
| 1c3fb4 | P02 | 33% OFF | 237 | 327 |
| 677e2c | P13 | BOGOF | 122 | 326 |
| 8cd1ec | P13 | BOGOF | 124 | 324 |
| 0a4160 | P03 | 25% OFF | 330 | 323 |
| f90ae9 | P13 | BOGOF | 82 | 323 |
| a21f91 | P03 | 25% OFF | 393 | 322 |
| 7b187a | P14 | BOGOF | 82 | 322 |
| 541bef | P01 | 33% OFF | 234 | 322 |
| e7f270 | P01 | 33% OFF | 211 | 322 |
| 8f4f8c | P02 | 33% OFF | 210 | 321 |
| 6a7668 | P15 | 500 Cashback | 112 | 321 |
| 9d3d1f | P15 | 500 Cashback | 147 | 320 |
| 9b5299 | P04 | 25% OFF | 360 | 320 |
| 12bb06 | P03 | 25% OFF | 351 | 319 |
| 8937eb | P03 | 25% OFF | 357 | 317 |
| 5487a6 | P03 | 25% OFF | 358 | 315 |
| 00a7c3 | P02 | 33% OFF | 231 | 314 |
| da3c49 | P02 | 33% OFF | 270 | 313 |
| 1f8bc3 | P01 | 33% OFF | 190 | 313 |
| b6b840 | P02 | 33% OFF | 244 | 312 |
| d3227b | P04 | 25% OFF | 343 | 312 |
| c917a3 | P04 | 25% OFF | 350 | 311 |
| bd2635 | P04 | 25% OFF | 327 | 310 |
| 6562df | P14 | BOGOF | 78 | 310 |
| 93dff2 | P03 | 25% OFF | 390 | 308 |
| c5176d | P01 | 33% OFF | 196 | 307 |
| d60641 | P03 | 25% OFF | 351 | 305 |
| bcad3c | P01 | 33% OFF | 201 | 305 |
| 4cf56a | P04 | 25% OFF | 311 | 304 |
| 292d0a | P01 | 33% OFF | 219 | 304 |
| 8819fd | P04 | 25% OFF | 350 | 304 |
| 0a45d8 | P02 | 33% OFF | 196 | 303 |
| 29411f | P08 | BOGOF | 69 | 303 |
| 8f25a6 | P15 | 500 Cashback | 126 | 302 |
| 2f0b42 | P01 | 33% OFF | 213 | 302 |
| 667c78 | P01 | 33% OFF | 223 | 301 |
| 1a1edd | P03 | 25% OFF | 343 | 301 |
| 345b49 | P14 | BOGOF | 76 | 300 |
| c9899d | P02 | 33% OFF | 199 | 300 |
| ef95a9 | P13 | BOGOF | 87 | 298 |
| 3b54c7 | P04 | 25% OFF | 367 | 297 |
| c3b511 | P14 | BOGOF | 75 | 297 |
| 13a676 | P01 | 33% OFF | 203 | 296 |
| 3b4a4f | P04 | 25% OFF | 337 | 296 |
| 2dc515 | P01 | 33% OFF | 232 | 294 |
| e0de60 | P03 | 25% OFF | 327 | 294 |
| e12c11 | P14 | BOGOF | 112 | 294 |
| 73c8f5 | P01 | 33% OFF | 229 | 293 |
| c115da | P13 | BOGOF | 84 | 293 |
| 4d8607 | P03 | 25% OFF | 323 | 293 |
| 260ff2 | P01 | 33% OFF | 204 | 291 |
| de1ced | P03 | 25% OFF | 330 | 290 |
| 24541f | P13 | BOGOF | 111 | 290 |
| dd2475 | P04 | 25% OFF | 325 | 289 |
| 5c8b9f | P01 | 33% OFF | 187 | 289 |
| 8f5618 | P04 | 25% OFF | 302 | 289 |
| 8d68bc | P03 | 25% OFF | 357 | 289 |
| a25cbf | P04 | 25% OFF | 295 | 289 |
| b44f0e | P15 | 500 Cashback | 136 | 288 |
| 741bef | P13 | BOGOF | 114 | 287 |
| 8481be | P04 | 25% OFF | 327 | 287 |
| 91649 | P13 | BOGOF | 73 | 287 |
| c1cdb5 | P15 | 500 Cashback | 135 | 286 |
| eae38f | P13 | BOGOF | 73 | 286 |
| 4e3a3d | P02 | 33% OFF | 197 | 285 |
| 6ed2f5 | P13 | BOGOF | 84 | 285 |
| fe4a15 | P01 | 33% OFF | 205 | 284 |
| 75c3a0 | P13 | BOGOF | 73 | 282 |
| 74399f | P13 | BOGOF | 73 | 282 |
| 933f7e | P07 | BOGOF | 71 | 282 |
| e5d28d | P13 | BOGOF | 73 | 282 |
| 98d4e3 | P13 | BOGOF | 70 | 281 |
| aa54a7 | P13 | BOGOF | 91 | 281 |
| 4236be | P14 | BOGOF | 70 | 280 |
| f98db5 | P15 | 500 Cashback | 129 | 279 |
| 86206 | P14 | BOGOF | 102 | 279 |
| 308de6 | P01 | 33% OFF | 225 | 279 |
| fe1a8b | P15 | 500 Cashback | 126 | 278 |
| 300664 | P13 | BOGOF | 80 | 276 |
| 68a7bc | P04 | 25% OFF | 322 | 276 |
| 6bb477 | P04 | 25% OFF | 318 | 276 |
| f013a9 | P14 | BOGOF | 105 | 276 |
| b5cd07 | P01 | 33% OFF | 222 | 275 |
| 5202ed | P03 | 25% OFF | 306 | 275 |
| 87bb82 | P15 | 500 Cashback | 126 | 275 |
| 49057f | P15 | 500 Cashback | 121 | 274 |
| 5db3e3 | P13 | BOGOF | 78 | 274 |
| 49706e | P15 | 500 Cashback | 120 | 274 |
| 5dda21 | P14 | BOGOF | 69 | 274 |
| 2b0a40 | P13 | BOGOF | 82 | 273 |
| 465ef1 | P04 | 25% OFF | 304 | 273 |
| 1d651c | P15 | 500 Cashback | 121 | 273 |
| 6d153f | P15 | 500 Cashback | 122 | 272 |
| 74657 | P02 | 33% OFF | 194 | 271 |
| d290a1 | P04 | 25% OFF | 343 | 270 |
| 5f8870 | P13 | BOGOF | 70 | 270 |
| 87564a | P04 | 25% OFF | 346 | 269 |
| d304f9 | P04 | 25% OFF | 309 | 268 |
| d3575d | P02 | 33% OFF | 210 | 268 |
| 9a425b | P03 | 25% OFF | 276 | 267 |
| 1f1b71 | P01 | 33% OFF | 214 | 267 |
| 68718c | P04 | 25% OFF | 309 | 265 |
| 8c62ba | P01 | 33% OFF | 161 | 265 |
| 0a453f | P03 | 25% OFF | 301 | 264 |
| 3a3e96 | P07 | BOGOF | 68 | 263 |
| 861506 | P03 | 25% OFF | 334 | 260 |
| f940cf | P13 | BOGOF | 77 | 260 |
| 50802a | P07 | BOGOF | 64 | 257 |
| 7641 | P14 | BOGOF | 97 | 257 |
| c3b647 | P08 | BOGOF | 64 | 256 |
| 7b0f7d | P01 | 33% OFF | 180 | 255 |
| 7a2a47 | P07 | BOGOF | 64 | 254 |
| 583386 | P08 | BOGOF | 63 | 254 |
| 496b80 | P15 | 500 Cashback | 118 | 253 |
| 1ed982 | P13 | BOGOF | 75 | 252 |
| 74d23a | P07 | BOGOF | 75 | 252 |
| c8e17c | P02 | 33% OFF | 166 | 252 |
| 6.59E+23 | P01 | 33% OFF | 186 | 252 |
| ebd35e | P04 | 25% OFF | 323 | 251 |
| 5947fb | P15 | 500 Cashback | 118 | 251 |
| 75f30e | P15 | 500 Cashback | 117 | 251 |
| 18a68a | P01 | 33% OFF | 173 | 250 |
| 58e374 | P07 | BOGOF | 64 | 250 |
| bea96f | P14 | BOGOF | 64 | 250 |
| 5f0a89 | P15 | 500 Cashback | 114 | 249 |
| 8e1636 | P15 | 500 Cashback | 109 | 249 |
| 8dca75 | P13 | BOGOF | 71 | 248 |
| fe3560 | P13 | BOGOF | 73 | 245 |
| e78335 | P03 | 25% OFF | 281 | 244 |
| d0daaa | P14 | BOGOF | 63 | 244 |
| 95792f | P15 | 500 Cashback | 106 | 243 |
| c092d4 | P07 | BOGOF | 70 | 243 |
| 6a7fa1 | P14 | BOGOF | 61 | 243 |
| 11ea6f | P04 | 25% OFF | 271 | 243 |
| 021d48 | P14 | BOGOF | 61 | 243 |
| dcaeaa | P04 | 25% OFF | 276 | 242 |
| ee68d9 | P15 | 500 Cashback | 136 | 242 |
| d62a10 | P13 | BOGOF | 63 | 242 |
| 6ebca9 | P13 | BOGOF | 60 | 240 |
| 715baf | P13 | BOGOF | 82 | 239 |
| eb3bea | P15 | 500 Cashback | 109 | 238 |
| 8cbaa3 | P08 | BOGOF | 60 | 238 |
| 66050c | P08 | BOGOF | 60 | 238 |
| 716abd | P08 | BOGOF | 54 | 238 |
| 2e3594 | P13 | BOGOF | 61 | 237 |
| 35637b | P03 | 25% OFF | 301 | 237 |
| c4db5b | P01 | 33% OFF | 164 | 236 |
| 029ff8 | P01 | 33% OFF | 169 | 236 |
| d6cc80 | P07 | BOGOF | 61 | 236 |
| 11578 | P14 | BOGOF | 87 | 236 |
| 1ee94b | P13 | BOGOF | 68 | 235 |
| 68c31e | P08 | BOGOF | 54 | 235 |
| 413f48 | P14 | BOGOF | 61 | 234 |
| 4b3df6 | P14 | BOGOF | 61 | 234 |
| 60ba75 | P13 | BOGOF | 60 | 234 |
| 0e96b4 | P14 | BOGOF | 93 | 234 |
| d33904 | P07 | BOGOF | 59 | 233 |
| 105788 | P07 | BOGOF | 58 | 232 |
| b8269b | P13 | BOGOF | 77 | 232 |
| 4ab9ba | P01 | 33% OFF | 165 | 232 |
| 4888d5 | P07 | BOGOF | 70 | 231 |
| eae379 | P01 | 33% OFF | 161 | 231 |
| 17edbc | P03 | 25% OFF | 281 | 230 |
| ca7298 | P15 | 500 Cashback | 85 | 228 |
| 66c422 | P07 | BOGOF | 66 | 227 |
| e7d681 | P13 | BOGOF | 66 | 226 |
| 3.14E+36 | P04 | 25% OFF | 252 | 226 |
| 6c9451 | P03 | 25% OFF | 259 | 225 |
| b6dd84 | P01 | 33% OFF | 166 | 225 |
| 543c36 | P07 | BOGOF | 58 | 225 |
| 793873 | P03 | 25% OFF | 248 | 225 |
| d59c23 | P03 | 25% OFF | 252 | 224 |
| a6276f | P14 | BOGOF | 56 | 224 |
| 73211e | P01 | 33% OFF | 182 | 223 |
| 252235 | P07 | BOGOF | 64 | 223 |
| 457639 | P08 | BOGOF | 54 | 222 |
| b6233e | P01 | 33% OFF | 175 | 222 |
| 1bfbb8 | P12 | 50% OFF | 171 | 222 |
| a304b6 | P03 | 25% OFF | 285 | 222 |
| e0a83a | P07 | BOGOF | 63 | 221 |
| c405b3 | P04 | 25% OFF | 252 | 221 |
| b92097 | P03 | 25% OFF | 257 | 221 |
| 292ca5 | P04 | 25% OFF | 287 | 220 |
| 41b8f8 | P08 | BOGOF | 56 | 220 |
| c55ec9 | P15 | 500 Cashback | 136 | 220 |
| b76f57 | P13 | BOGOF | 66 | 220 |
| 1ba928 | P04 | 25% OFF | 255 | 219 |
| 3adeb2 | P14 | BOGOF | 84 | 219 |
| 4e7ca5 | P07 | BOGOF | 54 | 219 |
| 02fa4b | P01 | 33% OFF | 155 | 218 |
| c99d18 | P08 | BOGOF | 54 | 218 |
| 8a219d | P08 | BOGOF | 64 | 218 |
| c25b15 | P07 | BOGOF | 63 | 218 |
| 8fecef | P07 | BOGOF | 75 | 217 |
| 1b6084 | P01 | 33% OFF | 141 | 217 |
| 802dfa | P07 | BOGOF | 54 | 217 |
| 5dfa52 | P04 | 25% OFF | 244 | 217 |
| 4fca07 | P01 | 33% OFF | 183 | 215 |
| e67501 | P13 | BOGOF | 85 | 215 |
| 5.80E+27 | P07 | BOGOF | 73 | 215 |
| 46ee5a | P04 | 25% OFF | 246 | 214 |
| b838cd | P01 | 33% OFF | 147 | 214 |
| 7ef92f | P07 | BOGOF | 55 | 213 |
| 951bda | P07 | BOGOF | 63 | 213 |
| d76198 | P08 | BOGOF | 54 | 213 |
| f1b7e9 | P14 | BOGOF | 52 | 211 |
| 221da2 | P15 | 500 Cashback | 91 | 211 |
| 0c0339 | P07 | BOGOF | 64 | 211 |
| 0ba095 | P03 | 25% OFF | 274 | 210 |
| b79118 | P04 | 25% OFF | 236 | 210 |
| 13ad42 | P03 | 25% OFF | 241 | 209 |
| 955fa6 | P12 | 50% OFF | 161 | 209 |
| 3beb46 | P13 | BOGOF | 81 | 208 |
| 2177f8 | P04 | 25% OFF | 234 | 208 |
| 60170c | P08 | BOGOF | 63 | 208 |
| b7f012 | P15 | 500 Cashback | 118 | 208 |
| 5c3c33 | P12 | 50% OFF | 154 | 207 |
| 2eb400 | P07 | BOGOF | 52 | 207 |
| abffa2 | P07 | BOGOF | 59 | 206 |
| 166989 | P01 | 33% OFF | 169 | 206 |
| bb77b1 | P14 | BOGOF | 54 | 206 |
| c134bb | P07 | BOGOF | 51 | 205 |
| 0edad5 | P13 | BOGOF | 51 | 205 |
| ac0b82 | P04 | 25% OFF | 234 | 205 |
| 7d3d63 | P13 | BOGOF | 68 | 205 |
| 46d796 | P07 | BOGOF | 51 | 205 |
| aac58d | P08 | BOGOF | 52 | 204 |
| e5e0dc | P07 | BOGOF | 52 | 204 |
| ba86f4 | P13 | BOGOF | 61 | 204 |
| cf734f | P08 | BOGOF | 51 | 203 |
| 7a6449 | P10 | 50% OFF | 131 | 203 |
| 0894b7 | P08 | BOGOF | 46 | 203 |
| 37cb7c | P13 | BOGOF | 61 | 203 |
| b08c12 | P03 | 25% OFF | 227 | 202 |
| 35463c | P04 | 25% OFF | 211 | 202 |
| a9d059 | P14 | BOGOF | 50 | 202 |
| 90b2fb | P07 | BOGOF | 59 | 201 |
| 675714 | P13 | BOGOF | 61 | 201 |
| 79a95a | P15 | 500 Cashback | 121 | 200 |
| 8869 | P13 | BOGOF | 75 | 200 |
| 3a8b79 | P07 | BOGOF | 49 | 199 |
| 4ca177 | P14 | BOGOF | 75 | 198 |
| 2fc575 | P12 | 50% OFF | 147 | 198 |
| deea3e | P14 | BOGOF | 51 | 198 |
| 837127 | P03 | 25% OFF | 208 | 197 |
| b00eeb | P08 | BOGOF | 51 | 196 |
| 62775f | P07 | BOGOF | 59 | 196 |
| f65a1e | P04 | 25% OFF | 255 | 196 |
| 14f79d | P04 | 25% OFF | 252 | 196 |
| b97dfe | P07 | BOGOF | 56 | 196 |
| 4c1375 | P10 | 50% OFF | 148 | 196 |
| 71a7a0 | P14 | BOGOF | 59 | 195 |
| e2a523 | P07 | BOGOF | 59 | 195 |
| e875c6 | P03 | 25% OFF | 225 | 195 |
| acaff0 | P12 | 50% OFF | 133 | 195 |
| a42141 | P15 | 500 Cashback | 85 | 195 |
| 57576d | P08 | BOGOF | 49 | 194 |
| 3edc10 | P03 | 25% OFF | 246 | 194 |
| c32fcd | P08 | BOGOF | 73 | 192 |
| 26a18a | P15 | 500 Cashback | 109 | 192 |
| 86755e | P07 | BOGOF | 45 | 191 |
| 35fb5b | P13 | BOGOF | 50 | 190 |
| 9d9a6c | P15 | 500 Cashback | 82 | 190 |
| 268b09 | P13 | BOGOF | 49 | 189 |
| 6aae63 | P13 | BOGOF | 63 | 189 |
| 652101 | P07 | BOGOF | 61 | 189 |
| d91475 | P07 | BOGOF | 61 | 189 |
| a40872 | P14 | BOGOF | 47 | 189 |
| 349c73 | P14 | BOGOF | 57 | 189 |
| 20d916 | P07 | BOGOF | 57 | 188 |
| ef61c6 | P07 | BOGOF | 48 | 188 |
| 35701b | P04 | 25% OFF | 192 | 188 |
| 08086d | P10 | 50% OFF | 120 | 188 |
| d2b963 | P14 | BOGOF | 48 | 187 |
| 30c488 | P01 | 33% OFF | 132 | 187 |
| 660f7c | P07 | BOGOF | 43 | 186 |
| 4a42f9 | P08 | BOGOF | 49 | 186 |
| c16abb | P08 | BOGOF | 42 | 186 |
| 63a2d2 | P08 | BOGOF | 47 | 186 |
| de6e7e | P15 | 500 Cashback | 88 | 186 |
| d4b484 | P10 | 50% OFF | 140 | 186 |
| 987463 | P07 | BOGOF | 45 | 185 |
| 5f2c41 | P08 | BOGOF | 54 | 185 |
| 20da13 | P07 | BOGOF | 48 | 185 |
| 4cefe1 | P12 | 50% OFF | 127 | 185 |
| 43feca | P13 | BOGOF | 56 | 184 |
| 8f2264 | P12 | 50% OFF | 124 | 184 |
| 3d8361 | P08 | BOGOF | 47 | 184 |
| da99ec | P14 | BOGOF | 54 | 184 |
| 699bac | P07 | BOGOF | 42 | 183 |
| 33da9a | P14 | BOGOF | 54 | 183 |
| bf33ae | P14 | BOGOF | 59 | 182 |
| d78c78 | P14 | BOGOF | 52 | 182 |
| 79bfae | P10 | 50% OFF | 134 | 182 |
| cc4a67 | P03 | 25% OFF | 187 | 181 |
| c4dae9 | P08 | BOGOF | 52 | 180 |
| 6046fa | P12 | 50% OFF | 141 | 180 |
| 6d24bc | P03 | 25% OFF | 206 | 179 |
| e80ad8 | P10 | 50% OFF | 136 | 179 |
| 17df71 | P08 | BOGOF | 46 | 179 |
| fb9e95 | P12 | 50% OFF | 141 | 179 |
| adf52a | P14 | BOGOF | 47 | 179 |
| 5.88E+11 | P12 | 50% OFF | 112 | 178 |
| f46036 | P13 | BOGOF | 61 | 178 |
| 1c7c7f | P14 | BOGOF | 52 | 178 |
| 555fcd | P13 | BOGOF | 57 | 178 |
| 9.57E+11 | P15 | 500 Cashback | 103 | 177 |
| ce3c11 | P14 | BOGOF | 52 | 176 |
| 4aa7ef | P07 | BOGOF | 59 | 176 |
| 1548f8 | P15 | 500 Cashback | 100 | 175 |
| f8e037 | P08 | BOGOF | 52 | 175 |
| ad2ad4 | P04 | 25% OFF | 197 | 175 |
| 8f66c3 | P01 | 33% OFF | 126 | 175 |
| a0da88 | P03 | 25% OFF | 204 | 175 |
| 7bb8ed | P08 | BOGOF | 45 | 175 |
| 8f3699 | P03 | 25% OFF | 196 | 174 |
| 6846a8 | P04 | 25% OFF | 201 | 174 |
| c6bf42 | P07 | BOGOF | 52 | 173 |
| 17d5c1 | P13 | BOGOF | 52 | 173 |
| 3ea7d6 | P15 | 500 Cashback | 105 | 173 |
| b2270b | P07 | BOGOF | 52 | 173 |
| 52ec61 | P10 | 50% OFF | 133 | 172 |
| 0842b9 | P04 | 25% OFF | 227 | 172 |
| d3f755 | P08 | BOGOF | 43 | 171 |
| 171bbb | P15 | 500 Cashback | 79 | 171 |
| 896c2a | P04 | 25% OFF | 180 | 171 |
| 8b1147 | P15 | 500 Cashback | 73 | 170 |
| 609bfd | P12 | 50% OFF | 129 | 170 |
| 3bc352 | P07 | BOGOF | 54 | 170 |
| 655aa2 | P10 | 50% OFF | 112 | 170 |
| e24a3a | P07 | BOGOF | 49 | 170 |
| 35e1c7 | P14 | BOGOF | 54 | 169 |
| 0f422c | P14 | BOGOF | 42 | 168 |
| 3c3c49 | P08 | BOGOF | 40 | 168 |
| cd36b2 | P10 | 50% OFF | 127 | 168 |
| 657a95 | P12 | 50% OFF | 126 | 168 |
| b94bda | P13 | BOGOF | 56 | 168 |
| c0ecb5 | P07 | BOGOF | 43 | 167 |
| ca1e8f | P08 | BOGOF | 54 | 167 |
| 7d5e81 | P07 | BOGOF | 43 | 167 |
| 223d36 | P10 | 50% OFF | 129 | 167 |
| a3caaa | P10 | 50% OFF | 126 | 167 |
| 40baa1 | P08 | BOGOF | 42 | 167 |
| 6d343d | P12 | 50% OFF | 133 | 167 |
| 333b7d | P08 | BOGOF | 49 | 166 |
| 1cfaa8 | P08 | BOGOF | 43 | 166 |
| f41ca1 | P07 | BOGOF | 42 | 166 |
| 9d63a7 | P08 | BOGOF | 43 | 166 |
| 4ad894 | P03 | 25% OFF | 192 | 165 |
| fc3f51 | P07 | BOGOF | 40 | 165 |
| a2fd0b | P12 | 50% OFF | 112 | 165 |
| ba0b3e | P07 | BOGOF | 40 | 165 |
| 4fc1b2 | P08 | BOGOF | 47 | 165 |
| 718bb4 | P12 | 50% OFF | 129 | 165 |
| 902903 | P13 | BOGOF | 49 | 164 |
| e39703 | P08 | BOGOF | 47 | 163 |
| 14f1e9 | P08 | BOGOF | 49 | 163 |
| 40f110 | P12 | 50% OFF | 122 | 163 |
| b17786 | P13 | BOGOF | 63 | 163 |
| 333ef0 | P14 | BOGOF | 47 | 163 |
| 0a3c5c | P13 | BOGOF | 47 | 163 |
| fc3573 | P08 | BOGOF | 61 | 163 |
| c48008 | P14 | BOGOF | 47 | 162 |
| cd4812 | P07 | BOGOF | 47 | 162 |
| 99482c | P08 | BOGOF | 42 | 161 |
| 262ff3 | P13 | BOGOF | 47 | 161 |
| 27bc6e | P14 | BOGOF | 42 | 160 |
| 66b476 | P10 | 50% OFF | 103 | 160 |
| 6bf19b | P04 | 25% OFF | 169 | 160 |
| 0951b6 | P09 | 50% OFF | 103 | 159 |
| 8c13bb | P08 | BOGOF | 47 | 159 |
| d04c7f | P07 | BOGOF | 40 | 159 |
| 02c389 | P12 | 50% OFF | 120 | 159 |
| d9d3f4 | P10 | 50% OFF | 103 | 158 |
| a9ee19 | P08 | BOGOF | 58 | 158 |
| fc2170 | P08 | BOGOF | 40 | 158 |
| f2d198 | P03 | 25% OFF | 166 | 157 |
| 6b0ee6 | P07 | BOGOF | 47 | 157 |
| d2a08d | P10 | 50% OFF | 141 | 157 |
| 1f03e5 | P13 | BOGOF | 45 | 157 |
| f304a8 | P04 | 25% OFF | 204 | 157 |
| b9b7dd | P12 | 50% OFF | 126 | 157 |
| 4ca50a | P08 | BOGOF | 50 | 156 |
| 8e6e77 | P08 | BOGOF | 37 | 156 |
| 52d20e | P10 | 50% OFF | 134 | 156 |
| 80be79 | P08 | BOGOF | 39 | 156 |
| 6d863b | P07 | BOGOF | 40 | 155 |
| 5abaf9 | P07 | BOGOF | 37 | 155 |
| 1130ea | P14 | BOGOF | 45 | 155 |
| 9.33E+11 | P08 | BOGOF | 40 | 154 |
| edacb9 | P10 | 50% OFF | 119 | 154 |
| 9acfa3 | P12 | 50% OFF | 115 | 154 |
| 35e3ec | P07 | BOGOF | 40 | 154 |
| 5a6ad7 | P14 | BOGOF | 45 | 153 |
| a35a4f | P10 | 50% OFF | 122 | 153 |
| d0356d | P08 | BOGOF | 45 | 152 |
| 85e08f | P08 | BOGOF | 50 | 152 |
| 268ca2 | P15 | 500 Cashback | 63 | 151 |
| 42fb76 | P10 | 50% OFF | 112 | 151 |
| c74866 | P10 | 50% OFF | 115 | 151 |
| 47af00 | P03 | 25% OFF | 183 | 150 |
| 4d3722 | P04 | 25% OFF | 175 | 150 |
| 4fe9ba | P07 | BOGOF | 45 | 150 |
| 7bdc1e | P07 | BOGOF | 50 | 149 |
| a55960 | P08 | BOGOF | 50 | 149 |
| d88318 | P08 | BOGOF | 45 | 149 |
| c2ee4f | P13 | BOGOF | 58 | 148 |
| e7bb4f | P13 | BOGOF | 45 | 148 |
| d834f0 | P08 | BOGOF | 34 | 147 |
| f856b9 | P15 | 500 Cashback | 66 | 147 |
| cf0a2a | P09 | 50% OFF | 92 | 147 |
| 092c09 | P08 | BOGOF | 43 | 147 |
| 115760 | P07 | BOGOF | 43 | 147 |
| 7d6e2a | P03 | 25% OFF | 166 | 146 |
| d70dcb | P15 | 500 Cashback | 90 | 146 |
| 0a0062 | P12 | 50% OFF | 110 | 146 |
| 04f19c | P08 | BOGOF | 50 | 146 |
| ed0d01 | P12 | 50% OFF | 108 | 145 |
| c6d7c5 | P12 | 50% OFF | 124 | 145 |
| 3.56E+10 | P08 | BOGOF | 36 | 145 |
| e98f37 | P08 | BOGOF | 43 | 145 |
| 642b50 | P14 | BOGOF | 36 | 145 |
| ce39e4 | P13 | BOGOF | 42 | 145 |
| 788131 | P10 | 50% OFF | 108 | 145 |
| dc23bb | P08 | BOGOF | 42 | 145 |
| 6c1493 | P15 | 500 Cashback | 66 | 144 |
| e74698 | P14 | BOGOF | 43 | 144 |
| 30bacd | P14 | BOGOF | 42 | 143 |
| fc9ab7 | P08 | BOGOF | 40 | 140 |
| 84dbe3 | P07 | BOGOF | 51 | 140 |
| 06c981 | P14 | BOGOF | 42 | 139 |
| 5c6465 | P08 | BOGOF | 36 | 139 |
| f8b215 | P14 | BOGOF | 40 | 138 |
| ce95b1 | P12 | 50% OFF | 119 | 138 |
| 7d89b1 | P08 | BOGOF | 45 | 138 |
| 62d659 | P10 | 50% OFF | 105 | 137 |
| 420258 | P14 | BOGOF | 54 | 137 |
| 380a4f | P08 | BOGOF | 45 | 137 |
| 69557f | P10 | 50% OFF | 106 | 137 |
| 4f0587 | P08 | BOGOF | 33 | 136 |
| ddddb3 | P09 | 50% OFF | 103 | 136 |
| 2db607 | P14 | BOGOF | 40 | 136 |
| bc8315 | P12 | 50% OFF | 122 | 135 |
| 5f313a | P10 | 50% OFF | 124 | 135 |
| fc7056 | P08 | BOGOF | 40 | 135 |
| 4f255c | P08 | BOGOF | 52 | 134 |
| cbe691 | P10 | 50% OFF | 103 | 134 |
| 98c85b | P13 | BOGOF | 38 | 133 |
| bb83e5 | P08 | BOGOF | 40 | 133 |
| e116d8 | P12 | 50% OFF | 98 | 133 |
| 02fe6a | P04 | 25% OFF | 152 | 133 |
| 3d7dc9 | P10 | 50% OFF | 127 | 133 |
| 28acbc | P10 | 50% OFF | 105 | 132 |
| dd9914 | P10 | 50% OFF | 98 | 132 |
| fa0c0c | P13 | BOGOF | 40 | 132 |
| 1f5ed3 | P08 | BOGOF | 33 | 131 |
| 8ba5a1 | P09 | 50% OFF | 84 | 131 |
| 30b66a | P11 | 50% OFF | 84 | 131 |
| aa6972 | P12 | 50% OFF | 103 | 131 |
| 578a67 | P11 | 50% OFF | 101 | 131 |
| 1b295f | P12 | 50% OFF | 110 | 130 |
| d1e51d | P07 | BOGOF | 42 | 130 |
| 6639a5 | P07 | BOGOF | 31 | 130 |
| 0f1be6 | P12 | 50% OFF | 89 | 129 |
| e553f2 | P13 | BOGOF | 38 | 129 |
| 17537 | P08 | BOGOF | 33 | 129 |
| 6.20E+94 | P08 | BOGOF | 48 | 129 |
| 8.31E+08 | P08 | BOGOF | 33 | 129 |
| 2c893f | P12 | 50% OFF | 103 | 129 |
| e17280 | P08 | BOGOF | 38 | 129 |
| fea4be | P07 | BOGOF | 30 | 129 |
| 276150 | P07 | BOGOF | 33 | 128 |
| 9779b0 | P10 | 50% OFF | 85 | 128 |
| 89bbca | P13 | BOGOF | 42 | 128 |
| f41256 | P15 | 500 Cashback | 58 | 128 |
| e3929b | P12 | 50% OFF | 98 | 128 |
| df4373 | P07 | BOGOF | 33 | 128 |
| 5a0c33 | P10 | 50% OFF | 87 | 127 |
| 6bbadf | P14 | BOGOF | 43 | 127 |
| 98cc83 | P10 | 50% OFF | 84 | 127 |
| 38b760 | P14 | BOGOF | 33 | 126 |
| 5ea63d | P12 | 50% OFF | 82 | 126 |
| e2f806 | P14 | BOGOF | 36 | 126 |
| da5d21 | P10 | 50% OFF | 92 | 125 |
| 127984 | P04 | 25% OFF | 141 | 125 |
| 7b1d41 | P14 | BOGOF | 43 | 125 |
| c5f80e | P14 | BOGOF | 43 | 125 |
| e2c229 | P15 | 500 Cashback | 54 | 125 |
| d7e3d8 | P13 | BOGOF | 36 | 124 |
| 879d99 | P09 | 50% OFF | 92 | 124 |
| 9413a7 | P11 | 50% OFF | 80 | 124 |
| 4e0e90 | P12 | 50% OFF | 80 | 124 |
| 669d35 | P12 | 50% OFF | 108 | 124 |
| 3426bd | P10 | 50% OFF | 80 | 124 |
| b79fd9 | P04 | 25% OFF | 150 | 123 |
| cd3392 | P07 | BOGOF | 31 | 123 |
| 367e8d | P07 | BOGOF | 30 | 123 |
| 4f75fe | P08 | BOGOF | 42 | 123 |
| 9154f0 | P11 | 50% OFF | 91 | 123 |
| c3bbcc | P07 | BOGOF | 31 | 122 |
| a0d919 | P08 | BOGOF | 35 | 122 |
| 316cd1 | P07 | BOGOF | 45 | 122 |
| a50d87 | P10 | 50% OFF | 82 | 122 |
| a26e60 | P13 | BOGOF | 36 | 122 |
| 4e6a19 | P07 | BOGOF | 45 | 121 |
| a340fc | P05 | 25% OFF | 136 | 121 |
| f4192d | P11 | 50% OFF | 84 | 121 |
| 23ef05 | P12 | 50% OFF | 78 | 121 |
| 93e61f | P10 | 50% OFF | 92 | 120 |
| e7cb59 | P11 | 50% OFF | 96 | 120 |
| 6bce12 | P07 | BOGOF | 46 | 120 |
| 9ff4a9 | P10 | 50% OFF | 94 | 120 |
| d85264 | P07 | BOGOF | 30 | 120 |
| e8aca2 | P08 | BOGOF | 40 | 119 |
| 323aee | P07 | BOGOF | 36 | 119 |
| 5d5637 | P09 | 50% OFF | 94 | 119 |
| be3489 | P14 | BOGOF | 38 | 119 |
| d2dc77 | P13 | BOGOF | 40 | 119 |
| a9ae21 | P12 | 50% OFF | 80 | 119 |
| 6436da | P08 | BOGOF | 30 | 118 |
| 11178a | P07 | BOGOF | 36 | 118 |
| a37f93 | P14 | BOGOF | 38 | 117 |
| 0f2c3a | P07 | BOGOF | 30 | 117 |
| 565a38 | P07 | BOGOF | 30 | 117 |
| b83644 | P11 | 50% OFF | 75 | 117 |
| cc2182 | P12 | 50% OFF | 85 | 117 |
| cf0ccd | P08 | BOGOF | 35 | 117 |
| e716e7 | P09 | 50% OFF | 78 | 117 |
| 8.02E+96 | P11 | 50% OFF | 91 | 116 |
| ff43bf | P11 | 50% OFF | 91 | 116 |
| 417902 | P08 | BOGOF | 29 | 116 |
| 24054f | P09 | 50% OFF | 89 | 116 |
| fe2fe7 | P05 | 25% OFF | 127 | 115 |
| 512d92 | P09 | 50% OFF | 87 | 115 |
| 0b38d9 | P08 | BOGOF | 29 | 115 |
| 46917a | P12 | 50% OFF | 105 | 115 |
| 37cb87 | P07 | BOGOF | 46 | 115 |
| f97b6d | P07 | BOGOF | 33 | 115 |
| 6dae49 | P05 | 25% OFF | 117 | 114 |
| 7ae5f8 | P11 | 50% OFF | 87 | 114 |
| 3080c6 | P14 | BOGOF | 38 | 114 |
| 2e0950 | P05 | 25% OFF | 133 | 114 |
| 0eb526 | P07 | BOGOF | 38 | 113 |
| ae288b | P11 | 50% OFF | 89 | 113 |
| d671d3 | P12 | 50% OFF | 91 | 113 |
| e391bc | P09 | 50% OFF | 77 | 113 |
| d0f417 | P12 | 50% OFF | 89 | 112 |
| 627200 | P14 | BOGOF | 36 | 111 |
| d105db | P07 | BOGOF | 43 | 111 |
| fa5b45 | P08 | BOGOF | 27 | 109 |
| 61b929 | P14 | BOGOF | 33 | 109 |
| 5aa413 | P08 | BOGOF | 43 | 109 |
| 191614 | P10 | 50% OFF | 103 | 109 |
| 339bf7 | P05 | 25% OFF | 127 | 109 |
| 8d7458 | P12 | 50% OFF | 98 | 109 |
| 9ebcf9 | P10 | 50% OFF | 80 | 109 |
| a298bc | P07 | BOGOF | 33 | 109 |
| b1a501 | P11 | 50% OFF | 80 | 108 |
| 7.83E+87 | P14 | BOGOF | 31 | 108 |
| 3af058 | P07 | BOGOF | 36 | 108 |
| fb2c04 | P08 | BOGOF | 28 | 108 |
| ad1849 | P05 | 25% OFF | 119 | 107 |
| e8a904 | P05 | 25% OFF | 112 | 107 |
| 4f570c | P05 | 25% OFF | 122 | 107 |
| 311946 | P05 | 25% OFF | 119 | 107 |
| 9a13a5 | P11 | 50% OFF | 82 | 107 |
| d58c29 | P08 | BOGOF | 27 | 107 |
| e025ee | P07 | BOGOF | 27 | 107 |
| ba7fb5 | P05 | 25% OFF | 119 | 107 |
| faeeb8 | P09 | 50% OFF | 80 | 107 |
| c381ea | P08 | BOGOF | 27 | 106 |
| 1fa488 | P07 | BOGOF | 31 | 105 |
| a0dc46 | P05 | 25% OFF | 129 | 104 |
| 5bbf38 | P09 | 50% OFF | 78 | 104 |
| bd3f78 | P11 | 50% OFF | 68 | 104 |
| 9.90E+87 | P05 | 25% OFF | 117 | 104 |
| fb4f00 | P11 | 50% OFF | 80 | 102 |
| 567271 | P10 | 50% OFF | 78 | 102 |
| 73ad85 | P05 | 25% OFF | 106 | 102 |
| ff02ae | P11 | 50% OFF | 66 | 102 |
| e4b7e4 | P09 | 50% OFF | 78 | 102 |
| cca40f | P12 | 50% OFF | 73 | 102 |
| e2c5f7 | P08 | BOGOF | 31 | 102 |
| b7db9e | P05 | 25% OFF | 106 | 101 |
| 108d5a | P14 | BOGOF | 29 | 101 |
| 42ba27 | P05 | 25% OFF | 115 | 101 |

---

Q3. DISTINCT Promotion Types
Find all unique promotion types used in the dataset.

Display only the unique promo_type values.

Concepts:
DISTINCT.

Query - 

-- Q3 
SELECT DISTINCT promo_type
FROM fact_events;

Query Answer - 
| promo_type |
|---|
| 50% OFF |
| 25% OFF |
| BOGOF |
| 500 Cashback |
| 33% OFF |

---

Q4. Basic Aggregation
Calculate the following for the complete fact_events table:

- Total number of events
- Total quantity sold before promotion
- Total quantity sold after promotion
- Average base price
- Maximum base price
- Minimum base price

Return all metrics in one row.

Concepts:
COUNT, SUM, AVG, MAX, MIN.

Query - 
-- Q4
 SELECT
    COUNT(*),
    SUM(`quantity_sold(before_promo)`),
    SUM(`quantity_sold(after_promo)`),
    AVG(base_price) ,
    MAX(base_price) ,
    MIN(base_price) 
FROM fact_events;

Query Answer - 
| event_count | total_before | total_after | avg_base_price | max_base_price | min_base_price |
|---|---|---|---|---|---|
| 1500 | 209050 | 435473 | 551.9667 | 3000 | 50 |

---

Q5. Sales Volume by Promotion Type
For each promo_type, calculate:

- Number of events
- Total quantity sold before promotion
- Total quantity sold after promotion

Sort by total quantity sold after promotion in descending order.

Concepts:
GROUP BY, COUNT, SUM, ORDER BY.

Query - 
-- Q5
SELECT
    promo_type,
    COUNT(*) AS event_count,
    SUM(quantity_sold(before_promo)) AS total_before,
    SUM(quantity_sold(after_promo)) AS total_after
FROM fact_events
GROUP BY promo_type
ORDER BY total_after DESC;

Query Answer - 
| promo_type | event_count | total_before | total_after |
|---|---|---|---|
| BOGOF | 500 | 58180 | 215253 |
| 33% OFF | 200 | 63321 | 90576 |
| 500 Cashback | 100 | 22299 | 63180 |
| 25% OFF | 400 | 44007 | 38290 |
| 50% OFF | 300 | 21243 | 28174 |

---

Q6. Promotion Uplift
For every promotion type, calculate:

- Total quantity before promotion
- Total quantity after promotion
- Quantity increase/decrease

Use:

Quantity Change = After Promo Quantity - Before Promo Quantity

Display:
- promo_type
- total_before
- total_after
- quantity_change

Sort by quantity_change descending.

Concepts:
GROUP BY, SUM, arithmetic calculations, aliases.

Query - 
-- Q6
SELECT
    fe.promo_type,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    SUM(fe.`quantity_sold(after_promo)`) 
        - SUM(fe.`quantity_sold(before_promo)`) AS quantity_change
FROM fact_events AS fe
GROUP BY fe.promo_type
ORDER BY quantity_change DESC; 

Query Answer - 
| promo_type | total_before | total_after | quantity_change |
|---|---|---|---|
| BOGOF | 58180 | 215253 | 157073 |
| 500 Cashback | 22299 | 63180 | 40881 |
| 33% OFF | 63321 | 90576 | 27255 |
| 50% OFF | 21243 | 28174 | 6931 |
| 25% OFF | 44007 | 38290 | -5717 |

---

============================================================
MEDIUM QUESTIONS
============================================================

Q7. Product Performance
Using fact_events and dim_products, calculate total quantity sold after promotion for every product.

Display:
- product_code
- product_name
- category
- total quantity after promotion

Sort by total quantity after promotion descending.

Concepts:
INNER JOIN, GROUP BY, SUM, ORDER BY.

Query -
-- Q7
SELECT
    dp.product_code,
    dp.product_name,
    dp.category,
    SUM(fe.`quantity_sold(after_promo)`) AS total_quantity_after
FROM fact_events AS fe
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY
    dp.product_code,
    dp.product_name,
    dp.category
ORDER BY total_quantity_after DESC; 

Query Answer - 
| product_code | product_name | category | total_quantity_after |
|---|---|---|---|
| P04 | Atliq_Farm_Chakki_Atta (1KG) | Grocery & Staples | 81290 |
| P03 | Atliq_Suflower_Oil (1L) | Grocery & Staples | 74478 |
| P15 | Atliq_Home_Essential_8_Product_Combo | Combo1 | 63180 |
| P02 | Atliq_Sonamasuri_Rice (10KG) | Grocery & Staples | 53235 |
| P01 | Atliq_Masoor_Dal (1KG) | Grocery & Staples | 37341 |
| P13 | Atliq_High_Glo_15W_LED_Bulb | Home Appliances | 29928 |
| P14 | Atliq_waterproof_Immersion_Rod | Home Appliances | 23685 |
| P07 | Atliq_Curtains | Home Care | 16317 |
| P08 | Atliq_Double_Bedsheet_set | Home Care | 15058 |
| P12 | Atliq_Lime_Cool_Bathing_Bar (125GM) | Personal Care | 10280 |
| P10 | Atliq_Cream_Beauty_Bathing_Soap (125GM) | Personal Care | 7697 |
| P11 | Atliq_Doodh_Kesar_Body_Lotion (200ML) | Personal Care | 7022 |
| P09 | Atliq_Body_Milk_Nourishing_Lotion (120ML) | Personal Care | 6505 |
| P05 | Atliq_Scrub_Sponge_For_Dishwash | Home Care | 4985 |
| P06 | Atliq_Fusion_Container_Set_of_3 | Home Care | 4472 |

---

Q8. Category-Level Performance
Using fact_events and dim_products, calculate for every product category:

- Number of events
- Total quantity before promotion
- Total quantity after promotion
- Quantity change

Sort categories by total quantity after promotion descending.

Concepts:
JOIN, GROUP BY, SUM, COUNT, arithmetic calculations.

Query - 
-- Q8
SELECT
    dp.category,
    COUNT(*) AS event_count,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    SUM(fe.`quantity_sold(after_promo)`) 
        - SUM(fe.`quantity_sold(before_promo)`) AS quantity_change
FROM fact_events AS fe
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY dp.category
ORDER BY total_after DESC;

Query Answer - 
| category | event_count | total_before | total_after | quantity_change |
|---|---|---|---|---|
| Grocery & Staples | 400 | 126970 | 246344 | 119374 |
| Combo1 | 100 | 22299 | 63180 | 40881 |
| Home Appliances | 200 | 14713 | 53613 | 38900 |
| Home Care | 400 | 19764 | 40832 | 21068 |
| Personal Care | 400 | 25304 | 31504 | 6200 |

---

Q9. Store Performance
Using fact_events and dim_stores, calculate for every city:

- Number of promotional events
- Total quantity before promotion
- Total quantity after promotion

Display:
- city
- event_count
- total_before
- total_after

Sort cities by total_after descending.

Concepts:
JOIN, GROUP BY, aggregation, ORDER BY.

Query - 
-- Q9
SELECT
    ds.city,
    COUNT(*) AS event_count,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after
FROM fact_events AS fe
JOIN dim_stores AS ds
    ON fe.store_id = ds.store_id
GROUP BY ds.city
ORDER BY total_after DESC; 

Query Answer -
| city | event_count | total_before | total_after |
|---|---|---|---|
| Bengaluru | 300 | 49171 | 105141 |
| Chennai | 240 | 39505 | 83273 |
| Hyderabad | 210 | 34363 | 69399 |
| Coimbatore | 150 | 18150 | 38900 |
| Mysuru | 120 | 18569 | 37470 |
| Visakhapatnam | 150 | 17175 | 33916 |
| Madurai | 120 | 14458 | 31169 |
| Mangalore | 90 | 7529 | 14929 |
| Vijayawada | 60 | 5297 | 11106 |
| Trivandrum | 60 | 4833 | 10170 |

---

Q10. Campaign Performance
Using fact_events and dim_campaigns, calculate for each campaign:

- Campaign name
- Start date
- End date
- Number of events
- Total quantity before promotion
- Total quantity after promotion

Sort by total quantity after promotion descending.

Concepts:
JOIN, GROUP BY, date columns, aggregation.

Query - 
-- Q10
SELECT
    dc.campaign_name,
    dc.start_date,
    dc.end_date,
    COUNT(*) AS event_count,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after
FROM fact_events AS fe
JOIN dim_campaigns AS dc
    ON fe.campaign_id = dc.campaign_id
GROUP BY
    dc.campaign_name,
    dc.start_date,
    dc.end_date
ORDER BY total_after DESC; 

Query Answer - 
| campaign_name | start_date | end_date | event_count | total_before | total_after |
|---|---|---|---|---|---|
| Sankranti | 2024-01-10 | 2024-01-16 | 750 | 98731 | 252069 |
| Diwali | 2023-11-12 | 2023-11-18 | 750 | 110319 | 183404 |

---

Q11. Product Category with HAVING
Find product categories where the total quantity sold after promotion is greater than 1,000.

Display:
- category
- total quantity after promotion
- average base price

Sort by total quantity after promotion descending.

Concepts:
JOIN, GROUP BY, HAVING, AVG, SUM.

Query - 
-- Q11 
SELECT
    dp.category,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    AVG(fe.base_price) AS avg_price
FROM fact_events AS fe
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY dp.category
HAVING SUM(fe.`quantity_sold(after_promo)`) > 1000
ORDER BY total_after DESC;

Query Answer - 
| category | total_after | avg_price |
|---|---|---|
| Grocery & Staples | 246344 | 385.0000 |
| Combo1 | 63180 | 3000.0000 |
| Home Appliances | 53613 | 685.0000 |
| Home Care | 40832 | 490.0000 |
| Personal Care | 31504 | 102.3750 |

---

Q12. Store + Category Analysis
Using fact_events, dim_stores and dim_products, calculate total quantity sold after promotion for every combination of:

- City
- Product category

Display:
- city
- category
- total quantity after promotion

Sort first by city and then by total quantity descending.

Concepts:
Multiple JOINs, GROUP BY, ORDER BY.

Query - 
-- Q12
SELECT
    ds.city,
    dp.category,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after
FROM fact_events AS fe
JOIN dim_stores AS ds
    ON fe.store_id = ds.store_id
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY
    ds.city,
    dp.category
ORDER BY
    ds.city,
    total_after DESC; 

Query Answer - 
| city | category | total_after |
|---|---|---|
| Bengaluru | Grocery & Staples | 59431 |
| Bengaluru | Combo1 | 15250 |
| Bengaluru | Home Appliances | 12909 |
| Bengaluru | Home Care | 10006 |
| Bengaluru | Personal Care | 7545 |
| Chennai | Grocery & Staples | 46639 |
| Chennai | Combo1 | 12081 |
| Chennai | Home Appliances | 10686 |
| Chennai | Home Care | 7974 |
| Chennai | Personal Care | 5893 |
| Coimbatore | Grocery & Staples | 22735 |
| Coimbatore | Combo1 | 5369 |
| Coimbatore | Home Appliances | 4606 |
| Coimbatore | Home Care | 3527 |
| Coimbatore | Personal Care | 2663 |
| Hyderabad | Grocery & Staples | 39488 |
| Hyderabad | Combo1 | 9337 |
| Hyderabad | Home Appliances | 8466 |
| Hyderabad | Home Care | 6691 |
| Hyderabad | Personal Care | 5417 |
| Madurai | Grocery & Staples | 17307 |
| Madurai | Combo1 | 5258 |
| Madurai | Home Appliances | 3927 |
| Madurai | Home Care | 2754 |
| Madurai | Personal Care | 1923 |
| Mangalore | Grocery & Staples | 8539 |
| Mangalore | Combo1 | 2146 |
| Mangalore | Home Appliances | 1789 |
| Mangalore | Home Care | 1391 |
| Mangalore | Personal Care | 1064 |
| Mysuru | Grocery & Staples | 20699 |
| Mysuru | Combo1 | 6124 |
| Mysuru | Home Appliances | 4408 |
| Mysuru | Home Care | 3420 |
| Mysuru | Personal Care | 2819 |
| Trivandrum | Grocery & Staples | 5752 |
| Trivandrum | Combo1 | 1357 |
| Trivandrum | Home Appliances | 1346 |
| Trivandrum | Home Care | 989 |
| Trivandrum | Personal Care | 726 |
| Vijayawada | Grocery & Staples | 6249 |
| Vijayawada | Combo1 | 1653 |
| Vijayawada | Home Appliances | 1403 |
| Vijayawada | Home Care | 992 |
| Vijayawada | Personal Care | 809 |
| Visakhapatnam | Grocery & Staples | 19505 |
| Visakhapatnam | Combo1 | 4605 |
| Visakhapatnam | Home Appliances | 4073 |
| Visakhapatnam | Home Care | 3088 |
| Visakhapatnam | Personal Care | 2645 |

---

Q13. Promotion Effectiveness by Product
For each product, calculate:

- Product name
- Category
- Total quantity before promotion
- Total quantity after promotion
- Quantity change
- Percentage change

Use:

Percentage Change =
((After Promo - Before Promo) / Before Promo) * 100

Handle division by zero appropriately.

Sort by percentage change descending.

Concepts:
JOIN, GROUP BY, arithmetic calculations, NULLIF, percentage calculations.

Query - 
-- Q13
SELECT
    dp.product_name,
    dp.category,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    SUM(fe.`quantity_sold(after_promo)`) 
        - SUM(fe.`quantity_sold(before_promo)`) AS quantity_change,
    (
        (
            SUM(fe.`quantity_sold(after_promo)`) 
            - SUM(fe.`quantity_sold(before_promo)`)
        )
        / NULLIF(SUM(fe.`quantity_sold(before_promo)`), 0)
    ) * 100 AS percentage_change
FROM fact_events AS fe
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY
    dp.product_code,
    dp.product_name,
    dp.category
ORDER BY percentage_change DESC;

Query Answer - 
| product_name | category | total_before | total_after | quantity_change | percentage_change |
|---|---|---|---|---|---|
| Atliq_waterproof_Immersion_Rod | Home Appliances | 6468 | 23685 | 17217 | 266.1874 |
| Atliq_High_Glo_15W_LED_Bulb | Home Appliances | 8245 | 29928 | 21683 | 262.9836 |
| Atliq_Double_Bedsheet_set | Home Care | 4203 | 15058 | 10855 | 258.2679 |
| Atliq_Curtains | Home Care | 4592 | 16317 | 11725 | 255.3354 |
| Atliq_Home_Essential_8_Product_Combo | Combo1 | 22299 | 63180 | 40881 | 183.3311 |
| Atliq_Farm_Chakki_Atta (1KG) | Grocery & Staples | 32340 | 81290 | 48950 | 151.3605 |
| Atliq_Suflower_Oil (1L) | Grocery & Staples | 31309 | 74478 | 43169 | 137.8805 |
| Atliq_Masoor_Dal (1KG) | Grocery & Staples | 26040 | 37341 | 11301 | 43.3986 |
| Atliq_Sonamasuri_Rice (10KG) | Grocery & Staples | 37281 | 53235 | 15954 | 42.7939 |
| Atliq_Doodh_Kesar_Body_Lotion (200ML) | Personal Care | 5257 | 7022 | 1765 | 33.5743 |
| Atliq_Lime_Cool_Bathing_Bar (125GM) | Personal Care | 7718 | 10280 | 2562 | 33.1951 |
| Atliq_Cream_Beauty_Bathing_Soap (125GM) | Personal Care | 6380 | 7697 | 1317 | 20.6426 |
| Atliq_Body_Milk_Nourishing_Lotion (120ML) | Personal Care | 5949 | 6505 | 556 | 9.3461 |
| Atliq_Scrub_Sponge_For_Dishwash | Home Care | 5762 | 4985 | -777 | -13.4849 |
| Atliq_Fusion_Container_Set_of_3 | Home Care | 5207 | 4472 | -735 | -14.1156 |

---

Q14. Campaign and Promotion Type Analysis
For each campaign and promo_type combination, calculate:

- Number of events
- Total quantity before promotion
- Total quantity after promotion
- Quantity change

Display:
- campaign_name
- promo_type
- event_count
- total_before
- total_after
- quantity_change

Sort by campaign_name and quantity_change descending.

Concepts:
Multiple GROUP BY columns, JOIN, aggregation, ORDER BY.

Query - 
-- Q14
SELECT
    dc.campaign_name,
    fe.promo_type,
    COUNT(*) AS event_count,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    SUM(fe.`quantity_sold(after_promo)`) 
        - SUM(fe.`quantity_sold(before_promo)`) AS quantity_change
FROM fact_events AS fe
JOIN dim_campaigns AS dc
    ON fe.campaign_id = dc.campaign_id
GROUP BY
    dc.campaign_name,
    fe.promo_type
ORDER BY
    dc.campaign_name,
    quantity_change DESC;

Query Answer - 
| campaign_name | promo_type | event_count | total_before | total_after | quantity_change |
|---|---|---|---|---|---|
| Diwali | 500 Cashback | 50 | 16791 | 50769 | 33978 |
| Diwali | BOGOF | 200 | 10024 | 34461 | 24437 |
| Diwali | 33% OFF | 100 | 29152 | 43117 | 13965 |
| Diwali | 50% OFF | 200 | 16843 | 22074 | 5231 |
| Diwali | 25% OFF | 200 | 37509 | 32983 | -4526 |
| Sankranti | BOGOF | 300 | 48156 | 180792 | 132636 |
| Sankranti | 33% OFF | 100 | 34169 | 47459 | 13290 |
| Sankranti | 500 Cashback | 50 | 5508 | 12411 | 6903 |
| Sankranti | 50% OFF | 100 | 4400 | 6100 | 1700 |
| Sankranti | 25% OFF | 200 | 6498 | 5307 | -1191 |

---

Q15. Product Revenue Before and After Promotion
For each product, calculate:

1. Revenue before promotion =
   base_price × quantity_sold(before_promo)

2. Revenue after promotion =
   base_price × quantity_sold(after_promo)

3. Revenue difference =
   Revenue after - Revenue before

Display:
- product_name
- category
- revenue_before
- revenue_after
- revenue_difference

Sort by revenue_difference descending.

Concepts:
JOIN, GROUP BY, SUM, arithmetic calculations, aliases.

Query - 
-- Q15
SELECT
    dp.product_name,
    dp.category,
    SUM(
        fe.base_price * fe.`quantity_sold(before_promo)`
    ) AS revenue_before,
    SUM(
        fe.base_price * fe.`quantity_sold(after_promo)`
    ) AS revenue_after,
    SUM(
        fe.base_price * fe.`quantity_sold(after_promo)`
    )
    -
    SUM(
        fe.base_price * fe.`quantity_sold(before_promo)`
    ) AS revenue_difference
FROM fact_events AS fe
JOIN dim_products AS dp
    ON fe.product_code = dp.product_code
GROUP BY
    dp.product_code,
    dp.product_name,
    dp.category
ORDER BY revenue_difference DESC; 

Query Answer - 
| product_name | category | revenue_before | revenue_after | revenue_difference |
|---|---|---|---|---|
| Atliq_Home_Essential_8_Product_Combo | Combo1 | 66897000 | 189540000 | 122643000 |
| Atliq_Farm_Chakki_Atta (1KG) | Grocery & Staples | 10851800 | 29100500 | 18248700 |
| Atliq_waterproof_Immersion_Rod | Home Appliances | 6597360 | 24158700 | 17561340 |
| Atliq_Sonamasuri_Rice (10KG) | Grocery & Staples | 32061660 | 45782100 | 13720440 |
| Atliq_Double_Bedsheet_set | Home Care | 5001570 | 17919020 | 12917450 |
| Atliq_Suflower_Oil (1L) | Grocery & Staples | 5599512 | 14310708 | 8711196 |
| Atliq_High_Glo_15W_LED_Bulb | Home Appliances | 2885750 | 10474800 | 7589050 |
| Atliq_Curtains | Home Care | 1377600 | 4895100 | 3517500 |
| Atliq_Masoor_Dal (1KG) | Grocery & Staples | 4478880 | 6422652 | 1943772 |
| Atliq_Doodh_Kesar_Body_Lotion (200ML) | Personal Care | 998830 | 1334180 | 335350 |
| Atliq_Lime_Cool_Bathing_Bar (125GM) | Personal Care | 478516 | 637360 | 158844 |
| Atliq_Cream_Beauty_Bathing_Soap (125GM) | Personal Care | 393625 | 483145 | 89520 |
| Atliq_Body_Milk_Nourishing_Lotion (120ML) | Personal Care | 601270 | 671830 | 70560 |
| Atliq_Scrub_Sponge_For_Dishwash | Home Care | 316910 | 274175 | -42735 |
| Atliq_Fusion_Container_Set_of_3 | Home Care | 2160905 | 1855880 | -305025 |

---

Q16. Classify Promotion Performance
For every promotion type, calculate total quantity before and after promotion.

Then classify the promotion using CASE:

- Percentage change >= 50% → "High Impact"
- Percentage change >= 20% → "Medium Impact"
- Percentage change < 20% → "Low Impact"

Display:
- promo_type
- total_before
- total_after
- percentage_change
- performance_category

Sort by percentage_change descending.

Concepts:
GROUP BY, CASE, arithmetic calculations, NULLIF, aliases.

Query - 
-- Q16
SELECT
    fe.promo_type,
    SUM(fe.`quantity_sold(before_promo)`) AS total_before,
    SUM(fe.`quantity_sold(after_promo)`) AS total_after,
    (
        (
            SUM(fe.`quantity_sold(after_promo)`)
            - SUM(fe.`quantity_sold(before_promo)`)
        )
        / NULLIF(SUM(fe.`quantity_sold(before_promo)`), 0)
    ) * 100 AS percentage_change,

    CASE
        WHEN (
            (
                SUM(fe.`quantity_sold(after_promo)`)
                - SUM(fe.`quantity_sold(before_promo)`)
            )
            / NULLIF(SUM(fe.`quantity_sold(before_promo)`), 0)
        ) * 100
        >= 50 THEN 'High Impact'

        WHEN (
            (
                SUM(fe.`quantity_sold(after_promo)`)
                - SUM(fe.`quantity_sold(before_promo)`)
            )
            / NULLIF(SUM(fe.`quantity_sold(before_promo)`), 0)
        ) * 100
        >= 20 THEN 'Medium Impact'

        ELSE 'Low Impact'
    END AS performance_category

FROM fact_events AS fe
GROUP BY fe.promo_type
ORDER BY percentage_change DESC; 

Query Answer - 
| promo_type | total_before | total_after | percentage_change | performance_category |
|---|---|---|---|---|
| BOGOF | 58180 | 215253 | 269.9777 | High Impact |
| 500 Cashback | 22299 | 63180 | 183.3311 | High Impact |
| 33% OFF | 63321 | 90576 | 43.0426 | Medium Impact |
| 50% OFF | 21243 | 28174 | 32.6272 | Medium Impact |
| 25% OFF | 44007 | 38290 | -12.9911 | Low Impact |

---

============================================================
HARD QUESTIONS
============================================================

Q17. Top Products Within Each Category
Using a CTE:

1. Calculate total quantity sold after promotion for every product.
2. Rank products within each category based on total quantity sold after promotion.
3. Return only the top 2 products from every category.

Display:
- category
- product_name
- total_quantity_after
- category_rank

Concepts:
CTE, JOIN, GROUP BY, DENSE_RANK/ROW_NUMBER,
PARTITION BY, window functions.

Query - 
-- Q17 
WITH product_sales AS
(
    SELECT
        dp.product_code,
        dp.product_name,
        dp.category,
        SUM(fe.`quantity_sold(after_promo)`) AS total_quantity_after
    FROM fact_events AS fe
    JOIN dim_products AS dp
        ON fe.product_code = dp.product_code
    GROUP BY
        dp.product_code,
        dp.product_name
),

ranked_products AS
(
    SELECT
        category,
        product_name,
        total_quantity_after,
        DENSE_RANK() OVER (
            PARTITION BY category
            ORDER BY total_quantity_after DESC
        ) AS category_rank
    FROM product_sales
)

SELECT
    category,
    product_name,
    total_quantity_after,
    category_rank
FROM ranked_products
WHERE category_rank <= 2
ORDER BY
    category,
    category_rank;

Query Answer - 
| category | product_name | total_quantity_after | category_rank |
|---|---|---|---|
| Combo1 | Atliq_Home_Essential_8_Product_Combo | 63180 | 1 |
| Grocery & Staples | Atliq_Farm_Chakki_Atta (1KG) | 81290 | 1 |
| Grocery & Staples | Atliq_Suflower_Oil (1L) | 74478 | 2 |
| Home Appliances | Atliq_High_Glo_15W_LED_Bulb | 29928 | 1 |
| Home Appliances | Atliq_waterproof_Immersion_Rod | 23685 | 2 |
| Home Care | Atliq_Curtains | 16317 | 1 |
| Home Care | Atliq_Double_Bedsheet_set | 15058 | 2 |
| Personal Care | Atliq_Lime_Cool_Bathing_Bar (125GM) | 10280 | 1 |
| Personal Care | Atliq_Cream_Beauty_Bathing_Soap (125GM) | 7697 | 2 |

---

Q18. Best-Performing Stores Within Each City
Calculate total quantity sold after promotion for each store.

Join dim_stores to obtain the city.

Then rank stores within each city based on total quantity sold after promotion.

Return the top 2 stores from each city.

Display:
- city
- store_id
- total_quantity_after
- city_rank

Concepts:
JOIN, CTE, GROUP BY, window functions,
PARTITION BY, RANK/DENSE_RANK.

Query - 
-- Q18
WITH store_sales AS
(
    SELECT
        ds.city,
        fe.store_id,
        SUM(fe.`quantity_sold(after_promo)`) AS total_quantity_after
    FROM fact_events AS fe
    JOIN dim_stores AS ds
        ON fe.store_id = ds.store_id
    GROUP BY
        ds.city,
        fe.store_id
),

ranked_stores AS
(
    SELECT
        city,
        store_id,
        total_quantity_after,
        DENSE_RANK() OVER (
            PARTITION BY city
            ORDER BY total_quantity_after DESC
        ) AS city_rank
    FROM store_sales
)

SELECT
    city,
    store_id,
    total_quantity_after,
    city_rank
FROM ranked_stores
WHERE city_rank <= 2
ORDER BY
    city,
    city_rank;

Query Answer - 
| city | store_id | total_quantity_after | city_rank |
|---|---|---|---|
| Bengaluru | STBLR-7 | 11866 | 1 |
| Bengaluru | STBLR-6 | 11601 | 2 |
| Chennai | STCHE-4 | 11547 | 1 |
| Chennai | STCHE-7 | 11546 | 2 |
| Coimbatore | STCBE-0 | 8657 | 1 |
| Coimbatore | STCBE-2 | 8535 | 2 |
| Hyderabad | STHYD-2 | 10822 | 1 |
| Hyderabad | STHYD-0 | 10522 | 2 |
| Madurai | STMDU-0 | 8310 | 1 |
| Madurai | STMDU-2 | 7685 | 2 |
| Mangalore | STMLR-2 | 5253 | 1 |
| Mangalore | STMLR-1 | 5187 | 2 |
| Mysuru | STMYS-1 | 11773 | 1 |
| Mysuru | STMYS-3 | 9833 | 2 |
| Trivandrum | STTRV-0 | 5193 | 1 |
| Trivandrum | STTRV-1 | 4977 | 2 |
| Vijayawada | STVJD-0 | 5751 | 1 |
| Vijayawada | STVJD-1 | 5355 | 2 |
| Visakhapatnam | STVSK-1 | 7614 | 1 |
| Visakhapatnam | STVSK-0 | 7527 | 2 |

---

Q19. Campaign-Level Product Performance
For every campaign and product:

Calculate:
- Total quantity before promotion
- Total quantity after promotion
- Quantity change
- Percentage change

Then rank products within each campaign based on percentage change.

Return the top 3 products for every campaign.

Display:
- campaign_name
- product_name
- total_before
- total_after
- quantity_change
- percentage_change
- campaign_rank

Concepts:
Multiple JOINs, CTE, GROUP BY, arithmetic calculations,
NULLIF, window functions, PARTITION BY, ranking.

Query - 
-- Q19 
WITH campaign_products AS
(
    SELECT
        dc.campaign_name,
        dp.product_code,
        dp.product_name,

        SUM(fe.`quantity_sold(before_promo)`) AS total_before,

        SUM(fe.`quantity_sold(after_promo)`) AS total_after,

        SUM(fe.`quantity_sold(after_promo)`) - SUM(fe.`quantity_sold(before_promo)`) AS quantity_change,

        (
            (
                SUM(fe.`quantity_sold(after_promo)`)
                -
                SUM(fe.`quantity_sold(before_promo)`)
            )
            / NULLIF(
                SUM(fe.`quantity_sold(before_promo)`),
                0
            )
        ) * 100 AS percentage_change

    FROM fact_events AS fe

    JOIN dim_campaigns AS dc
        ON fe.campaign_id = dc.campaign_id

    JOIN dim_products AS dp
        ON fe.product_code = dp.product_code

    GROUP BY
        dc.campaign_name,
        dp.product_code,
        dp.product_name
),

ranked_products AS
(
    SELECT
        campaign_name,
        product_name,
        total_before,
        total_after,
        quantity_change,
        percentage_change,

        DENSE_RANK() OVER (
            PARTITION BY campaign_name
            ORDER BY percentage_change DESC
        ) AS campaign_rank

    FROM campaign_products
)

SELECT
    campaign_name,
    product_name,
    total_before,
    total_after,
    quantity_change,
    percentage_change,
    campaign_rank
FROM ranked_products
WHERE campaign_rank <= 3
ORDER BY
    campaign_name,
    campaign_rank; 

Query Answer - 
| campaign_name | product_name | total_before | total_after | quantity_change | percentage_change | campaign_rank |
|---|---|---|---|---|---|---|
| Diwali | Atliq_waterproof_Immersion_Rod | 2015 | 6950 | 4935 | 244.9132 | 1 |
| Diwali | Atliq_Curtains | 2680 | 9214 | 6534 | 243.8060 | 2 |
| Diwali | Atliq_High_Glo_15W_LED_Bulb | 3215 | 11053 | 7838 | 243.7947 | 3 |
| Sankranti | Atliq_Suflower_Oil (1L) | 16257 | 61185 | 44928 | 276.3610 | 1 |
| Sankranti | Atliq_waterproof_Immersion_Rod | 4453 | 16735 | 12282 | 275.8141 | 2 |
| Sankranti | Atliq_High_Glo_15W_LED_Bulb | 5030 | 18875 | 13845 | 275.2485 | 3 |

---

Q20. Complete Promotional Performance Analysis
Create a complete analytical report at the product-category level.

For every product, calculate:

- Product name
- Category
- Number of promotional events
- Total quantity before promotion
- Total quantity after promotion
- Quantity change
- Percentage change
- Revenue before promotion
- Revenue after promotion
- Revenue change
- Average base price
- Product rank within its category

Use:

Quantity Change =
Total After - Total Before

Percentage Change =
((Total After - Total Before) / Total Before) * 100

Revenue Before =
SUM(base_price × quantity_before)

Revenue After =
SUM(base_price × quantity_after)

Revenue Change =
Revenue After - Revenue Before

Then:

1. Rank products within each category by Revenue Change.
2. Return only the top 2 products from each category.
3. Use appropriate handling for division by zero.

Concepts:
- Multiple JOINs
- CTEs
- GROUP BY
- COUNT
- SUM
- AVG
- CASE
- NULLIF
- Arithmetic calculations
- Percentage calculations
- Window functions
- PARTITION BY
- DENSE_RANK / ROW_NUMBER
- Filtering ranked results
- Business analysis


Query - 
-- Q20 
WITH product_analysis AS
(
    SELECT
        dp.product_code,
        dp.product_name,
        dp.category,

        COUNT(*) AS event_count,

        SUM(fe.`quantity_sold(before_promo)`) AS total_before,

        SUM(fe.`quantity_sold(after_promo)`) AS total_after,

        SUM(fe.`quantity_sold(after_promo)`)
        -
        SUM(fe.`quantity_sold(before_promo)`) AS quantity_change,

        (
            (
                SUM(fe.`quantity_sold(after_promo)`)
                -
                SUM(fe.`quantity_sold(before_promo)`)
            )
            / NULLIF(
                SUM(fe.`quantity_sold(before_promo)`),
                0
            )
        ) * 100 AS percentage_change,

        SUM(
            fe.base_price *
            fe.`quantity_sold(before_promo)`
        ) AS revenue_before,

        SUM(
            fe.base_price *
            fe.`quantity_sold(after_promo)`
        ) AS revenue_after,

        SUM(
            fe.base_price *
            fe.`quantity_sold(after_promo)`
        )
        -
        SUM(
            fe.base_price *
            fe.`quantity_sold(before_promo)`
        ) AS revenue_change,

        AVG(fe.base_price) AS avg_base_price

    FROM fact_events AS fe

    JOIN dim_products AS dp
        ON fe.product_code = dp.product_code

    GROUP BY
        dp.product_code,
        dp.product_name,
        dp.category
),

ranked_products AS
(
    SELECT
        product_name,
        category,
        event_count,
        total_before,
        total_after,
        quantity_change,
        percentage_change,
        revenue_before,
        revenue_after,
        revenue_change,
        avg_base_price,

        DENSE_RANK() OVER (
            PARTITION BY category
            ORDER BY revenue_change DESC
        ) AS product_rank

    FROM product_analysis
)

SELECT
    product_name,
    category,
    event_count,
    total_before,
    total_after,
    quantity_change,
    percentage_change,
    revenue_before,
    revenue_after,
    revenue_change,
    avg_base_price,
    product_rank
FROM ranked_products
WHERE product_rank <= 2
ORDER BY
    category,
    product_rank;

Query Answer - 
| product_name | category | event_count | total_before | total_after | quantity_change | percentage_change | revenue_before | revenue_after | revenue_change | avg_base_price | product_rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Atliq_Home_Essential_8_Product_Combo | Combo1 | 100 | 22299 | 63180 | 40881 | 183.3311 | 66897000 | 189540000 | 122643000 | 3000.0000 | 1 |
| Atliq_Farm_Chakki_Atta (1KG) | Grocery & Staples | 100 | 32340 | 81290 | 48950 | 151.3605 | 10851800 | 29100500 | 18248700 | 330.0000 | 1 |
| Atliq_Sonamasuri_Rice (10KG) | Grocery & Staples | 100 | 37281 | 53235 | 15954 | 42.7939 | 32061660 | 45782100 | 13720440 | 860.0000 | 2 |
| Atliq_waterproof_Immersion_Rod | Home Appliances | 100 | 6468 | 23685 | 17217 | 266.1874 | 6597360 | 24158700 | 17561340 | 1020.0000 | 1 |
| Atliq_High_Glo_15W_LED_Bulb | Home Appliances | 100 | 8245 | 29928 | 21683 | 262.9836 | 2885750 | 10474800 | 7589050 | 350.0000 | 2 |
| Atliq_Double_Bedsheet_set | Home Care | 100 | 4203 | 15058 | 10855 | 258.2679 | 5001570 | 17919020 | 12917450 | 1190.0000 | 1 |
| Atliq_Curtains | Home Care | 100 | 4592 | 16317 | 11725 | 255.3354 | 1377600 | 4895100 | 3517500 | 300.0000 | 2 |
| Atliq_Doodh_Kesar_Body_Lotion (200ML) | Personal Care | 100 | 5257 | 7022 | 1765 | 33.5743 | 998830 | 1334180 | 335350 | 190.0000 | 1 |
| Atliq_Lime_Cool_Bathing_Bar (125GM) | Personal Care | 100 | 7718 | 10280 | 2562 | 33.1951 | 478516 | 637360 | 158844 | 62.0000 | 2 |
