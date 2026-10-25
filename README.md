# CAPSTONE PROJECT FOR NTUC LEARNING HUB PROJECT
* **Prepared by Atticus Poh**
* **Dataset used: 14.1 Hotel Bookings**
  
# Hotel Booking Cancellation 📊

<p align="center">
<img width="400" height="250" alt="image" src="https://github.com/user-attachments/assets/498567bb-27b0-4522-8b8b-3ac396eef551" />

</p>

<h1 align="center">Hotel Bookings Cancellation</h1>

This repository contains a transactional dataset capturing the bookings received and bookings cancellation for 2 Hotels - a City Hotel & a Resort Hotel. An end-to-end data analytics project on 119,390 hotel bookings (City Hotel and Resort Hotel, July 2015 – August 2017). It measures how much cancellations cost, finds the bookings, channels and guests most likely to cancel, analyses pricing and demand, and builds a Multiple Linear Regression model to predict the room price (ADR).


## 📋 Dataset Overview

* **File Name:** `bookings.csv`, `Customer Types.csv`, `Hotels.csv`, `Market Segments.csv`, `Reservation Status.csv`
* **Time Horizon:** July 2015 – August 2027
* **Target Category:** Hotels Bookings Cancellation
* **Key Entities:** Market Segment, Customer Type, Country, ADR, Cancellation 

  Link to Jupyter Notebook in Google Colab:
https://raw.githubusercontent.com/atticusptp-cloud/CAPSTONE/refs/heads/main/capstone_analysis.ipynb


## Problem Statement

More than a third of all bookings were cancelled. Cancellations leave rooms empty at short notice and cost revenue on the hotels expected to earn. Management wants to know the severity of the issue, which bookings are most at risk, which channels and guests are most reliable, and how room prices move with seasonality and demand.


##    Research Objectives

1. Measure overall booking and cancellation performance. Measure booking volume, cancellation rate, ADR (average daily rate) and revenue lost to cancellations. Compare the City Hotel with the Resort Hotel, and look at changes by year, month and season.
2. Find the booking factors linked to cancellations. Test how lead time, deposit type, previous cancellations, booking changes, special requests, waiting-list days and parking requests relate to whether a booking is canceled. Early data points to some strong signals. Non-refundable bookings are canceled 99% of the time, which suggests a data or process problem worth investigating. Group bookings are canceled 61% of the time.
3. Evaluate market segments and distribution channels. Compare cancellation rates, ADR and revenue across segments such as Online TA, Offline TA/TO, Groups, Direct and Corporate. The goal is to show which channels bring in the most valuable and most reliable bookings.
4. Profile customer types and guest behaviour. Compare customer types (Transient, Contract, Group, Transient-Party), repeat and first-time guests, meal plans, party makeup (adults, children, babies) and country of origin. This shows which guest profiles are most loyal and which carry the most risk.
5. Analyse pricing and demand patterns. Look at how ADR changes by hotel, month, room demand and length of stay, and whether price level affects the chance of cancellation.
   
## 🗂️ Data Dictionary

The dataset consists of the following 28 features:

