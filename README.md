# Customer Behavior Analysis Using Sql,Power Bi,Python

![Customer Behavior Dashboard](powerbi-dashboard.png) <img width="1359" height="734" alt="Screenshot 2026-01-19 164113" src="https://github.com/user-attachments/assets/cdda23b9-aa8e-412b-ba19-9fd3e5bb915c" />


## Table of Contents
- [Project Overview](#-project-overview)
- [Dataset Summary](#-dataset-summary)
- [Technologies & Workflow](#️-technologies--workflow)
- [Data Preparation (Python)](#-data-preparation-python)
- [Key SQL Analysis Highlights](#-key-sql-analysis-highlights)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Business Recommendations](#-business-recommendations)
- [Project Files](#-project-files)
- [How to Run](#-how-to-run)
- [License](#-license)

**Project Type:** Data Analysis | Exploratory Data Analysis (EDA) | SQL | Power BI  | Python
**Dataset Size:** 3,900 rows × 18 columns  
**Tools Used:** Python (pandas), MYSQL, Power BI  

## 📋 Project Overview
This project analyzes customer shopping behavior using transactional data from **3,900 purchases** across various product categories.  

**Goal:** Uncover insights into spending patterns, customer segments, product preferences, and subscription behavior to guide strategic business decisions.

## 📊 Dataset Summary
- **Rows:** 3,900  
- **Columns:** 18  
- **Key Features:**  
  - Customer demographics: Age, Gender, Location, Subscription Status  
  - Purchase details: Item Purchased, Category, Purchase Amount (USD), Season, Size, Color  
  - Shopping behavior: Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type  
- **Missing Data:** 37 values in Review Rating column  

## 🛠️ Technologies & Workflow
- **Python** → Data cleaning, feature engineering, EDA  
- **MySQL** → Business queries & analysis  
- **Power BI** → Interactive dashboard  
- **Database** → Cleaned data loaded into MySQL  

## 🔧 Data Preparation (Python)
```python
# Key steps performed
import pandas as pd

df = pd.read_csv('shopping_trends.csv')
df.info()
df.describe()

# Missing value handling
df['Review Rating'] = df.groupby('Category')['Review Rating'].transform(lambda x: x.fillna(x.median()))

# Feature Engineering
df['age_group'] = pd.cut(df['Age'], bins=[0,25,40,55,100], labels=['Young Adult','Middle-aged','Adult','Senior'])
df['purchase_frequency_days'] = ... # custom logic

# Dropped redundant column
df = df.drop(columns=['Promo Code Used'])

📈 Key SQL Analysis Highlights

Revenue by Gender
Male: $157,890 | Female: $75,191Revenue by Gender Table
High-Spending Discount Users → 839 customers spent above average despite discountHigh-Spending Discount Users Table
Top 5 Products by Rating
Gloves (3.86), Sandals (3.84), Boots (3.82), Hat (3.80), Skirt (3.78)Top Products by Rating Table
Shipping Type → Express: $60.48 avg | Standard: $58.46 avgShipping Type Table
Subscribers vs Non-Subscribers
Subscribers (27%): Avg spend $59.49 | Non: $59.87Subscribers vs Non-Subscribers Table
Discount-Dependent Products
Hat (50%), Sneakers (49.66%), Coat (49.07%)...Discount-Dependent Products Table
Customer Segmentation
Loyal: 3,116 | Returning: 701 | New: 83Customer Segmentation Table
Top 3 Products per Category
Accessories: Jewelry, Sunglasses, Belt
Clothing: Blouse, Pants, Shirt
Footwear: Sandals, Shoes, Sneakers
Outerwear: Jacket, Coat
Top Products per Category Table
Repeat Buyers & Subscription → 958 repeat buyers are subscribersRepeat Buyers Table
Revenue by Age Group
Young Adult: $62,143 | Middle-aged: $59,197 | Adult: $55,978 | Senior: $55,763Revenue by Age Group Table

📊 Power BI Dashboard
Interactive dashboard created with:

Key KPIs (Total Customers, Avg Purchase, Avg Rating)
Revenue by Category, Age Group, Subscription
Pie charts, bar charts, slicers

Power BI Dashboard Screenshot
💡 Business Recommendations

Boost Subscriptions → Promote exclusive benefits
Customer Loyalty Programs → Reward repeat buyers to move them to "Loyal" segment
Review Discount Policy → Balance sales boost with margin control
Product Positioning → Highlight top-rated & best-selling items
Targeted Marketing → Focus on high-revenue age groups & Express shipping users

📁 Project Files
text├──customer behaviour analysis.csv              (Original dataset)
├── customer_shopping_analysis.ipynb (Python notebook)
├── sql_queries.sql                  (All 10 business queries)
├── cleaned_customer_data.sql        (MySQL table)
├── Customer_Behavior_Dashboard.pbix (Power BI file)
├── README.md
└── images/                          (Dashboard and table screenshots)
🚀 How to Run

Install: pip install pandas sqlalchemy
Run Python notebook
Import SQL file into MySQL
Open Power BI file

📄 License
MIT License
Made with ❤️ using Python, SQL & Power BI
