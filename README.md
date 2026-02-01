# Data Virtualized Project - Inventory-to-Sales Reporting Solution (Denodo)

## 📌 Project Overview
This project documents the development of a virtualized **Inventory-to-Sales** reporting solution built using **Denodo**. It addresses "data blind spots" in retail supply chain management by federating nine disparate CSV data sources into a unified, real-time reporting view.

The solution bridges the gap between available stock and customer demand, enabling stakeholders like the **Chief Operations Officer (COO)** and **Regional Supply Chain Managers** to identify stockout risks, track aging inventory, and analyze regional profitability without the overhead of physical data consolidation.

---

## 🚀 Key Features & Engineered Intelligence
To transform raw data into actionable insights, several engineered features were developed within the virtualization layer:

* **Stock Status Automation**: A categorical label (`stock_status`) that instantly flags items as 'CRITICAL LOW', 'OVERSTOCK', or 'HEALTHY' based on live quantity counts.
* **Net Revenue Calculation**: An engineered metric (`net_revenue`) that reveals true profitability by accounting for discounts and list prices.
* **Status Translation**: A user-friendly conversion of integer database codes into readable statuses like 'Pending' or 'Completed'.
* **Stock Value Quantification**: A cost metric (`stock_value`) used to measure the total financial capital tied up in unsold inventory.
* **Data Standardization**: Implementation of standardized base views to ensure referential integrity across sales and production datasets.

---

## 🛠️ Technical Architecture
The Denodo database (`dvrt_asg_jaydentee`) follows a tiered folder structure for scalability and clarity:

1.  **01_connectivity**: Dedicated CSV data source connections using the Denodo delimited file connector.
2.  **02_base_views**: Standardized views defining the schema and contracts for the underlying data.
3.  **03_integrated_views**: Intermediate views (e.g., `iv_sales_master`) that resolve "Product Logic" and "People Logic".
4.  **04_finalize_views**: The business-ready reporting view (`rv_regional_supply_chain`).
5.  **05_web_service**: Deployment of the final view as a RESTful web service.

---

## 📊 Data Sources
The solution integrates 9 core business entities from the bicycle retail ecosystem:
* **Sales Data**: `customers`, `staff`, `orders`, `stores`, and `order_items`.
* **Production Data**: `categories`, `products`, `stocks`, and `brands`.

---

## 🌐 Deployment & Security
The finalized view was deployed as a **REST Web Service** (`ws_regional_supply_chain`) to enable lightweight, real-time consumption by downstream BI tools like Tableau or PowerBI.

* **Protocol**: REST (selected for universal compatibility and performance over SOAP).
* **Formats**: Supports HTML, XML, and JSON representations.
* **Security**: Secured using **HTTP Basic Authentication with VDP**, ensuring that only authorized users can access the data.

---

## 📈 Key Learning Outcomes
* **Logical Integration**: Mastered joining and transforming data without physical movement.
* **Grain Alignment**: Successfully aligned "Transaction Grain" (Sales) with "Store-Product Grain" (Inventory) using composite join keys (`product_id` + `store_id`).
* **Business Logic Centralization**: Derived critical metrics within the virtualization layer to prevent conflicting calculations in BI tools.

---
