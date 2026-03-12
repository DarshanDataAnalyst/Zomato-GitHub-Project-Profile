# 🍽 Zomato Order Analytics

> End-to-end analysis of **8,998 food delivery orders** across 5 Indian cities — uncovering revenue patterns, delivery bottlenecks, and customer experience drivers.


![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)

![Status](https://img.shields.io/badge/Status-Complete-22c55e?style=flat)

---

## 📊 At a Glance

| Metric | Value |
|--------|-------|
| Total Orders | 8,998 |
| Total Order Value | ₹61.94 Lakh |
| Cities Analyzed | 5 (Bangalore, Pune, Kolkata, Delhi, Mumbai) |
| Cuisines | 8 |
| Avg Order Value | ₹688 |
| Discount Impact | ₹7.09L (11.4% off revenue) |

---

## 🎯 Objective

Analyse order-level transactional data from Zomato to answer 10+ business questions covering **revenue**, **delivery efficiency**, **customer satisfaction**, **discounting strategy**, and **payment behaviour** — using Excel formulas and Python EDA.

---

## 📁 Dataset Schema — Details Sheet (7 Sub-Tables)

| Table | Key Columns | Description |
|-------|-------------|-------------|
| City–Area Map | City, Area Code | Maps each area code to one of 5 cities |
| Customer Master | Customer ID, Name, Area Code | Customer demographics linked to city |
| Cuisine / Dish | Cuisine Name, Code, Dish Code, Price | Menu items with base prices |
| Orders Fact | Order ID, Date, Slot, Customer ID | Core transactions — one row per order |
| Discount Matrix | Cuisine × City (5 cols) | Percentage discounts per cuisine per city |
| Delivery Info | Order ID, Delivery Time (min), Distance (km) | Logistics data for fee & speed derivation |
| Rating & Payment | Order ID, Rating (1–5), Payment Method | Post-order satisfaction and payment channel |

---

## 🔢 Derived Metrics — Formula Reference

```
Final Price       = Order Value × (1 − Discount% ÷ 100)
                    e.g. ₹500 × (1 − 16/100) = ₹420

Delivery Fee      = IF(distance ≤ 4km → ₹0 ; else → (distance − 4) × 10)
                    e.g. 6.6 km → (6.6 − 4) × 10 = ₹26

Customer Payable  = Final Price + Delivery Fee

Experience        = IF(Rating ≥ 4 → "Good" | Rating = 3 → "Average" | else → "Bad")

Delivery Speed    = IF(Time ≤ 30 → "Quick" | Time ≤ 45 → "On Time" | else → "Late")
```

> **Note:** Discount values in the matrix are percentages — `20` means **20% off**.

---

## ❓ 10 Business Questions — Answered

| # | Question | Answer |
|---|----------|--------|
| Q01 | What is the Delivery Fee per order? | Free ≤ 4km; ₹10/km beyond. **Avg = ₹22.69**. 26.3% of orders qualify for free delivery. |
| Q02 | What is the Customer Payable amount? | Final Price + Delivery Fee. Total payable after discounts = **₹54.86L** |
| Q03 | What is the Customer Experience? | Good **40.0%** (3,600) · Average **20.1%** (1,813) · Bad **39.8%** (3,585) |
| Q04 | What is the Delivery Speed? | Quick **1.8%** · On Time **17.4%** · Late **80.8%** ⚠️ |
| Q05 | Which city has the most orders? | **Bangalore (1,942)** → Pune (1,903) → Kolkata (1,867) |
| Q06 | Which cuisine is ordered most? | **Continental (1,498)** → Bengali (1,276) → Chinese (1,240) |
| Q07 | Which time slot is busiest? | **Breakfast (1,835)** — all 5 slots within 3.7% variance |
| Q08 | Which city has the highest revenue? | **Bangalore ₹13.37L** → Pune ₹13.02L → Kolkata ₹13.01L |
| Q09 | What is the top payment method? | **Debit Card (1,839)** — all 5 methods near-equal distribution |
| Q10 | What is the total discount impact? | **₹7.09L (11.4%)** reduced from ₹61.94L → ₹54.86L |

---

## 🚚 Delivery Performance

| Speed | Orders | Percentage | Criteria |
|-------|--------|------------|----------|
| 🔴 Late | 7,271 | **80.8%** | Delivery time > 45 minutes |
| 🟡 On Time | 1,565 | 17.4% | 30 < Delivery time ≤ 45 minutes |
| 🟢 Quick | 162 | 1.8% | Delivery time ≤ 30 minutes |

> ⚠️ **Critical Finding:** Over **80% of orders arrive late**. This directly correlates with 39.8% of customers giving a Bad rating — the single biggest operational problem in this dataset.

---

## 😊 Customer Experience Breakdown

| Experience | Orders | Percentage | Rating Criteria |
|------------|--------|------------|-----------------|
| 😊 Good | 3,600 | **40.0%** | Rating 4 or 5 |
| 😐 Average | 1,813 | **20.1%** | Rating 3 |
| 😞 Bad | 3,585 | **39.8%** | Rating 1 or 2 |

---

## 🏙️ Revenue by City

| City | Orders | Total Order Value | Avg Order Value | Market Share |
|------|--------|-------------------|-----------------|--------------|
| 🥇 Bangalore | 1,942 | ₹13,37,150 | ₹689 | 21.6% |
| Pune | 1,903 | ₹13,01,596 | ₹684 | 21.2% |
| Kolkata | 1,867 | ₹13,00,504 | ₹697 | 20.8% |
| Delhi | 1,678 | ₹11,51,601 | ₹686 | 18.6% |
| Mumbai | 1,608 | ₹11,03,547 | ₹686 | 17.9% |

> Average order value is consistent across all cities (₹684–₹697), confirming uniform platform pricing regardless of geography.

---

## 🎁 Discount Matrix (% by Cuisine × City)

| Cuisine | Orders | Bangalore | Mumbai | Delhi | Pune | Kolkata |
|---------|--------|-----------|--------|-------|------|---------|
| Continental | 1,498 | 10% | 10% | 8% | 14% | 13% |
| Bengali | 1,276 | 13% | 11% | 11% | 8% | 8% |
| Chinese | 1,240 | 10% | 8% | 11% | **20%** 🔴 | 10% |
| Italian | 1,140 | 12% | 10% | **16%** | 14% | 8% |
| Dessert | 999 | **17%** | 9% | 8% | 16% | 9% |
| Mexican | 994 | **15%** | 9% | 13% | 12% | 10% |
| South Indian | 967 | 14% | 11% | 9% | 10% | 8% |
| North Indian | 884 | **16%** | 14% | 11% | 9% | 13% |

> **Highest discount:** Chinese food in Pune at **20%** — the maximum in the entire matrix.

---

## ⏰ Slot Distribution

| Slot | Orders | Share |
|------|--------|-------|
| 🌅 Breakfast | 1,835 | 20.4% |
| 🍽️ Dinner | 1,816 | 20.2% |
| 🌆 Evening Snacks | 1,792 | 19.9% |
| 🌙 Late Night | 1,786 | 19.8% |
| ☀️ Lunch | 1,769 | 19.7% |

> Demand is nearly perfectly uniform — Zomato operates as a true 24/7 platform.

---

## 💳 Payment Methods

| Method | Orders |
|--------|--------|
| 💳 Debit Card | 1,839 |
| 💳 Credit Card | 1,811 |
| 📱 UPI | 1,807 |
| 🏦 Net Banking | 1,781 |
| 📋 EMI | 1,760 |

---

## 💡 Key Findings & Recommendations

- 🔴 **Delivery is the #1 critical issue.** 80.8% of orders arrive late (>45 min), driving 39.8% Bad ratings. Implement driver SLAs, dynamic routing, and penalty/incentive structures.

- 📍 **Bangalore is the priority market.** Highest orders (1,942) and revenue (₹13.37L). Focus on restaurant expansion, loyalty programs, and premium partnerships here first.

- 🍽️ **Continental dominates unexpectedly** (1,498 orders vs. only 884 for North Indian). Investigate whether this reflects supply-side availability or a genuine urban preference shift.

- 💰 **₹7.09L (11.4%) is discounted across all orders.** Chinese/Pune (20%) and Dessert/Bangalore (17%) are the highest-cost discount segments — evaluate volume uplift vs. margin erosion.

- 📊 **Truly 24/7 demand.** All 5 slots are within 3.7% of each other. Operational staffing, kitchen capacity, and delivery fleet must be consistent round-the-clock.

- 💳 **Strong digital payment diversity.** All 5 methods are nearly equally used. EMI availability (1,760 orders) signals appetite for higher-ticket bundled orders.

---

## 🛠️ Tech Stack

  `Microsoft Excel` · `VLOOKUP` · `Pivot Tables` · 

---

## 📂 Project Structure

```
zomato-order-analytics/
├── data/
│   └── Zomato_Dataset.xlsx          # Raw workbook (Details + Data sheets)
├── notebooks/
│   ├── 01_data_cleaning.ipynb       # Null handling, type casting, VLOOKUP recreation
│   ├── 02_derived_metrics.ipynb     # Final Price, Delivery Fee, Payable, Speed, Experience
│   └── 03_analysis_answers.ipynb    # All 10 business questions answered with charts
├── outputs/
│   ├── city_revenue_analysis.xlsx
│   ├── delivery_performance.xlsx
│   └── customer_experience_report.xlsx
└── README.md
```

---

⭐ *If this project helped you, consider starring the repository!*
