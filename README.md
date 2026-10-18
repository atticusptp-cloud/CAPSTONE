# CAPSTONE PROJECT FOR NTUC LEARNING HUB PROJECT
* **Prepared by Atticus Poh**
* **Dataset used: 14.1 Hotel Bookings**
  
# Hotel Booking Cancellation 📊

<p align="center">
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/498567bb-27b0-4522-8b8b-3ac396eef551" />

</p>

<h1 align="center">Hotel Bookings Cancellation</h1>

This repository contains a transactional dataset capturing retail sales performance for consumer electronics products throughout the first half of **2026**. The data includes granular details on order parameters, product categories, geographic regions, salesperson mapping, and promotional discounts.

It serves as an excellent resource for exploratory data analysis (EDA), sales performance forecasting, regional market analysis, and missing data imputation practice.


## 📋 Dataset Overview

* **File Name:** `bookings.csv`, `Customer Types.csv`, `Hotels.csv`, `Market Segments.csv`, `Reservation Status.csv`
* **Time Horizon:** July 2015 – August 2027
* **Target Category:** Hotels Bookings Cancellation
* **Key Entities:** Products, Sales Team, Regional Markets, Revenue Metrics

  Link to Jupyter Notebook in Google Colab:
[  https://colab.research.google.com/drive/1zdPR2ig9qFp6Q1gPrZvky3Ac7UITW3Mv?usp=sharing](https://colab.research.google.com/drive/1qR-WG3Cuy9BQYkelKnsSL8fwCqMvxfIl)


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
| **Hotel_ID** | Float | Identifier of the hotel associated with the booking. | `1 - Resort Hotel`, `2 - City Hotel` |
| **Market_Segment_ID** | String | Identifier of the booking market segment and distribution channel. | `1`, `2`, `23` |
| **Customer_Type_ID** | String | Identifier of the customer classification, deposit type, and meal plan. | `1`, `2`, `23` |
| **Reservation_ID** | String | Identifier of the reservation status. | `1`, `2`, `3`|
| **is_canceled** | String | Indicates whether the booking was canceled. | `0`, `1` |
| **lead_time** | Integer | Number of days between booking creation and arrival date. | `0`, `2`, `521` |
| **arrival_date_year** | Float | Year of guest arrival. | `2015`, `2016`, `2017`|
| **arrival_date_month** | Float | Month of guest arrival. | `April`, `August`, `November`|
| **arrival_date_week_number** | Float | Week number of guest arrival. | `1`, `8`, `53`|
| **arrival_date_day_of_month** | Float | Day of the month of guest arrival. | `997.|
| **stays_in_weekend_nights** | Float | Number of weekend nights booked. | `997.|
| **stays_in_week_nights** | Float | Number of weekday nights booked. | `997.|
| **adults** | Float |Number of adult guests included in the booking. | `0`, `2`, `50`|
| **babies** | Float | Number of babies included in the booking.| `6983.69` |
| **country** | Float | Country of origin of the guest. | `6983.69` |
| **is_repeated_guest** | Float | Indicates whether the guest has booked previously. | `6983.69` |
| **previous_cancellations** | Float | Number of previous canceled bookings by the guest. | `6983.69` |
| **previous_bookings_not_canceled** | Float | Number of previous completed bookings by the guest. | `6983.69` |
| **booking_changes** | Float | Number of modifications made to the booking. | `6983.69` |
| **agent** | Float | Travel agent identifier associated with the booking. | `6983.69` |
| **company** | Float | Company identifier associated with the booking. | `6983.69` |
| **days_in_waiting_list** | Float | Number of days the booking remained on a waiting list. | `6983.69` |
| **adr** | Float | Average Daily Rate charged for the booking. | `6983.69` |
| **required_car_parking_spaces** | Float | Number of parking spaces requested by the guest. | `6983.69` |
| **total_of_special_requests** | Float | Number of special requests submitted by the guest. | `6983.69` |
| **reservation_status_date** | Float | Date on which the reservation status was recorded. | `6983.69` |

## 🔍 Data Quality & Cleaning Notes

If you are using this dataset for data cleaning projects, please note that it intentionally contains realistic real-world data anomalies:
* **Missing Values (NaNs):** Features like `Region`, `Salesperson`, `Unit_Price`, `Discount`, and `Sales` contain scattered missing fields (e.g., missing revenue values or unattributed regional boundaries).
* **Calculated Columns:** The `Sales` column follows the general formula:  
  \[\text{Sales} = (\text{Quantity} \times \text{Unit\_Price}) \times (1 - \text{Discount})\]
  This relationship can be exploited to programmatically restore missing metrics.
* **Empty Rows:** The raw structure contains blank structural divider rows (`,,,,,,,,,`) that should be filtered out during preprocessing.

## 🛠️ Usage Example (Python & Pandas)

Get started analyzing this dataset quickly using Python:

```python
import pandas as pd

# Load the dataset and drop completely empty structural lines
df = pd.read_csv('sales_data.csv').dropna(how='all')

# Convert date column to datetime object
df['Date'] = pd.to_datetime(df['Date'])

# Quick view of total sales revenue by product
revenue_by_product = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
print("Revenue by Product:\n", revenue_by_product)
