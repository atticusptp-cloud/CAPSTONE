# CAPSTONE PROJECT FOR NTUC LEARNING HUB PROJECT
* ** Prepared by Atticus Poh**
* ** Dataset used: 14.1 Hotel Bookings**
  
# Hotel Booking Cancellation 📊

<p align="center">
 <img width="266" height="205" alt="image_1e16842e_edited" src="https://github.com/user-attachments/assets/699034ae-2410-4f06-ae9d-66dd5003594f" />
</p>

<h1 align="center">Hotel Booking Cancellation</h1>

This repository contains a transactional dataset capturing retail sales performance for consumer electronics products throughout the first half of **2026**. The data includes granular details on order parameters, product categories, geographic regions, salesperson mapping, and promotional discounts.

It serves as an excellent resource for exploratory data analysis (EDA), sales performance forecasting, regional market analysis, and missing data imputation practice.

<img width="1317" height="742" alt="image" src="https://github.com/user-attachments/assets/fd2d0b2f-b7d0-4953-8c8b-868132c2485a" />

## 📋 Dataset Overview

* **File Name:** `product_sales_practice.csv`
* **Time Horizon:** January 2026 – June 2026
* **Target Category:** Electronics
* **Key Entities:** Products, Sales Team, Regional Markets, Revenue Metrics

  Link to Jupyter Notebook in Google Colab:
  https://colab.research.google.com/drive/1zdPR2ig9qFp6Q1gPrZvky3Ac7UITW3Mv?usp=sharing


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
| **Booking_ID** | String | A unique alphanumeric identifier for each hotel booking. | `ORD078` |
| **Hotel_ID** | Float | The transaction date formatted as `YYYY-MM-DD`. | `2026-04-09` |
| **Market_Segment_ID** | String | The name of the electronic item sold. | `Laptop`, `Mouse`, `Webcam` |
| **Customer_Type_ID** | String | The high-level category classification. | `Electronics` |
| **Reservation_ID** | String | The geographic sales territory. | `North`, `East`, `West`, `South` |
| **Is_canceled** | String | The name of the account representative. | `Alice`, `Bob`, `Charlie`, `Diana`, `Ethan` |
| **Lead-time** | Integer | The total units purchased in the order. | `7.0` |
| **arrival_date_year** | Float | The retail price per single unit of the product. | `997.|
| **arrival_date_month** | Float | The retail price per single unit of the product. | `997.|
| **arrival_date_week_number** | Float | The retail price per single unit of the product. | `997.|
| **arrival_date_day_of_month** | Float | The retail price per single unit of the product. | `997.|
| **stays_in_weekend_nights** | Float | The retail price per single unit of the product. | `997.|
| **stays_in_week_nights** | Float | The retail price per single unit of the product. | `997.|
| **adults** | Float | The promotional deduction percentage applied (0.0 to 0.15). | `0.15` (equivalent to 15%) |
| **babies** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **country** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **is_repeated_guest** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **previous_cancellations** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **previous_bookings_not_canceled** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **booking_changes** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **agent** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **children** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **children** | Float | The final calculated gross revenue earned from the order. | `6983.69` |
| **children** | Float | The final calculated gross revenue earned from the order. | `6983.69` |




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
