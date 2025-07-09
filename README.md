# 🚗 Dynamic Parking Pricing System

> **Smart real-time pricing for urban parking lots using demand modeling and time-windowed streaming.**

---

## 🧩 Overview

This project dynamically adjusts parking prices using real-time and historical demand data. We simulate a smart city scenario using stream-processed parking sensor data and implement multiple pricing models based on demand, competition, and occupancy trends.

The output includes an interactive Bokeh visualization of price recommendations from three different pricing models.

---

## 🛠️ Tech Stack

| Category       | Technology                     |
| -------------- | ------------------------------ |
| Language       | Python 3.11                    |
| Data Streaming | [Pathway](https://pathway.com) |
| Visualization  | Bokeh, Panel                   |
| Notebook       | Google Colab                   |
| Deployment     | GitHub Pages (Bokeh HTML)      |

---

## 📐 Architecture Diagram (Mermaid)

```mermaid
graph TD
    A[CSV: Occupancy, Capacity, Timestamp] --> B[Preprocessing: Merge & Sort]
    B --> C[Pathway Input (Static Mode)]
    C --> D[Windowing: Daily Tumbling]
    D --> E1[Model 1: Linear]
    D --> E2[Model 2: Demand-Based]
    D --> E3[Model 3: Competitive]
    E1 --> F[JSONL Output]
    E2 --> F
    E3 --> F
    F --> G[Bokeh Plot: Price vs Time]
    G --> H[Export to HTML]

```

---

## ⚙️ Architecture and Workflow

### 1. **Data Ingestion**

* Raw dataset includes date, time, occupancy, and capacity for various parking lots
* We merge date and time to form a timestamp
* The first 300 rows are selected for fast simulation

### 2. **Streaming Engine**

* We use Pathway in `static` mode to simulate real-time streaming
* Data is windowed using tumbling windows of 1 day for temporal grouping

### 3. **Pricing Models**

#### ✅ Model 1: Baseline Linear Pricing

* Simple formula: `price = 10 + 5 * (occupancy / capacity)`

#### ✅ Model 2: Demand-Based Pricing

* Formula includes:

  * Occupancy
  * Queue length
  * Traffic level
  * Vehicle type
  * Special day flag

#### ✅ Model 3: Competitive Pricing Simulation

* `price = (occupancy / capacity) * 10`
* Placeholder for market-aware dynamic pricing

### 4. **Output Generation**

* Each model writes results to a `.jsonl` file
* We parse these into DataFrames
* Plot all 3 model outputs on one interactive Bokeh chart

---

## 📈 Visual Output

* 📁 `bokeh_output.html`: Interactive visualization of all models
* 📓 `Dynamic_Parking_Pricing_Updated_Static.ipynb`: Final executable notebook

---

## 📄  Report

A full project report is included here:
📄 [`Dynamic_Pricing_Report.pdf`]

---

## 🧠 Key Takeaways

* Model 2 provides the most realistic pricing logic
* Pathway is excellent for stream-time logic & windowing
* Easily expandable to real APIs for traffic, GPS, or competitor pricing

---

> Built for **Summer Analytics 2025** by **Akash K**
