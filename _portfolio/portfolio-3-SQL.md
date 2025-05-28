---
title: "03 SQL & Data Modeling -- Divvy Bike Sharing Service"
excerpt: "<span style='font-size:0.85em; color:#494e52;'>  
A SQL and data modeling project for a bike-sharing service. Focused on database interrogation, re-modeling, and business-level query design, this school project showcases advanced SQL skills, ER modeling, and strategic recommendations for operational efficiency... <br/><img src='/site/images/sql-list.jpg' style='width:50%;'/>"  
collection: portfolio
---

## Background
As part of a final project for the SQL module in my M.Sc. in Digital Marketing and Data Science program, I worked on a simulated challenge to enhance the database system of **Divvy**, a bike-sharing service in Chicago, IL, USA.  

The project utilized the Divvy dataset, which includes trip data from 2018 and station information, accessible via MySQL Workbench. My task was to interrogate the database using SQL, propose a re-modeled structure, and demonstrate its value in addressing business needs through actionable insights and strategic recommendations.  

<img src="/site/images/sql1.jpg" class="img-medium" />

## My Core Contributions

Delivered technical solutions and business-oriented insights to improve Divvy’s database system.

### 1. SQL Database Interrogation
1. Utilized **MySQL Workbench** to explore the Divvy database,
2. Executed SQL queries to answer predefined questions, gaining deep insights into trip patterns, user behavior, and station usage.

```sql
-- Step 3: Using the same UNION keyword, count the total number of different stations in the two columns of the Trips table
SELECT count(*) FROM
(
SELECT DISTINCT from_station_id
FROM Trips
WHERE from_station_id NOT IN (SELECT id FROM Stations)
UNION
SELECT DISTINCT to_station_id
FROM Trips
WHERE to_station_id NOT IN (SELECT id FROM Stations)
)
as result;

-- Step 4: Finally, write a query that displays the percentage of missing stations from the Stations table.
SELECT 
    (SELECT COUNT(id) FROM Stations) / 
    (
        (SELECT COUNT(id) FROM Stations) + 
        (SELECT COUNT(*) 
         FROM (
             SELECT DISTINCT from_station_id
             FROM Trips
             WHERE from_station_id NOT IN (SELECT id FROM Stations)
             UNION
             SELECT DISTINCT to_station_id
             FROM Trips
             WHERE to_station_id NOT IN (SELECT id FROM Stations)
         ) AS result)
    ) * 100 AS percentage_dif;

 ```

### 2. Database Re-Modeling
<img src="/site/images/sql2.jpg" class="img-medium" />
1. Developed a **conceptual diagram** (submitted as a clear PDF/image) illustrating high-level improvements to the database schema.
2. Designed a detailed **Entity-Relationship (ER) Model** using Hackolade, incorporating attributes, data types, primary/foreign keys, and cardinalities. Proposed a re-structured database to enhance query efficiency and data usability for Divvy Inc.
<img src="/site/images/sql3.png"/>
### 3. Business-Level Insights
Crafted **five business-level questions** (e.g., peak usage times, customer segmentation) that Divvy could address with the new database design. Wrote corresponding **SQL queries** to demonstrate the effectiveness of the re-modeled structure in answering strategic questions.
<img src="/site/images/sql-list.jpg" class="img-medium" />



<p style="font-size: 0.7em; color: gray; text-align: left;">
  <strong>Data Disclaimer</strong><br/>
  All data is sourced from the publicly available Divvy Trip Data dataset. This project is for educational purposes only and does not reflect actual business operations or real-world strategic decisions by Divvy Inc.
</p>
