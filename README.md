
# 🗽 New York City Airbnb Market Analysis (2019)

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-00A699)

> An end-to-end data analysis project: from raw listings data to a cleaned dataset, exploratory analysis, an interactive Power BI dashboard, and business recommendations for the NYC short-term rental market.

<!-- Replace the path below with your dashboard overview screenshot -->
<img width="967" height="545" alt="overview" src="https://github.com/user-attachments/assets/2c375907-c1a0-44e8-897c-ddf55d16570c" />

---

## 📑 Table of Contents

1. [Project Overview](#-project-overview)
2. [Dataset](#-dataset)
3. [Tools & Skills](#-tools--skills)
4. [Data Cleaning & Preparation](#-data-cleaning--preparation)
5. [Exploratory Analysis](#-exploratory-analysis)
6. [Interactive Dashboard](#-interactive-dashboard)
7. [Key Findings & Business Insights](#-key-findings--business-insights)
8. [Recommendations](#-recommendations)
9. [Limitations](#-limitations)
10. [Repository Structure](#-repository-structure)
11. [How to Use This Project](#-how-to-use-this-project)
12. [Author](#-author)

---

## 🎯 Project Overview

**Business problem:** An Airbnb operations or investment team wants to understand where activity is concentrated in New York City, what drives listing prices, and which segments perform best, in order to guide pricing, host-acquisition, and market-expansion decisions.

**Goal:** Turn 48,000+ raw listings into clear, decision-ready insights by answering questions such as:

- What are the most common listing types?
- Which boroughs and neighborhoods have the highest activity?
- How do prices differ between areas and room types?
- Is there a relationship between price and review activity?
- Which neighborhoods and host segments stand out?

---

## 📦 Dataset

| Item | Detail |
|---|---|
| **Source** | Airbnb New York City listings (2019), provided with the project brief (the only dataset used) |
| **Raw size** | 48,895 rows × 16 columns |
| **Cleaned size** | 48,884 rows × 22 columns |
| **Coverage** | 5 boroughs, 221 neighborhoods, 3 room types |

**Main columns**

| Column | Description |
|---|---|
| `id`, `host_id` | Listing and host identifiers |
| `neighbourhood_group`, `neighbourhood` | Borough and neighborhood |
| `latitude`, `longitude` | Listing location |
| `room_type` | Entire home/apt, Private room, Shared room |
| `price` | Nightly price (USD) |
| `minimum_nights` | Minimum stay required |
| `number_of_reviews`, `reviews_per_month`, `last_review` | Review activity |
| `calculated_host_listings_count` | Number of listings per host |
| `availability_365` | Days available in the next year |

---

## 🛠 Tools & Skills

- **Python** (Jupyter Notebook, pandas) for cleaning, feature preparation, and exploratory analysis
- **Power BI** for the interactive dashboard (KPIs, slicers, cross-filtering)
- **Skills demonstrated:** data cleaning, outlier handling, feature engineering, EDA, data visualization, dashboard design, business storytelling

---

## 🧹 Data Cleaning & Preparation

| Issue | Action |
|---|---|
| Duplicates | Checked `id` and full rows, none found |
| Missing `reviews_per_month` | Filled with 0 for listings with no reviews (no reviews means a rate of zero) |
| Missing `last_review` | Kept as null instead of inventing dates; added `has_reviews` flag |
| Missing listing/host names | Handled; not needed for the analysis |
| Invalid prices | Removed 11 listings with price = 0 (48,895 → 48,884 rows) |
| Extreme prices | Flagged 239 listings priced above $1,000 with `is_extreme_price` rather than silently deleting them |
| Long-term stays | Flagged 747 listings with more than 30 minimum nights using `is_long_term_stay` |
| Data types | Converted `last_review` to a date type |

**Engineered features**

| Feature | Categories |
|---|---|
| `price_category` | Budget, Mid, Premium, Luxury |
| `stay_type` | Short, Medium, Long-term |
| `availability_category` | Not Available, Low, Medium, High |
| `has_reviews` | 1 if the listing has at least one review, else 0 |

---

## 🔍 Exploratory Analysis

The notebook ([`airbnb_data_analysis_code.ipynb`](airbnb_data_analysis_code.ipynb)) covers:

- Listing mix by room type and borough
- Price distribution and outlier behavior
- Price comparison by borough, neighborhood, and room type
- Relationship between price and review activity
- Host concentration (single vs multi-listing hosts)
- Availability and minimum-stay patterns
- Review activity over time and geographic distribution

---

## 📊 Interactive Dashboard

Built in Power BI: [`Airbnb Dashboard.pbix`](Airbnb%20Dashboard.pbix) (open with Power BI Desktop).

| Page | What it shows |
|---|---|
| **Market Overview** | KPI cards (total listings, unique hosts, median price, reviews per month, availability), listing map, room-type mix, listings and median price by borough |
| **Pricing & Guest Demand** | Price by borough and room type, top 10 neighborhoods by price and by volume, price vs review activity scatter, reviews by price tier |
| **Hosts, Availability & Activity** | Host portfolio size, top host names, availability levels, reviews by stay length, listings by year of last review, borough × room type matrix |

**Interactivity:** slicers for borough, room type, price tier, minimum stay, and host portfolio size, synced across pages, plus a reset button and cross-filtering between charts.

<!-- Replace with your screenshots (create an /images folder) -->
| Overview | Pricing & Demand | Hosts & Availability |
|---|---|---|
| <img width="967" height="545" alt="overview" src="https://github.com/user-attachments/assets/18fa2eca-39ac-40c4-af7e-57c6ee380c9b" />
| <img width="960" height="541" alt="pricing and performance" src="https://github.com/user-attachments/assets/1f6a1ff8-d070-4e32-bd45-921a70a3aec4" />
 | <img width="962" height="540" alt="host, availability and activity " src="https://github.com/user-attachments/assets/b8d09d82-bb0c-4ee3-9ebd-ab232502a64e" />
|

---

## 💡 Key Findings & Business Insights

| # | What I found | What it means |
|---|---|---|
| 1 | Manhattan (44%) and Brooklyn (41%) hold about **85% of all listings** | Supply is highly concentrated; outer boroughs are under-served |
| 2 | Median nightly price: **Manhattan $150**, Brooklyn $90, Queens and Staten Island $75, Bronx $65 | Location drives a large price premium |
| 3 | Entire homes have a median of **$160** vs **$70** for private rooms and $45 for shared rooms | Room type is a major price factor |
| 4 | **Tribeca** is the most expensive neighborhood with 30+ listings ($295 median); **Corona** is the cheapest ($40) | Price varies widely within boroughs, not only between them |
| 5 | Review activity falls as price rises: **1.18 reviews/month for Budget** vs **0.67 for Luxury** | Lower-priced listings see more guest activity |
| 6 | Outer boroughs show higher review rates per listing (Queens 1.57, Staten Island 1.58, Bronx 1.47) than Manhattan (0.98) and Brooklyn (1.05) | Strong engagement in less saturated markets |
| 7 | Listings with short minimum stays average **1.23 reviews/month** vs about **0.30** for stays over a week | Short minimum stays correlate strongly with activity |
| 8 | Listings in Manhattan belong to hosts with **12.8 listings on average** (2.2–4.1 elsewhere); 34% of all listings belong to multi-listing hosts | Professional operators are concentrated in Manhattan |
| 9 | **36% of listings** show zero availability, and about 21% have no reviews | A large share of inventory looks inactive |

---

## ✅ Recommendations

1. **Expand host acquisition in Queens, the Bronx, and Staten Island.** High review rates and low supply suggest unmet demand.
2. **Use neighborhood-level pricing guidance.** A single borough-wide price hides large differences (for example Tribeca vs the rest of Manhattan).
3. **Encourage shorter minimum stays.** Listings with minimum stays over a week see far less review activity.
4. **Run a re-activation campaign for inactive listings.** Zero-availability and no-review listings represent a large pool of potential supply.
5. **Monitor multi-listing host concentration in Manhattan.** It matters for market balance and for supporting individual hosts.
6. **Review pricing for high-end listings.** Luxury listings get the lowest review activity, so pricing or positioning may need adjusting.

---

## ⚠️ Limitations

- The dataset has **no rating score**, so review counts and review rate are used as a proxy for popularity.
- The dataset has **no booking or occupancy data**; `availability_365` shows how many days a listing is open, not how many were booked.
- Reviews are an imperfect proxy for bookings.
- The data is a **2019 snapshot**; trends over time are limited to `last_review` dates.
- Findings show **associations, not causation**.

---

## 📁 Repository Structure

```
airbnb_data_analysis/
├── Data_Files/                       # Dataset files used in the project
├── airbnb_data_analysis_code.ipynb   # Cleaning, EDA, and analysis notebook
├── Airbnb Dashboard.pbix             # Interactive Power BI dashboard
├── images/                           # Dashboard and chart screenshots
└── README.md
```

---

## 🚀 How to Use This Project

1. **Clone the repo**
   ```bash
   git clone https://github.com/kirlosmagdy/airbnb_data_analysis.git
   cd airbnb_data_analysis
   ```
2. **Explore the analysis:** open `airbnb_data_analysis_code.ipynb` in Jupyter Notebook or VS Code and run the cells in order.
3. **Explore the dashboard:** open `Airbnb Dashboard.pbix` in Power BI Desktop and use the slicers to filter by borough, room type, and more.

---

## 👤 Author

**Kirolos Magdy** — Data Engineer | Data Analytics

[![GitHub](https://img.shields.io/badge/GitHub-kirlosmagdy-181717?logo=github)](https://github.com/kirlosmagdy)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Kirolos%20Magdy-0A66C2?logo=linkedin)](https://www.linkedin.com/in/kirolos-magdy1/)

⭐ If you found this project useful, consider giving it a star!
