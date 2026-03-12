# 🍽 Zomato Order Analytics

> End-to-end analysis of **8,998 food delivery orders** across 5 Indian cities — uncovering revenue patterns, delivery bottlenecks, and customer experience drivers.

![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)

![Status](https://img.shields.io/badge/Status-Complete-22c55e?style=flat)

---

## 📊 At a Glance

| Metric | Value |
|---|---|
| Total Orders | 8,998 |
| Total Order Value | ₹61.94 Lakh |
| Cities Analyzed | 5 (Bangalore, Pune, Kolkata, Delhi, Mumbai) |
| Cuisines | 8 |
| Avg Order Value | ₹688 |
| Discount Impact | ₹7.09L (11.4% off revenue) |

---

## 🎯 Objective

Analyse order-level transactional data from Zomato to answer 10+ business questions covering revenue, delivery efficiency, customer satisfaction, discounting strategy, and payment behaviour.

---

## 📁 Dataset Schema — Details Sheet (7 Tables)

| Table | Key Columns | Description |
|---|---|---|
| City–Area Map | City, Area Code | Maps each area code to one of 5 cities |
| Customer Master | Customer ID, Name, Area Code | Customer demographics linked to area/city |
| Cuisine / Dish | Cuisine Name, Code, Dish Code, Price | Menu with base prices |
| Orders Fact | Order ID, Date, Slot, Customer ID | Core transactions — one row per order |
| Discount Matrix | Cuisine × City (5 cols) | % discounts per cuisine per city |
| Delivery Info | Order ID, Delivery Time, Distance | Logistics data |
| Rating & Payment | Order ID, Rating (1–5), Payment Method | Post-order satisfaction |

---

## 🔢 Derived Metrics

```
Final Price       = Order Value × (1 − Discount% ÷ 100)
Delivery Fee      = IF(distance ≤ 4km, ₹0, (distance − 4) × 10)
Customer Payable  = Final Price + Delivery Fee
Experience        = IF(Rating ≥ 4, "Good", IF(Rating = 3, "Average", "Bad"))
Delivery Speed    = IF(Time ≤ 30, "Quick", IF(Time ≤ 45, "On Time", "Late"))
```

---

## ❓ 10 Business Questions — Answered

| # | Question | Answer |
|---|---|---|
| Q01 | Delivery Fee per order? | Free ≤4km; ₹10/km beyond. Avg = ₹22.69. 26.3% free. |
| Q02 | Customer Payable amount? | Final Price + Delivery Fee. Total after discounts = ₹54.9L |
| Q03 | Customer Experience? | Good 40.0% · Average 20.1% · Bad 39.8% |
| Q04 | Delivery Speed? | Quick 1.8% · On Time 17.4% · **Late 80.8%** ⚠ |
| Q05 | Top city by orders? | **Bangalore (1,942)** → Pune (1,903) → Kolkata (1,867) |
| Q06 | Most ordered cuisine? | **Continental (1,498)** → Bengali (1,276) → Chinese (1,240) |
| Q07 | Busiest time slot? | **Breakfast (1,835)** — all slots within 3.7% variance |
| Q08 | Highest revenue city? | **Bangalore ₹13.37L** → Pune ₹13.02L → Kolkata ₹13.01L |
| Q09 | Top payment method? | **Debit Card (1,839)** — all 5 methods near-equal |
| Q10 | Total discount impact? | ₹7.09L (11.4%) reduced from ₹61.94L → ₹54.86L |

---

## 🚚 Delivery Performance

| Speed | Orders | % | Criteria |
|---|---|---|---|
| 🔴 Late | 7,271 | **80.8%** | > 45 minutes |
| 🟡 On Time | 1,565 | 17.4% | 30–45 minutes |
| 🟢 Quick | 162 | 1.8% | ≤ 30 minutes |

> ⚠ **Critical Finding:** Over 80% of orders arrive late. This directly correlates with 39.8% Bad customer experience.

---

## 😊 Customer Experience

| Experience | Orders | % | Rating |
|---|---|---|---|
| 😊 Good | 3,600 | 40.0% | 4–5 ★ |
| 😐 Average | 1,813 | 20.1% | 3 ★ |
| 😞 Bad | 3,585 | 39.8% | 1–2 ★ |

---

## 🏙 Revenue by City

| City | Orders | Total Order Value | Avg Order |
|---|---|---|---|
| 🥇 Bangalore | 1,942 | ₹13,37,150 | ₹689 |
| Pune | 1,903 | ₹13,01,596 | ₹684 |
| Kolkata | 1,867 | ₹13,00,504 | ₹697 |
| Delhi | 1,678 | ₹11,51,601 | ₹686 |
| Mumbai | 1,608 | ₹11,03,547 | ₹686 |

---

## 🎁 Discount Matrix (% by Cuisine × City)

| Cuisine | Orders | Bangalore | Mumbai | Delhi | Pune | Kolkata |
|---|---|---|---|---|---|---|
| Continental | 1,498 | 10% | 10% | 8% | 14% | 13% |
| Bengali | 1,276 | 13% | 11% | 11% | 8% | 8% |
| Chinese | 1,240 | 10% | 8% | 11% | **20%** | 10% |
| Italian | 1,140 | 12% | 10% | 16% | 14% | 8% |
| Dessert | 999 | **17%** | 9% | 8% | 16% | 9% |
| Mexican | 994 | 15% | 9% | 13% | 12% | 10% |
| South Indian | 967 | 14% | 11% | 9% | 10% | 8% |
| North Indian | 884 | **16%** | 14% | 11% | 9% | 13% |

---

## 💡 Key Findings & Recommendations

- 🔴 **Delivery is the #1 issue.** 80.8% late deliveries drive 39.8% Bad ratings. Implement driver SLAs and real-time routing immediately.
- 📍 **Bangalore is the priority market.** Highest orders & revenue. Invest in restaurant partnerships and loyalty programs here first.
- 🍽 **Continental dominates unexpectedly** (1,498 orders vs. 884 North Indian). Investigate demographic drivers and expand restaurant supply.
- 💰 **₹7.09L in discounts given.** Chinese/Pune (20%) and Dessert/Bangalore (17%) are highest-cost segments — evaluate ROI.
- 📊 **Truly 24/7 platform.** Slot variance < 4%. Uniform staffing and capacity planning needed across all time slots.
- 💳 **Digital-first customers.** All 5 payment methods used equally — EMI availability signals appetite for premium order bundles.

---

## 🛠 Tech Stack

![Microsoft Excel](https://img.shields.io/badge/Microsoft Excel-217346?style=flat&logo=microsoft-excel&logoColor=white) 
`VLOOKUP` 
`Pivot Tables`

---

## 📂 Project Structure

```
zomato-order-analytics/
├── data/
│   └── Zomato_Dataset.xlsx
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_derived_metrics.ipynb
│   └── 03_analysis_answers.ipynb
├── outputs/
│   ├── city_revenue_analysis.xlsx
│   ├── delivery_performance.xlsx
│   └── customer_experience_report.xlsx
└── README.md
```

---

⭐ *If this project helped you, consider starring the repository!*
