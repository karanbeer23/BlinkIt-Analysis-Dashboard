# 🟡 Blinkit Sales Analysis Dashboard

An interactive **Power BI** dashboard that analyses Blinkit (India's last-minute grocery delivery app) sales data across product categories, outlet types, locations, and establishment years.
> 📸 **Dashboard preview:** add a screenshot here (https://github.com/karanbeer23/BlinkIt-Analysis-Dashboard/blob/main/Snapshot%20of%20BlinkIt%20Analysis%20Dashboard.png).
---

## 📌 Overview

This project turns raw grocery sales data into a single-page, filterable report that helps answer questions like:

- How much are we selling in total, and what is the average sale per item?
- Which **item types** (Fruits & Vegetables, Snack Foods, Dairy, etc.) drive the most revenue?
- How do **Low Fat vs Regular** products perform across different outlets?
- Which **outlet sizes** and **location tiers** contribute the most sales?
- How have sales changed by **outlet establishment year**?
- How do customer **ratings** vary across outlet types?

---

## 📊 Dashboard Features

### KPI Cards
| KPI | Description |
|---|---|
| **Total Sales** | Sum of all sales |
| **Average Sales** | Average sales per item |
| **No. of Items** | Total number of item records |
| **Average Rating** | Mean customer rating |

### Visuals (Single Page, 1400 × 800)
| Visual | What it shows |
|---|---|
| **Fat Content (Donut)** | Sales split by Low Fat / Regular |
| **Item Type (Bar)** | Sales by product category |
| **Fat by Outlet (Clustered Bar)** | Fat content vs. outlet location tier |
| **Outlet Size (Donut)** | Sales share by Small / Medium / High outlets |
| **Outlet Location (Funnel)** | Sales by location tier (Tier 1, 2, 3) |
| **Outlet Establishment (Line)** | Sales trend by year the outlet was established |
| **Outlet Type Table (Matrix)** | Total sales, average sales, items, rating, and item visibility by outlet type |

### Interactivity
- **Filter panel (slicers):** Outlet Location Type, Outlet Size, Item Type
- **Dynamic metric selector:** a slicer lets you switch the main charts between *Total Sales*, *Avg Sales*, *Avg Rating*, and *No. of Items* (built with a field parameter)
- **Cross-filtering:** clicking the Fat Content donut filters the other charts on the page

---

## 🧮 DAX Measures

```DAX
Total sales    = SUM('BlinkIT Grocery Data'[Sales])
No Of Items    = COUNTROWS('BlinkIT Grocery Data')
Average Rating = AVERAGE('BlinkIT Grocery Data'[Rating])
Average sales  = AVERAGE('BlinkIT Grocery Data'[Sales])
```

A calculated `metrics` table (field parameter) powers the dynamic metric switcher:

```DAX
metrics = {
    ("Total sales", NAMEOF('measure'[Total sales]), 0),
    ("Avg Sales",   NAMEOF('measure'[Average sales]), 1),
    ("Avg Rating",  NAMEOF('measure'[Average Rating]), 2),
    ("No Of Items", NAMEOF('measure'[No Of Items]), 3)
}
```

---

## 🗂️ Dataset

**Source file:** `BlinkIT Grocery Data.xlsx` (single sheet, loaded via Power Query)

| Column | Type | Description |
|---|---|---|
| Item Identifier | Text | Unique product ID |
| Item Type | Text | Product category |
| Item Fat Content | Text | Low Fat / Regular |
| Item Weight | Decimal | Weight of the item |
| Item Visibility | Decimal | Share of display area allotted to the item |
| Outlet Identifier | Text | Unique outlet ID |
| Outlet Establishment Year | Integer | Year the outlet opened |
| Outlet Size | Text | Small / Medium / High |
| Outlet Location Type | Text | Tier 1 / Tier 2 / Tier 3 |
| Outlet Type | Text | Grocery Store / Supermarket Type 1, 2, 3 |
| Sales | Decimal | Sales amount |
| Rating | Integer | Customer rating |

> ⚠️ **Note:** The `.pbit` file is a Power BI **template** and does **not** contain the data itself. You need the Excel dataset to load the report.

---

## 🚀 Getting Started

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows)
- The `BlinkIT Grocery Data.xlsx` dataset

### Steps
1. **Clone the repository**
```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
```
2. **Place the dataset** (`BlinkIT Grocery Data.xlsx`) somewhere on your machine.
3. **Open** `BlinkIt_Analaysis.pbit` in Power BI Desktop.
4. If prompted for the data source, **browse to your Excel file** location, or update it later via  
   `Home → Transform data → Data source settings → Change Source`.
5. Click **Refresh** and the dashboard will load.

---

## 🛠️ Tech Stack

- **Power BI Desktop**: report design and interactivity
- **Power Query (M)**: data loading and type transformation
- **DAX**: measures and field parameters
- **Excel**: data source

---

## 📁 Repository Structure

```
├── BlinkIt_Analaysis.pbit      # Power BI template file
├── BlinkIT Grocery Data.xlsx   # Dataset (add this if you're allowed to share it)
├── images/
│   └── dashboard-preview.png   # Dashboard screenshot
└── README.md
```

---

## 🔮 Future Improvements

- Add more pages (customer ratings deep-dive, item visibility analysis)
- Add year-over-year growth and ranking measures
- Publish to Power BI Service and embed a live link
- Add tooltips and drill-through pages

---

## 👤 Author

**Karanbeer**  
---

⭐ If you found this project useful, consider giving it a star!
