# Marketing-Analytics-and-Sentiment-Analysis

### **SQL Server | Python (NLTK Sentiment Analysis) | Power BI | Data Modeling | Dashboarding**
**Extract → Transform → Load → Analyze → Visualize workflow**

# <h2 id="overview">📌 **Overview**</h2>

This project uncovers performance issues across **customer engagement**, **conversion patterns**, **product satisfaction**, and **marketing effectiveness** for ShopEasy.  
It leverages:

- **SQL Server** for data cleaning & transformation  
- **Python (NLTK)** for sentiment analysis  
- **Power BI** for dashboard creation  

The outcome is a complete, actionable analytics solution to improve performance and marketing ROI.

---

# <h2 id="executive-summary">**Executive Summary**</h2>

Marketing Analytics Project: This project analyzes customer behavior, campaign performance, and marketing channel effectiveness to uncover the factors influencing customer engagement and conversion rates. By leveraging marketing and customer data, the analysis identifies key trends, measures campaign ROI, segments customers, and provides actionable insights to optimize marketing strategies, improve conversion rates, increase customer engagement, and maximize overall business performance.

---

# <h2 id="business-problem">**Business Problem**</h2>

MarketPulse is facing several key marketing challenges that require a data-driven approach to optimize campaign performance, understand customer behavior, improve engagement, increase conversion rates, and maximize marketing ROI. 
• **Reduced Customer Engagement:** The number of customer interactions with the website and marketing content has declined.  
• **Decreased Conversion Rates:** Fewer site visitors are successfully converting into paying customers.  
• **High Marketing Expenses:** Significant investments in marketing campaigns are not yielding the expected Return on Investment (ROI).  
• **Need for Customer Feedback Analysis:** Understanding customer opinions about products and services is crucial for improving engagement and conversions.

---

# <h2 id="goals">🎯 **Goals**</h2>

1. **Increase Conversion Rates:** Identify factors impacting the conversion rate and provide recommendations for improvement.  
2. **Enhance Customer Engagement:** Determine which types of content drive the highest engagement.  
3. **Improve Customer Feedback Scores:** Understand common themes and sentiment in customer reviews and provide actionable insights.

---

# <h2 id="tools-technologies">🛠 **Tools & Technologies**</h2>

| **Tool** | **Purpose** |
|---------|-------------|
| **Microsoft SQL Server** | Data extraction, cleaning, transformation, analysis |
| **Python (Pandas, NLTK, SQLAlchemy)** | Sentiment analysis, SQL querying, data enrichment |
| **Power BI** | Data modeling, dashboard creation, visual insights |
| **SQLAlchemy** | Python ↔ SQL Server integration |
| **NLTK VADER** | Sentiment classification (Positive, Mixed, Negative) |

---

# <h2 id="project-flow">**ETL Pipeline WorkFlow**</h2>

**Extract → Transform → Load → Analyze**

**1. Extract**  
MSSQL → Raw Tables (Products, Customers, Reviews, Engagement, Journey)

&nbsp;⬇️

**2. Transform**  
MSSQL → Data Cleaning, Standardization, Deduplication  
Python → Sentiment Analysis (VADER), Feature Engineering → CSV Export

&nbsp;⬇️

**3. Load**  
Power BI → Import Clean SQL Data + Sentiment CSV → Build Star Schema Model

&nbsp;⬇️

**4. Analyze & Visualize**  
Power BI → DAX → Interactive Dashboards → KPIs → Insights

&nbsp;⬇️

**5. Recommend**  
Strategy Recommendations → Conversion Optimization → Engagement Improvements

This workflow represents a complete **ETL + BI Analytics Pipeline**, transforming raw operational data into actionable business insights.

# <h2 id="sql">🗄️ **MSSQL: Data Preparation & Analysis**</h2>

### ✔ **Database Creation**
- Restored `MarketingAnalytics.bak` into SQL Server  
- Database name: **PortfolioProject_MarketingAnalytics**

### ✔ **Data Cleaning & Transformations**
- **Products:** Added price categories using `CASE`  
- **Customers:** Joined with Geography table  
- **Customer Reviews:** Cleaned text formatting  
- **Engagement Data:** Split Views–Clicks field, standardized content types  
- **Customer Journey:** Removed duplicates with `ROW_NUMBER()` and filled null durations  

### ✔ **SQL Features Demonstrated**
- Window functions  
- CTEs  
- Joins  
- Aggregations  
- Conditional logic  
- Date formatting  

📄 All SQL scripts stored in: **queries.sql**

---

# <h2 id="python"> **Python: Sentiment Analysis**</h2>

### ✔ **Purpose**
To understand customer sentiment more deeply than numeric ratings allow—helping identify hidden pain points and satisfaction drivers.

### ✔ **What the Script Does**
- Connects to SQL Server using SQLAlchemy  
- Loads raw customer reviews  
- Applies **VADER sentiment scoring**  
- Creates three new sentiment fields:  
  - **SentimentScore** (numeric score)  
  - **SentimentCategory** (Positive, Negative, Mixed Positive, Mixed Negative, Neutral)  
  - **SentimentBucket** (score range groups)  
- Exports enriched data to CSV

### ✔ **Output File**
📄 `fact_customer_reviews_with_sentiment.csv`

---

# <h2 id="powerbi">📊 **Power BI: Data Modeling & Dashboarding**</h2>

### ✔ **Data Connections**
- Direct SQL Server import  
- Sentiment CSV from Python  

