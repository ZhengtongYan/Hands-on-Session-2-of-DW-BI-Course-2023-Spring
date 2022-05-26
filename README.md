# **Hands-on Session 2: OLAP Analysis With PostgreSQL**
**This repository contains the instructions of the second hands-on session in our DW&BI course.** 

**You need to complete the [first hands-on session](https://github.com/ZhengtongYan/Hands-on-Session-1-of-DW-BI-Course-2023-Spring) before you start the second one as you need to use the start schema created in the fisrt hands-on session.**

## **Recorded Video Links**


## **Learning Objectives**
Gain hands-on experience in conducting OLAP analysis using PostgreSQL. 



## **Exercises (20 points)**
In hands-on session 1, we focus on how to building a DW&BI application with PostgreSQL and Pentaho using the MOLAP model. In this hands-on session, we will utilize a different approach (i.e. ROLAP) to conduct the OLAP analysis only with PostgreSQL on the star schema.

**1. Full Star Join (5 points)**

Create a full star join by joining the fact table with all the dimension tables.

(1) Write three SQL queries using **three different syntax** for join operation. **(3 points)**
- WHERE clause, e.g., WHERE T1.id=T2.id
- INNER JOIN operation, e.g., T1 INNER JOIN T2 ON (T1.id=T2.id)
- USING keyword, e.g., T1 INNER JOIN T2 USING (id)

Those three different writing formats are based on different SQL standards. You can use * in the SELECT clause to reture everything.


(2) What are the surrogate key and business key in those tables? Why use the surrogate key in star schema? **(2 points)**


**2. Top-N Query (2 points)**

Find the top-3 customers who come from USA and spend the highest amount of money in the year of 2006. Return the customer_id and total dollars sold. 

Please use two different methods:
- Use GROUP BY, ORDER BY, and LIMIT Operators **(1 point)**
- Use windows function **(1 point)**

**3.Cube Creation (6 points)**

(1) Build an OLAP cube for *sales_year* (in date_dim table) and *product_status* (in product_dim table) dimensions to calculate the total amount sold. Sort the resluts by sales_year and product_status in **ascending orders**. **(1 point)**

(2) How many combinations of the two dimensional attributes are created in the cube? Based on these combinantions of dimensional attributes, create the same OLAP cube with **UNION** and **GROUP BY** keywords instead of **CUBE** keyword. Comapre and ensure that you can get the same results of using CUBE keyword. Sort the resluts by sales_year and product_status in **ascending orders.** **(2 point)**
 

(3) Replace the CUBE keyword with ROLLUP and GROUPING SETS keywords respectively, compare and exaplain these results? **(2 points)** 


**4.Pivot Table (2 points)**

(1) calculate the total dollars sold per city of USA and per month in 2006. **(1 point)** 

(2) Use the crosstab function (or crosstabview command in psql) to create a pivot table view to show the results in the previous step. **(1 point)** 

**Tips:** Please refer to the documentaion about crosstab function and pivot table:

- [**Crosstab for Pivot Table in PostgreSQL**](https://www.postgresql.org/docs/14/tablefunc.html)
- [**Pivot table in Wikipedia**](https://en.wikipedia.org/wiki/Pivot_table)


**5.Roll-up Operation (2 points)**

(1) Calculate the total amount per month, per year, per city, per product category, and per parent category. **DO NOT** use the CUBE keyword, **ONLY** use GROUP BY keyword to calculate the aggregation results. Please sort the results in **ascending orders** on each dimension. **(1 point)**

(2) Roll up the results on two dimensions: roll-up from month to year and roll-up from product category to parent category. Please sort the results in **ascending orders** on each dimension. **(1 point)**

**Tips**: Roll-up means that you need to remove some attributes in the GROUP BY clause.

**Notice:** Here the *roll-up operation* is a kind of OLAP operation which is not the same as the *ROLLUP function* in SQL.

**6.Drill-down Operation(2 points)**

(1) Calculate the total amount per country, per promotion name, and per product category. **DO NOT** use the CUBE keyword, **ONLY** use GROUP BY keyword to calculate the aggregation results. Please sort the results in **ascending orders** on each dimension. **(1 point)**

(2) Drill down the results on two dimensions: drill-down from country to city and drill-down from product category to sub-category. Please sort the results in **ascending orders** on each dimension. **(1 point)**

**Tips**: Drill-down means that you want to obtain more details on some dimensions, so you need to add some attributes in the GROUP BY clause.


**7.Slice Operation (2 points)**

(1) Calculate the total dollars sold per salesrep's department, per sales_year, per sales_quarter, and per product category. **DO NOT** use the CUBE keyword, **ONLY** use GROUP BY keyword to calculate the aggregation results. Please sort the results in **ascending orders** on each dimension. **(1 point)**

(2) Slicing the data cube on the first quarter in 2006. Please sort the results in **ascending orders** on each dimension. **(1 point)**


**8.Dice Operation (2 points)**

(1) Calculate the total dollars sold per promotion name, per city, per month. **DO NOT** use the CUBE keyword, **ONLY** use GROUP BY keyword to calculate the aggregation results. Please sort  the results in **ascending orders** on each dimension. **(1 point)**

(2) Dicing the data cube in two dimensions: city (Madison and Indianapolis) and month (January and Novemeber). Please sort the result in **ascending orders** on each dimension. **(1 point)**


## **Submission Requirements**: 
- Post the queries and demonstrate the results.
- Upload all the results in a single PDF file.
- Submit to Moodle page and the deadline is **xxxx xxx, 2023**.


## **Some Useful Links**
[**GROUPING SETS, CUBE, ROLLUP, and Window Function in PostgreSQL**](https://www.postgresql.org/docs/current/queries-table-expressions.html#QUERIES-GROUPING-SETS)

