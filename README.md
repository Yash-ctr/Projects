# iTunes Music Store Database Analysis

## 📋 Project Overview

This project demonstrates a comprehensive database analysis of an iTunes Music Store dataset using MySQL. The project encompasses data loading, preprocessing, cleaning, and advanced querying to extract meaningful business insights from music sales data.

## 🎯 Objectives

- Build a relational database structure for iTunes music store data
- Implement data preprocessing and cleaning techniques
- Perform comprehensive business analytics through SQL queries
- Extract actionable insights for business decision-making

## 📊 Database Structure

The database consists of 10 interconnected tables:

### Core Tables
- **Artist** - Artist information and IDs
- **Album** - Album details with artist relationships
- **Genre** - Music genre classifications
- **Media_type** - Audio/video format types
- **Playlist** - User-created playlists
- **Playlist_track** - Track-to-playlist mappings

### Business Tables
- **Employee** - Staff information with hierarchical relationships
- **Customer** - Customer demographics and contact details
- **Invoice** - Purchase transactions
- **Invoice_line** - Individual items within purchases

## 🛠️ Technical Implementation

### Data Loading Process
```sql
-- Example table creation and data loading
CREATE TABLE Artist (
    artist_id INT PRIMARY KEY,
    name VARCHAR(100)
);

LOAD DATA INFILE 'path/to/artist.csv'
INTO TABLE Artist
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 1 ROWS;
```

### Data Preprocessing Steps

#### 1. **Data Type Validation**
- Verified column data types across all tables
- Ensured proper foreign key relationships
- Validated date formats and numeric fields

#### 2. **Missing Value Analysis**
Systematically checked for NULL values in critical fields:
- Customer contact information
- Employee hierarchical data
- Invoice totals and dates
- Track and playlist relationships

#### 3. **Data Cleaning Implementation**
```sql
-- Handle missing values in Customer table
UPDATE customer SET Company = 'Unknown' WHERE Company IS NULL;
UPDATE customer SET State = 'Unknown' WHERE State IS NULL;
UPDATE customer SET postal_code = 'N/A' WHERE postal_code IS NULL;

-- Remove incomplete employee records
DELETE FROM employee WHERE reports_to IS NULL;
```

#### 4. **Duplicate Detection & Removal**
- Identified duplicate records using GROUP BY and HAVING clauses
- Removed duplicates while preserving data integrity
- Maintained referential integrity across foreign key relationships

## 📈 Business Analytics Performed

### 1. Customer Analytics
- **Top Spending Customers**: Identified highest value customers
- **Customer Lifetime Value**: Calculated average customer worth
- **Customer Segmentation**: Classified repeat vs one-time buyers
- **Geographic Revenue Analysis**: Revenue per customer by country
- **Customer Retention**: Identified inactive customers

### 2. Sales & Revenue Analysis
- **Monthly Revenue Trends**: Time-series revenue analysis
- **Sales Performance**: Revenue by sales representatives
- **Peak Sales Identification**: Highest performing months/quarters
- **Average Invoice Value**: Transaction size analysis

### 3. Product & Content Analysis
- **Top Revenue Tracks**: Best-performing individual tracks
- **Playlist Popularity**: Most purchased playlist content
- **Inventory Optimization**: Identified unpurchased tracks
- **Price-Sales Correlation**: Unit price vs sales volume analysis

### 4. Employee & Operational Efficiency
- **Workload Distribution**: Average customers per employee
- **Regional Performance**: Revenue by employee regions
- **Sales Rep Effectiveness**: Individual performance metrics

### 5. Geographic Market Analysis
- **Market Penetration**: Customer distribution by country
- **Regional Revenue**: Geographic revenue analysis
- **Market Opportunities**: Underperforming regions identification

### 6. Advanced Customer Insights
- **Purchase Patterns**: Frequency analysis per customer
- **Customer Behavior**: Time between purchases
- **Product Affinity**: Track combination analysis

## 🔍 Key Findings & Business Insights

### Revenue Insights
- Identified top-performing sales representatives and their contribution to total revenue
- Discovered seasonal trends in music purchases
- Analyzed price sensitivity across different track categories

### Customer Behavior
- Segmented customers into repeat buyers vs one-time purchasers
- Identified geographic markets with highest customer lifetime value
- Discovered customer retention patterns and churn indicators

### Product Performance
- Found tracks and playlists driving the most revenue
- Identified inventory that's not generating sales
- Analyzed optimal pricing strategies based on sales data

## 💻 Technical Skills Demonstrated

### SQL Expertise
- **DDL (Data Definition Language)**: Table creation, constraints, relationships
- **DML (Data Manipulation Language)**: Data insertion, updates, deletions
- **Advanced Querying**: JOINs, subqueries, window functions, CTEs
- **Aggregation Functions**: SUM, COUNT, AVG, GROUP BY, HAVING
- **Date Functions**: DATE_FORMAT, STR_TO_DATE, DATEDIFF
- **Data Cleaning**: NULLIF, conditional updates, duplicate removal

### Database Management
- Foreign key constraint management
- Data integrity maintenance
- Performance optimization techniques
- Transaction safety with SQL_SAFE_UPDATES

### Analytics Techniques
- Customer segmentation analysis
- Time-series trend analysis
- Geographic market analysis
- Product performance evaluation
- Employee productivity metrics

## 📁 Project Structure

```
iTunes-Music-Store-Analysis/
│
├── Apple iTunes Music Store SQL.sql    # Main SQL script
├── README.md                          # Project documentation
└── data/                             # CSV data files
    ├── artist.csv
    ├── album.csv
    ├── customer.csv
    ├── employee.csv
    ├── invoice.csv
    ├── invoice_line.csv
    ├── genre.csv
    ├── media_type.csv
    ├── playlist.csv
    └── playlist_track.csv
```

## 🚀 How to Run

1. **Setup MySQL Environment**
   ```bash
   # Ensure MySQL Server is running
   # Create a new database
   CREATE DATABASE itunes_store;
   USE itunes_store;
   ```

2. **Prepare Data Files**
   - Place CSV files in MySQL upload directory
   - Update file paths in the SQL script to match your system

3. **Execute SQL Script**
   ```bash
   # Run the complete analysis
   mysql -u username -p itunes_store < "Apple iTunes Music Store SQL.sql"
   ```

## 🎓 Learning Outcomes

This project demonstrates proficiency in:
- **Database Design**: Creating normalized relational database structures
- **Data Engineering**: ETL processes, data cleaning, and preprocessing
- **SQL Mastery**: Complex querying, joins, and analytical functions
- **Business Intelligence**: Translating data into actionable business insights
- **Problem Solving**: Handling real-world data quality issues

## 🔧 Tools & Technologies

- **Database**: MySQL 8.0
- **Languages**: SQL
- **Concepts**: Relational Database Design, Data Analytics, Business Intelligence

## 📊 Results Impact

The analysis provides actionable insights for:
- **Marketing Teams**: Customer segmentation and targeting strategies
- **Sales Management**: Performance evaluation and territory optimization
- **Product Managers**: Inventory optimization and pricing strategies
- **Executive Leadership**: Strategic decision-making based on data-driven insights

---
