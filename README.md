# SQL Portfolio: Data Analysis & Query Optimization

<div align="center">

[![SQL](https://img.shields.io/badge/SQL-Database_Analysis-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Advanced-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Intermediate-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Data_Analysis-Query_Driven-4CAF50?style=for-the-badge)](https://github.com/CarineJackson1)

</div>

---

## 🎯 Overview

A collection of **production-ready SQL queries and database analysis projects** demonstrating expertise in complex data retrieval, performance optimization, and business intelligence. These projects showcase real-world problem-solving across retail, entertainment, and customer analytics domains.

**Focus areas:** Complex joins • Data aggregation • Customer insights • Performance tuning • Business analytics

---

## 📂 Repository Structure

```
SQL-Portfolio/
├── README.md                          (this file)
├── requirements.txt                   (database setup)
├── Datasets/                          (raw data files)
├── queries/
│   ├── Customer & Order Analytics/    (retail analytics)
│   ├── Netflix Database/              (entertainment analytics)
│   └── Superstore Database/           (comprehensive retail analysis)
└── documentation/                     (explanations & insights)
```

---

## 🔍 Featured Projects

### 1️⃣ **Customer & Order Analytics**

**Overview:** Comprehensive analysis of customer behavior, order patterns, and purchase trends across a retail database.

**Key Queries:**
- Customer segmentation by purchase frequency and lifetime value
- Order trends and seasonal patterns
- Revenue analysis by customer, product, and time period
- Customer retention and churn analysis
- Top customers and product performance

**SQL Techniques Used:**
- Multi-table JOINs (customers, orders, order_items, products)
- Window functions (ROW_NUMBER, RANK, LAG/LEAD for trend analysis)
- Aggregations (SUM, COUNT, AVG) with GROUP BY
- Date/time functions for temporal analysis
- CTEs for readable, complex queries

**Business Insights Unlocked:**
- Identify high-value customers for targeted marketing
- Detect seasonal trends to optimize inventory
- Analyze repeat purchase rates and customer loyalty
- Find product performance patterns

**Sample Query: Top 10 Customers by Revenue**
```sql
SELECT 
    c.customer_id,
    c.customer_name,
    SUM(o.order_total) as total_revenue,
    COUNT(o.order_id) as total_orders,
    AVG(o.order_total) as avg_order_value,
    RANK() OVER (ORDER BY SUM(o.order_total) DESC) as revenue_rank
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.customer_name
ORDER BY total_revenue DESC
LIMIT 10;
```

[**View All Customer & Order Queries →**](queries/Customer%20&%20Order%20Analytics)

---

### 2️⃣ **Netflix Database Analysis**

**Overview:** Analysis of streaming entertainment data including shows, viewers, watch patterns, and performance metrics.

**Key Queries:**
- Content performance (views, ratings, popularity)
- User engagement and viewing patterns
- Genre analysis and trends
- Title performance across regions
- Watch time and completion rates

**SQL Techniques Used:**
- Complex JOINs across shows, viewers, ratings, and genres
- Window functions for rankings and trending
- String functions for data parsing
- Date calculations for time-based analysis
- Aggregation functions for engagement metrics

**Business Insights Unlocked:**
- Identify top-performing shows and genres
- Analyze viewer engagement patterns
- Detect regional preferences
- Forecast content performance

**Sample Query: Top Shows by Average Rating**
```sql
SELECT 
    s.show_title,
    s.genre,
    COUNT(DISTINCT r.viewer_id) as total_viewers,
    AVG(r.rating) as avg_rating,
    COUNT(r.rating) as total_ratings,
    RANK() OVER (PARTITION BY s.genre ORDER BY AVG(r.rating) DESC) as genre_rank
FROM shows s
LEFT JOIN ratings r ON s.show_id = r.show_id
GROUP BY s.show_id, s.show_title, s.genre
HAVING COUNT(r.rating) >= 10
ORDER BY avg_rating DESC;
```

[**View All Netflix Queries →**](queries/Netflix%20Database)

---

### 3️⃣ **Superstore Database**

**Overview:** In-depth analysis of superstore sales data including products, regions, customer segments, and profitability.

**Key Queries:**
- Sales performance by region, category, and segment
- Profitability analysis and margin trends
- Product performance and inventory insights
- Regional market analysis
- Discount impact on profitability

**SQL Techniques Used:**
- Advanced JOINs (INNER, LEFT, FULL OUTER)
- Window functions (SUM OVER, ROW_NUMBER, LAG/LEAD)
- CASE statements for conditional logic
- Subqueries for complex filtering
- CTEs for modular query design

**Business Insights Unlocked:**
- Optimize pricing and discounting strategies
- Identify high-profit regions and products
- Analyze customer segments and behavior
- Improve inventory management
- Maximize profitability

**Sample Query: Sales by Region and Category with Margin Analysis**
```sql
SELECT 
    s.region,
    s.category,
    SUM(s.sales) as total_sales,
    SUM(s.profit) as total_profit,
    ROUND(100.0 * SUM(s.profit) / SUM(s.sales), 2) as profit_margin_percent,
    COUNT(DISTINCT s.order_id) as number_of_orders,
    RANK() OVER (PARTITION BY s.region ORDER BY SUM(s.profit) DESC) as category_rank_in_region
FROM superstore_sales s
GROUP BY s.region, s.category
ORDER BY s.region, total_profit DESC;
```

[**View All Superstore Queries →**](queries/Superstore%20Database)

---

## 💡 SQL Techniques Demonstrated

| Technique | Where Used | Complexity |
|-----------|-----------|-----------|
| **INNER/LEFT/FULL OUTER JOINs** | All projects | ⭐⭐ |
| **Window Functions** (ROW_NUMBER, RANK, LAG/LEAD, SUM OVER) | All projects | ⭐⭐⭐ |
| **CTEs (Common Table Expressions)** | Customer Analytics, Superstore | ⭐⭐⭐ |
| **Aggregation Functions** (SUM, COUNT, AVG, MIN, MAX) | All projects | ⭐ |
| **GROUP BY & HAVING** | All projects | ⭐⭐ |
| **Date/Time Functions** | Customer Analytics, Netflix | ⭐⭐ |
| **CASE Statements** | Superstore | ⭐⭐ |
| **Subqueries & Correlated Queries** | All projects | ⭐⭐⭐ |
| **String Functions** | Netflix Database | ⭐⭐ |
| **Performance Optimization** | All projects | ⭐⭐⭐ |

---

## 🚀 Quick Start

### 1. **Set Up Your Database**
```bash
# Install requirements
pip install -r requirements.txt

# Create databases from datasets/
psql -U username -d database_name -f datasets/setup.sql
```

### 2. **Explore the Queries**
Navigate to `queries/` folder and select a project:
- Start with **Customer & Order Analytics** for fundamentals
- Progress to **Netflix Database** for moderate complexity
- Master **Superstore Database** for advanced techniques

### 3. **Run a Query**
```sql
-- PostgreSQL
psql -U username -d database_name -f queries/Customer\ &\ Order\ Analytics/top_customers.sql

-- MySQL
mysql -u username -p database_name < queries/Superstore\ Database/regional_analysis.sql
```

### 4. **Study & Adapt**
- Read the query comments for explanations
- Modify for your own datasets
- Check execution plans for optimization insights

---

## 📊 Key Skills Demonstrated

<div align="center">

### **Data Retrieval & Analysis**
![Complex JOINs](https://img.shields.io/badge/Complex_JOINs-Multi_Table-0078D4?style=for-the-badge)
![Aggregations](https://img.shields.io/badge/Aggregations-GROUP_BY-4CAF50?style=for-the-badge)
![Window Functions](https://img.shields.io/badge/Window_Functions-Advanced-FF9800?style=for-the-badge)

### **Performance & Optimization**
![Query Optimization](https://img.shields.io/badge/Query_Optimization-Performance_Tuning-FF6B6B?style=for-the-badge)
![Indexing](https://img.shields.io/badge/Indexing-Query_Acceleration-336791?style=for-the-badge)
![Execution Plans](https://img.shields.io/badge/Execution_Plans-Analysis-FF6B6B?style=for-the-badge)

### **Database Management**
![Schema Design](https://img.shields.io/badge/Schema_Design-Normalization-4479A1?style=for-the-badge)
![Data Integrity](https://img.shields.io/badge/Data_Integrity-Validation-4CAF50?style=for-the-badge)

</div>

---

## 🎯 Use Cases & Business Value

**For Job Interviews:**
- Demonstrate real SQL expertise across multiple domains
- Show ability to solve complex business problems
- Display performance optimization knowledge

**For Learning:**
- Study real-world database structures
- Learn patterns for common analytics questions
- Practice progressive complexity

**For Business:**
- Extract actionable insights from data
- Support decision-making with data
- Optimize operations and profitability

---

## 📈 Query Complexity Progression

**Beginner:**
- Simple SELECT with WHERE and ORDER BY
- Basic aggregations with GROUP BY
- INNER JOINs between 2-3 tables

**Intermediate:**
- Multiple JOINs with different types
- Window functions for rankings
- CTEs for query organization
- CASE statements for logic

**Advanced:**
- Nested window functions
- Complex subqueries
- Performance optimization
- Multi-step analytics

---

## 🔗 Database Schemas

### Customer & Order Analytics
```
customers → orders → order_items → products
          ↓
       order_status
```

### Netflix Database
```
shows → ratings ← viewers
   ↓
genres
```

### Superstore Database
```
superstore_sales (all-in-one table with dimensions)
```

---

## 💼 What's Included

✅ **5+ production-ready queries per project**  
✅ **Well-commented code** with explanations  
✅ **Sample data** for testing  
✅ **Execution plans** showing optimization strategies  
✅ **Documentation** of business logic  
✅ **Requirements file** for easy setup  

---

## 🌟 Highlights

- **Real datasets** from retail, entertainment, and e-commerce
- **Progressive complexity** from basic to advanced
- **Performance-focused** with optimization tips
- **Well-organized** structure for easy navigation
- **Business-oriented** queries that answer real questions

---

## 🤝 Let's Connect

Questions about a specific query? Want to discuss optimization strategies or SQL best practices?

<div align="center">

[![LinkedIn](https://img.shields.io/badge/💼_LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/carinejackson)
[![Email](https://img.shields.io/badge/📧_Email-Reach_Out-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:carinejackson48@gmail.com)
[![GitHub](https://img.shields.io/badge/🔗_GitHub-View_Repository-333333?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CarineJackson1)

</div>

---

<div align="center">

### 📊 **Building data-driven solutions with SQL**

*Complex queries. Optimized performance. Real insights.*

**Explore | Learn | Apply**

</div>
