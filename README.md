# User Engagement Analysis (Yelp Dataset)

## Overview
This project analyzes **Yelp data** to understand how **user engagement** (reviews, tips, and check-ins) influences **restaurant success**. Using Python and SQLite, we explore correlations between engagement metrics, ratings, and review counts, while also identifying **temporal trends**, **city-level success patterns**, and **peak engagement hours**.

---

## Problem Statement
In a competitive restaurant industry, understanding the factors that drive success is crucial. This project investigates how **user engagement** impacts business performance, and provides actionable insights for improving visibility, customer interaction, and growth.

---

## Data
- **Source:** Yelp Academic Dataset  
- **Files:** `business.json`, `review.json`, `tip.json`, `checkin.json`, `user.json`  
- **Scope:** ~150,000 businesses across 8 US and Canadian cities, with ~35,000 **open restaurants** analyzed  
- **Storage:** Data loaded into **SQLite database** (`yelp.db`) for efficient querying  

---

## Tools & Libraries
- **Python:** pandas, numpy, matplotlib, seaborn, folium, geopy, statsmodels  
- **Database:** SQLite (via SQLAlchemy & sqlite3)  
- **Visualization:** Heatmaps, bar charts, pie charts, line plots, interactive maps  
- **Environment:** Jupyter Notebook  

---

## Methodology
1. **Data Ingestion:** Loaded Yelp JSON files into pandas DataFrames and stored in SQLite.  
2. **Data Cleaning:** Removed irrelevant columns (`attributes`, `hours`) and **outliers** using **IQR**.  
3. **Descriptive Analysis:** Examined review counts, star ratings, and engagement metrics.  
4. **Correlation Analysis:** Evaluated relationships among reviews, tips, and check-ins.  
5. **Time Series & Seasonal Analysis:** Tracked engagement trends over months and seasons using **seasonal decomposition**.  
6. **City-Level Success Analysis:** Calculated **success score** = `avg_rating * log(review_count + 1)` and visualized top cities on an interactive **Folium map**.  
7. **Peak Hour Analysis:** Determined busiest hours using review, tip, and check-in timestamps.  
8. **Elite User Analysis:** Compared contributions of elite vs non-elite users to total reviews.  

---

## Key Findings
- **No direct correlation** between ratings and review count. 
- Engagement increases from 1 → 4 stars, peaks at 4.0, then drops at 4.5–5.0 stars.  
- **Reviews, tips, and check-ins** are strongly correlated; boosting one can improve others.  
- **High-rated restaurants** maintain steady or increasing engagement over time; **tip counts** trend downward, while **review counts** trend upward.  
- **Peak hours:** 16:00–01:00, with seasonal peaks around Nov–Mar.  
- **Top city:** Philadelphia, followed by Tampa, Indianapolis, and Tucson.  
- **Elite users** contribute a disproportionate share of reviews despite smaller numbers.  

---

## Recommendations
- Engage with **elite users** to amplify reach and encourage loyalty.  
- Optimize staffing and promotions around **peak hours** and high-demand months.  
- Focus on strategies to increase all types of engagement (reviews, tips, check-ins).  
- Consider expansion or investment in cities with **high success scores**.  

---

## Skills & Techniques
- **Data Cleaning & Transformation:** pandas, IQR outlier removal  
- **Database Management:** SQLite, SQL queries via pandas  
- **Data Analysis:** Descriptive statistics, correlation, grouping, aggregation  
- **Time-Series & Seasonal Analysis:** statsmodels  
- **Visualization:** matplotlib, seaborn, folium  
- **Business Insights:** Peak hours, city-wise success, elite user impact

## Project Pipeline

```mermaid
flowchart LR
    A[Start] --> B[Yelp JSON Datasets]
    B --> C[Data Ingestion<br/>Load JSON to Pandas]
    C --> D[Database Integration<br/>Store in SQLite via SQLAlchemy]
    D --> E[Data Cleaning<br/>Drop nulls and irrelevant columns]
    
    subgraph Analysis["Exploratory & Statistical Analysis"]
        E --> F1[Ratings & Engagement Metrics]
        F1 --> F2[Correlation between Reviews, Tips, Check-ins]
        F2 --> F3[Time Trends & Seasonal Patterns]
        F3 --> F4[City-level Success Scoring]
        F4 --> F5[Peak Hour Analysis]
        F5 --> F6[Elite vs Non-Elite User Insights]
    end

    Analysis --> G[Visualization<br/>Matplotlib, Seaborn, Folium]
    G --> H[Insights & Recommendations]
    H --> I[End]



