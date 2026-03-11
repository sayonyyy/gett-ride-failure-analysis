
---

# 🚕 Ride Failure Analysis — Gett Ride-Hailing Platform

![Project](https://img.shields.io/badge/Project-Product%20Analytics-red)
![Domain](https://img.shields.io/badge/Domain-Ride%20Hailing%20Analytics-yellow)

![Python](https://img.shields.io/badge/Python-3.12-blue)
![SQL](https://img.shields.io/badge/SQL-MySQL-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-black)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-blue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-green)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-teal)
![Folium](https://img.shields.io/badge/Folium-Interactive%20Maps-darkgreen)
![H3](https://img.shields.io/badge/H3-Spatial%20Indexing-purple)

A data analytics project investigating **why ride requests fail** on the **Gett ride-hailing platform (similar to Uber, Ola, and Lyft)**.

The goal of this project is to analyze ride request data and identify **operational bottlenecks affecting ride completion**, including driver assignment delays, demand spikes, waiting time behavior, and geographic failure hotspots.

---

# 📌 Project Objective

Ride-hailing platforms depend on efficient **driver-rider matching**. When the system fails to assign drivers quickly enough, users cancel rides or the system rejects requests.

This project analyzes failed ride requests to answer key product questions:

* Why do ride requests fail?
* When do ride failures occur?
* How does estimated arrival time affect cancellations?
* Where do ride failures occur geographically?
* How long do users wait before cancelling?

The analysis helps identify **operational inefficiencies** and suggests improvements to reduce ride failures.

---

# 📂 Dataset

The project uses two datasets:

### **orders**

| Column                        | Description                           |
| ----------------------------- | ------------------------------------- |
| order_datetime                | Time when the ride request was placed |
| origin_longitude              | Pickup longitude                      |
| origin_latitude               | Pickup latitude                       |
| m_order_eta                   | Estimated driver arrival time         |
| order_gk                      | Unique order ID                       |
| order_status_key              | Ride outcome (cancelled or rejected)  |
| is_driver_assigned_key        | Whether a driver was assigned         |
| cancellations_time_in_seconds | Time before cancellation              |

### **offers**

| Column   | Description             |
| -------- | ----------------------- |
| order_gk | Order identifier        |
| offer_id | Driver offer identifier |

---

# 🛠 Tech Stack

**Languages & Tools**

* Python
* SQL
* Jupyter Notebook
* MySQL
* VS Code

**Libraries**

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Folium
* H3 (Uber hexagonal spatial indexing)

---

# 🔎 Key Analyses

## 1️⃣ Failure Reasons Analysis

Investigated the distribution of ride failures by driver assignment status.

### Insight

Most ride failures occur **before a driver is assigned**, indicating a **driver supply shortage or slow matching algorithm**.

---

## 2️⃣ Ride Failures by Hour of Day

Analyzed how ride failures change throughout the day.

### Insight

Two major demand spikes were observed:

* **Morning commute (~8 AM)**
* **Late evening (~9–11 PM)**

During these periods, **demand exceeds available drivers**, leading to more failed ride requests.

---

## 3️⃣ ETA vs Ride Failures

Examined whether longer estimated arrival times increase ride failures.

### Insight

A large portion of failures occur when **ETA = 0**, meaning **no driver was assigned at all**.

This confirms that **driver matching failure is the main problem**, rather than slow driver arrival.

---

## 4️⃣ Driver Assignment Rate

Measured how often drivers are successfully assigned to ride requests.

### Insight

A significant number of ride requests **never receive a driver**, reinforcing the presence of a **supply-demand imbalance**.

---

## 5️⃣ Failure Types by Hour

Analyzed whether failures are caused by **client cancellations** or **system rejections** during different hours.

### Insight

Client cancellations are consistently higher than system rejections, suggesting that **users cancel rides when driver assignment takes too long**.

---

## 6️⃣ Cancellation Time Analysis

Measured how long users wait before cancelling ride requests.

### Insight

Users typically wait **1–3 minutes** before cancelling a ride.

If a driver is not assigned within this time window, cancellation probability increases significantly.

---

## 7️⃣ ETA Group Analysis

Grouped rides into ETA ranges:

* Short ETA (<60s)
* Medium ETA (<120s)
* Long ETA (>120s)

### Insight

Failures appear highest in the Short ETA group simply because **most ride requests fall into that category**, not because short ETA causes failures.

---

## 8️⃣ Geographic Failure Hotspot Analysis

Used **H3 hexagonal spatial clustering** and **Folium maps** to visualize ride failure concentrations.

### Insight

Certain geographic zones experience **significantly higher ride failure rates**, likely due to:

* High demand areas
* Driver shortages
* Traffic congestion

---

# 📊 Key Findings

The primary cause of ride failures on the Gett platform is:

**Driver-Rider Matching Failure**

Key contributing factors include:

* Driver supply shortages during peak hours
* High demand spikes
* Slow driver assignment
* Geographic imbalance in driver distribution

---

# 💡 Business Recommendations

Based on the analysis, the platform could reduce ride failures by:

1. **Increasing driver incentives during peak hours**
2. **Improving driver dispatch algorithms**
3. **Repositioning drivers toward high-demand zones**
4. **Reducing driver assignment latency**
5. **Using surge pricing or bonuses in high-demand areas**

---

# 🗺 Example Visualization

The project includes an interactive **ride failure hotspot map** using **H3 hexagonal grids** to highlight geographic failure clusters.

*(Example map generated using Folium)*

---

# 📁 Project Structure

```
gett-ride-failure-analysis
│
├── insights_from_failed_orders.ipynb
├── data_orders.csv
├── data_offers.csv
├── db_connection.py
├── ride_failure_hotspots.html
└── README.md
```
---

## 📦 Dataset Source

The dataset used in this project is provided through **StrataScratch**, a platform that hosts real-world datasets used for data science and analytics case studies.

The data originates from **Gett**, a ride-hailing platform similar to Uber, Lyft, and Ola.

Source: StrataScratch Ride Failure Analysis dataset.

Note: The dataset is anonymized and provided for educational and analytical purposes.

---

# 📈 Future Improvements

Possible extensions of this analysis include:

* Failure probability prediction models
* Driver supply forecasting
* Demand prediction during peak hours
* Real-time ride failure risk monitoring

---

# 👤 Author

**Sayony Chakraborty**

B.Sc. Data Science
Techno India University

🔗 LinkedIn
linkedin.com/in/sayonychakraborty

---

