

# 🚕 OLA Booking Dashboard | Data Analytics Project

This project is a **Business Analytics Case Study** of OLA Cabs booking data. Using **Power BI**, **SQL**, and a dataset of 20,000 rows, this project provides insights into customer behavior, ride trends, cancellation patterns, and key financial metrics from the perspective of a ride-hailing company.

---

## 📁 Project Components

| File Name                        | Description                                                   |
|----------------------------------|---------------------------------------------------------------|
| `Bookings-20000-Rows updated again.csv` | Raw booking dataset with 20,000+ entries                     |
| `SQL QUERY.pdf`                  | SQL queries for insights and data transformation             |
| `OLA DATA OUTPUT.pdf`            | Output and explanations for the executed SQL queries         |
| `Ola Booking Dashboard.pdf`      | Power BI dashboard snapshots and insights summary            |
| `Schema.png`                     | Data schema used for SQL querying and Power BI modeling      |

---

## 📊 Dashboard Highlights (Power BI)

| KPI                     | Value      |
|-------------------------|------------|
| ✅ Successful Rides     | 12,652     |
| ❌ Cancelled Rides      | 5,735      |
| 💰 Total Booking Value  | ₹6.90M     |
| ⭐ Average Driver Rating | 4.0        |

### Key Insights:

1. **Cancellation Rate:** ~31% of rides were cancelled.
2. **Top Vehicle Type by Booking Value:** Prime Sedan (₹1650K+).
3. **Most Preferred Payment Method:** Cash (₹3822K).
4. **Booking Trends:** Booking values are highest mid-week and drop slightly on weekends.
5. **Customer Insights:** Top customer (CID836942) has total booking value ₹3757.

---

## 🧠 SQL-Based Data Analysis

Executed multiple queries to derive actionable insights such as:

- 🔁 **7-day Moving Average** of Bookings  
- 📈 **Compare Current Ride vs. Average by Vehicle Type**  
- 🎯 **Top 5 Customers** by Number of Rides  
- 📍 **Most Popular Pickup Location**  
- 🛑 **Cancellation Analysis:** Reasons by customer/driver  
- 📊 **Booking Value by Payment Method & Status**

### Sample SQL Queries Used:
```sql
-- Get each customer's rank by total booking value
SELECT Customer_ID, RANK() OVER (ORDER BY SUM(Booking_Value) DESC) AS CustomerRank
FROM Bookings
GROUP BY Customer_ID;

-- Calculate 7-day moving average of bookings
SELECT Booking_Date, AVG(Total_Rides) OVER (ORDER BY Booking_Date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS Moving_Avg
FROM Daily_Bookings;
