# 📊 E-commerce Pricing & Discount Strategy Analysis

## Overview
This project analyzes pricing behavior, discount strategies, and revenue drivers for an e-commerce platform focused on tech products (Apple ecosystem and related accessories).

The analysis combines multiple datasets (orders, orderlines, products, brands) to evaluate:
- How discounts influence revenue and demand
- Whether pricing logic is consistent across products
- Which product categories drive performance
- Seasonal effects (e.g. Black Friday, Christmas)

---

## Data Sources
The analysis is based on four datasets:
- Orders – transaction-level information  
- Orderlines – product-level purchases  
- Products – catalog with base prices and product types  
- Brands – product brand mapping  

Raw data is loaded via external links (Google Drive) directly in the notebook.

---

## Project Structure
- ecommerce-pricing-analysis.ipynb → main notebook (data cleaning + analysis)  
- requirements.txt → dependencies  
- README.md → project documentation  

---

## Data Preparation

### Cleaning & Validation
- Removed duplicates and malformed price entries  
- Standardized price formats (string → float)  
- Filtered invalid and extreme values using IQR  
- Ensured consistency across merged datasets  

### Merging
- Orders and orderlines joined on order_id  
- Product data merged using sku  

---

## Feature Engineering

### Discount Calculation
Discounts are derived by comparing the transaction price with the maximum observed price per SKU:

discount = 100 - (unit_price / max_price * 100)

### Discount Buckets
- 0% → No discount  
- 1–33% → Low discount  
- 34–50% → Medium discount  
- 50%+ → High discount  

### Revenue
t_price = unit_price × quantity  

### Product Categories
Products are grouped using the top ~35 type values (covering ~80% of the catalog), into:

- Device (iPhone, MacBook, Apple Watch)  
- Storage (SSD, HDD, external drives)  
- Audio (headphones, speakers)  
- Protection (cases, screen protectors)  
- Accessories (cables, adapters, peripherals)  
- Components (RAM, batteries)  
- Infrastructure (servers, NAS)  
- Smart Home / IoT  
- Service (warranty)  
- Other (long tail)  

---

## Analysis

### 1. Discount Analysis
- Distribution of discounts across products  
- Monthly evolution of discount buckets  
- Discounted vs non-discounted revenue comparison  

Key finding:
- Most sales occur in the low discount range (1–33%)  
- High discounts are rare and contribute little revenue  

---

### 2. Revenue & Performance

#### By Category
- Accessories generate the highest total revenue  
- Storage is a strong secondary contributor  
- Devices are not the dominant revenue driver  

#### Top Products (SKU-level)
- Top 15 SKUs identified by revenue  
- Analysis includes units sold, average discount, and average selling price  

---

### 3. Time-Based Analysis

#### Monthly Trends
- Revenue and orders aggregated per month  
- Clear seasonal variation observed  

#### Key Events
- Strong spikes during Black Friday and Christmas  
- Increased discount activity during peak demand periods  

---

### 4. Discount vs Revenue
- Discounted products generate significantly higher total revenue  
- This is driven by volume rather than extreme discounting  

---

### 5. Price & Category Insights
- High-price products (devices) tend to have lower discounts  
- Lower-price categories (accessories) drive volume and revenue  

---

## Key Insights

### Pricing Strategy
- No evidence of systematic over-discounting  
- Pricing structure appears consistent across categories  
- Base product prices are sufficient (no need for approximation)  

### Business Takeaways
- Revenue is driven primarily by accessories and storage  
- Discounts are used strategically rather than aggressively  
- Seasonal campaigns significantly impact performance  

---

## Tech Stack
- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Jupyter Notebook  

---

## How to Run
1. Install dependencies:  
   pip install -r requirements.txt  

2. Open the notebook:  
   ecommerce-pricing-analysis.ipynb  

3. Run all cells to reproduce results  

---

## Notes
- Raw data is not included due to size constraints  
- Data is loaded via external links in the notebook  
- Analysis is fully reproducible  

---

## Author
Dana Reva
Email: dreva96@gmail.com
LinkedIn: https://www.linkedin.com/in/dana-reva
Location: Cologne, Germany