| Column Name | Data Type | Description | Example Value |
| :--- | :--- | :--- | :--- |
| **Booking_ID** | String | Unique identifier assigned to each booking record. | `13117` |
| **Hotel_ID** | String | Identifier of the hotel associated with the booking. | `1 - Resort Hotel`, `2 - City Hotel` |
| **Market_Segment_ID** | String | Identifier of the booking market segment and distribution channel. | `1`, `2`, `23` |
| **Customer_Type_ID** | String | Identifier of the customer classification, deposit type, and meal plan. | `1`, `2`, `23` |
| **Reservation_ID** | String | Identifier of the reservation status. | `1`, `2`, `3`|
| **is_canceled** | Integar | Indicates whether the booking was canceled. | `0`, `1` |
| **lead_time** | String | Number of days between booking creation and arrival date. | `0`, `2`, `521` |
| **arrival_date_year** | String | Year of guest arrival. | `2015`, `2016`, `2017`|
| **arrival_date_month** | String | Month of guest arrival. | `April`, `August`, `November`|
| **arrival_date_week_number** | String | Week number of guest arrival. | `1`, `8`, `53`|
| **arrival_date_day_of_month** | String | Day of the month of guest arrival. | `997.|
| **stays_in_weekend_nights** | Integar | Number of weekend nights booked. | `997.|
| **stays_in_week_nights** | Integar | Number of weekday nights booked. | `997.|
| **adults** | Integar |Number of adult guests included in the booking. | `0`, `2`, `50`|
| **babies** | Integar | Number of babies included in the booking.| `6983.69` |
| **country** | String | Country of origin of the guest. | `6983.69` |
| **is_repeated_guest** | Integar | Indicates whether the guest has booked previously. | `6983.69` |
| **previous_cancellations** | Integar | Number of previous canceled bookings by the guest. | `6983.69` |
| **previous_bookings_not_canceled** | Integar | Number of previous completed bookings by the guest. | `6983.69` |
| **booking_changes** | Integar | Number of modifications made to the booking. | `6983.69` |
| **agent** | String | Travel agent identifier associated with the booking. | `6983.69` |
| **company** | String | Company identifier associated with the booking. | `6983.69` |
| **days_in_waiting_list** | String | Number of days the booking remained on a waiting list. | `6983.69` |
| **adr** | Float | Average Daily Rate charged for the booking. | `6983.69` |
| **required_car_parking_spaces** | Integar | Number of parking spaces requested by the guest. | `6983.69` |
| **total_of_special_requests** | Intergar | Number of special requests submitted by the guest. | `6983.69` |
| **reservation_status_date** | String | Date on which the reservation status was recorded. | `6983.69` |

## 🔍 Key Findings

## Headline numbers
| Metric | Value |
| :--- | :--- |
| Bookings (after cleaning)	| 118,561 |
| Cancellation rate | 37.3% |
| Average daily rate (ADR)	|        102.48 |
| Realised revenue | 26.0M |
|  Revenue lost to cancellations |	    16.7M (39% of booked value)



## Insights by objective

## 1. Performance

The City Hotel cancels 41.9% of bookings and the Resort 28.0%. The City Hotel accounts for 10.9M of the 16.7M lost.
Comparing January – August, 2017 had 11% more bookings and a 15% higher ADR than 2016, but cancellations also rose, from 34.9% to 38.8%.
<img width="1314" height="752" alt="image" src="https://github.com/user-attachments/assets/2343f72b-44d4-47ad-89f7-b620e0ee02c1" />

## 2. Cancellation factors

Cancellation rises steadily with lead time, from 9.7% for bookings made 0 – 7 days ahead to 67.7% for 365+ days.
Non-Refund bookings cancel 99.4% of the time. The investigation found that 97% come from Portugal, 97% come through Groups or Offline travel agents, and 93% are duplicate rows. This points to agency block bookings being released, not real guests cancelling.
Guests with special requests or booking changes cancel much less (14 – 22% vs 41 – 48%).
A simple rule-based risk score (if / elif) separates the bookings well:
Risk level	Share of bookings	Actual cancellation rate
Low	19.1%	7.3%
Medium	53.1%	29.5%
High	27.8%	72.6%
<img width="984" height="496" alt="image" src="https://github.com/user-attachments/assets/8bb3f8c1-3af7-4683-8bca-f7457d27da66" />
<img width="988" height="492" alt="image" src="https://github.com/user-attachments/assets/8842c679-8f39-4ad6-8bc2-bff1328e2e39" />
<img width="1094" height="492" alt="image" src="https://github.com/user-attachments/assets/ba8baf9e-28ac-4654-8e06-3e04f21cd17a" />
<img width="1316" height="644" alt="image" src="https://github.com/user-attachments/assets/78e97a28-0f5c-4471-9fd5-d1769302c313" />
<img width="1308" height="740" alt="image" src="https://github.com/user-attachments/assets/8e929846-b921-4fbc-9e93-55fb21ce057a" />


## 3. Segments and channels

Online TA brings 53% of realised revenue (ADR ~118) but cancels 36.9% of the time.
Direct is the best segment: ADR ~117 with only 15.5% cancellation. Groups cancel 61.2% of the time.
<img width="1310" height="738" alt="image" src="https://github.com/user-attachments/assets/dae2b7be-86d5-43d5-a974-e0a845e4f1c6" />

## 4. Guests

Repeat guests cancel 15.7% vs 37.9% for first-time guests, but they make up only ~3% of bookings.
Transient guests are 75% of bookings and cancel 41%. Bookings from Portugal cancel 57.3%.
<img width="1310" height="740" alt="image" src="https://github.com/user-attachments/assets/dca8f197-82d0-4687-a1cc-78609aec0953" />
<img width="1314" height="740" alt="image" src="https://github.com/user-attachments/assets/8de86ff9-aaf5-470a-8c0e-acc9c889361b" />

## 5. Pricing and demand

The Resort's ADR rises from ~50 in January to ~183 in August, a seasonal premium.
City Hotel prices follow monthly demand closely (r = 0.80); the Resort's follow it only weakly (r = 0.29).
Price on its own barely predicts cancellation (r = −0.03 City, 0.10 Resort).
🤖 Predictive Model: Multiple Linear Regression (ADR)

The data is bookings that were actually stayed, with duplicates removed (60,795 rows), split 75/25 into training and test sets with random_state=42. Text columns were converted to numbers with .map() dictionaries.

Model	R²	RMSE
A. Simple LR (July/August only)	0.170	45.15
B. Multiple LR (both hotels)	0.498	35.12
C. Multiple LR (City Hotel only)	0.462	29.19
C. Multiple LR (Resort Hotel only)	0.718	31.54

Main price drivers (model B coefficients):

Feature	Effect on ADR
Half or full board	+33
Each child	+27
Summer arrival	+23
Online TA / Direct booking	+22
Each adult	+19
Each later year	+14.5
💡 Recommendations
Audit Non-Refund and agency block bookings. Check deposits are collected, and record released blocks separately from guest cancellations.
Tighten group contracts with release dates, attrition clauses and staged deposits.
Apply the risk rules to every new booking. Ask High-risk bookings for a deposit and send reminders.
Use controlled overbooking at the City Hotel in its peak months (April – June).
Re-confirm long lead-time bookings (90+ days ahead).
Grow direct and repeat business with loyalty perks and a best-rate guarantee.
Encourage special requests at booking. Engaged guests rarely cancel.
Pricing: keep the Resort's summer premium, use demand-based pricing at the City Hotel, and use the model to check quoted rates.
🗂️ Repository Structure
├── Hotel_Booking_Analysis.ipynb     # Main notebook (all outputs saved)
├── Hotel_Booking_Analysis.html      # Notebook as a web page
├── Hotel_Booking_Dashboard.html     # Interactive plotly dashboard
├── requirements.txt
├── README.md
└── data/
    ├── raw/
    │   ├── Bookings.csv             # Fact table (119,390 rows)
    │   ├── Hotels.csv
    │   ├── Market_Segments.csv
    │   ├── Customer_Types.csv
    │   ├── Reservation_Status.csv
    │   └── Data_Dictionary.docx
    └── processed/
        ├── hotel_bookings_clean.csv # Created by the notebook
        └── model_results.csv        # Created by the notebook
Data model

Bookings is the fact table. It joins to four lookup tables with left joins:

Hotels ──(Hotel_ID)──┐
Market_Segments ─────┼── Bookings ──┬── Customer_Types
                     │              └── Reservation_Status
🧹 Data Preparation Summary
Issue	Rows	Action
Missing children / country	4 / 488	Filled with 0 / "Unknown"
Missing agent / company	16,340 / 112,593	Filled with 0, plus has_agent / has_company flags
0 guests or 0 nights	180 / 715	Removed
Negative ADR, ADR = 5,400	2	Removed (checked with z-scores)
Undefined market segment	2	Removed
Duplicate rows (block bookings)	~33,000	Kept for analysis, removed for modelling

In total, 829 rows (0.69%) were removed.

| Recommendation |	Evidence |
| :--- | :--- |
| 1	Audit Non-Refund  agency block bookings. Check that deposits are really collected, and record released blocks separately from guest cancellations. |	99% "cancellation" on Non-Refund bookings; 97% from Portugal and Groups/Offline TA; 93% duplicate rows |
| 2	Tighten group and tour-operator contracts: release dates, attrition clauses, staged deposits. |	The Groups segment cancels 61% and loses 60% of its booked value |
| 3	Use the risk rules on every new booking. For High risk, ask for a deposit and send reminders. | For Low risk, change nothing.	High risk cancels ~73%, Low risk ~7%
| 4	Controlled overbooking at the City Hotel in its peak months. |	City Hotel cancels 42%, ~45% in April – June |
| 5	Lead-time policy: Do not allow more than 60 days bookings. Global Average is within 32 days  |	Cancellation rises from 10% (0 – 7 days) to 68% (365+ days) |
| 6	Grow direct and repeat business with loyalty perks and a best-rate guarantee on the hotel website. |	Direct segment ~15% and repeat guests ~16% cancellation, vs 37% overall |
| 7	Encourage engagement at booking: ask guests for special requests and preferences. |	0 requests = 48% cancel vs ≤ 22% with 1+ requests |
| 8	Pricing: keep the Resort summer premium, use demand-based pricing at the City Hotel, and use the regression model to check quoted rates. |	Resort ADR ×3.7 from January to August; City ADR follows demand; R² up to ~0.7 |

▶️ How to Run
bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
jupyter notebook Hotel_Booking_Analysis.ipynb

Then run Kernel → Restart & Run All. It takes under a minute. Keep the data/ folder next to the notebook.

Libraries used: pandas, numpy, matplotlib, seaborn, plotly, scipy, scikit-learn