### ✔ **Data Model (Star Schema)**

<img width="1144" height="691" alt="image" src="https://github.com/user-attachments/assets/6fd51ee3-f6a4-4f07-a1ae-197624456713" />

**Dimensions:**
- `dim_products`  
- `dim_customers`  
- `Calendar`  

**Fact Tables:**
- `fact_customer_reviews`  
- `fact_customer_reviews_sentiment`  
- `fact_engagement_data`  
- `fact_customer_journey`  

### ✔ **Calendar Table**
Created to enable time intelligence (Month, Quarter, Year, etc.)

### ✔ **DAX Measures**
```DAX
Views = SUM(fact_engagement_data[Views])
Clicks = SUM(fact_engagement_data[Clicks])
Likes = SUM(fact_engagement_data[Likes])
Rating (Average) = AVERAGE(fact_customer_reviews[Rating])
Number of Journeys = COUNT(fact_customer_journey[JourneyID])
Conversion Rate = DIVIDE([Clicks], [Views], 0)
```

✔ Dashboard Pages

Overview Dashboard
<img width="940" height="520" alt="image" src="https://github.com/user-attachments/assets/91e781de-df4e-4dac-bea5-0e10a402d325" />


Conversion Performance
<img width="940" height="526" alt="image" src="https://github.com/user-attachments/assets/9457e121-b1b6-46ee-a3cb-b5d4edb9c3f1" />


Social Media Engagement
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/44bcad8a-9a6a-44a0-9ed3-ecb9b77f4ceb" />


Customer Reviews & Sentiment
<img width="1450" height="819" alt="image" src="https://github.com/user-attachments/assets/dd7686f2-bd0a-4f00-888c-7d6d647f3204" />

---
## <h2 id="key-insights">🔍 <strong>Key Insights</strong></h2>

### 🟦 **Conversion Trends**
- **Average conversion rate:** 9.57%  
- **Lowest conversion month:** October (6.15%)  
- **Highest conversion month:** January (17.31%)  
- Clear **seasonal performance patterns** observed throughout the year  

---

### 🟧 **Engagement Trends**
- **Views consistently declined** after April  
- **Likes remained extremely low**, indicating weak interaction quality  
- **Blogs** were the **best-performing content type**, generating the highest engagement  
- Social media performance weakened mid-year, impacting reach and clicks  

---

### 🟩 **Customer Feedback Insights**
- **Average customer rating:** 3.69 (below the target of 4.0)  
- **Sentiment Analysis Breakdown:**  
  - ⭐ **Positive:** 840 reviews  
  - ⚠️ **Mixed Negative:** 196 reviews  
  - 👍 **Mixed Positive:** 86 reviews  
  - ❌ **Negative:** 226 reviews  
  - ⚪ **Neutral:** 15 reviews  

- Large volume of **mixed reviews** suggests improvement opportunities in product experience  
- Negative sentiment, though smaller, highlights **key pain points** affecting customer satisfaction  

---


## <h2 id="recommendations">📌 <strong>Recommended Actions</strong></h2>

### ✔ **Boost Conversion**
- Focus on **high-performing product categories** (Ski Boots, Hockey Stick, Baseball Glove)  
- Launch **seasonal promotions** during peak purchase periods (**Jan–Feb, Dec**)  
- Strengthen **mid-year performance** (Mar–Jun) with targeted marketing campaigns and product offers  

---

### ✔ **Improve Engagement**
- Refresh content strategy:  
  - Use **interactive posts**, **short-form videos**, **reels**, and stronger **CTAs**  
- Increase posting frequency and engagement-driven content during low-activity months (**Jul–Oct**)  
- Optimize messaging to regain reach and attention across social platforms  

---

### ✔ **Raise Customer Satisfaction**
- Analyze **Mixed Negative** review patterns to identify recurring product/service issues  
- Implement a **customer follow-up workflow** for dissatisfied users  
- Encourage customers to **re-rate their experience** after issue resolution  
- Use sentiment signals to prioritize product improvements and service enhancements  

---


<h2 id="project-structure">📁 Project Structure</h2>
ShopEasy-Marketing-Analytics/
│

├── data/

│   ├── fact_customer_reviews_with_sentiment.csv

│   └── MarketingAnalytics.bak

│

├── sql/

│   └── queries.sql

│

├── python/

│   └── sentiment_analysis.py

│

├── powerbi/

│   └── Marketing_Analytics_Dashboard.pbix

│

└── README.md

---


## <h2 id="run">▶️ <strong>How to Run This Project</strong></h2>

### **1️⃣ Restore the SQL Database**
1. Open **SQL Server Management Studio (SSMS)**  
2. Restore the database using the backup file: `MarketingAnalytics.bak`  
3. Execute all SQL data-cleaning and transformation scripts from:  
   **`queries.sql`**

---

### **2️⃣ Run the Python Sentiment Analysis Script**
Install required dependencies:

```bash
pip install pandas sqlalchemy nltk pyodbc
python sentiment_analysis.py
```
This generates the enriched file:

fact_customer_reviews_with_sentiment.csv

### **3️⃣ Open the Power BI Dashboard**

1. Open **Power BI Desktop**  
2. Connect to your **SQL Server instance**  
3. Import the **sentiment CSV** file generated from Python  
4. Open the dashboard file:  
   **`Marketing_Analytics_Dashboard.pbix`**  
5. Click **Refresh** to load the latest SQL data and sentiment-enhanced review dataset  

---

