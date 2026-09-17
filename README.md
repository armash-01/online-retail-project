# Online Retail — Data Cleaning & Power BI Dashboard

An end-to-end data analytics project on the **Online Retail** dataset (UCI Machine Learning Repository): raw transactional data is cleaned and transformed with Python/Pandas, then visualized in an interactive Power BI dashboard.

## 📌 Project Overview

This project has two parts:

1. **ETL Notebook** (`online_retail_etl.ipynb`) — cleans and transforms the raw e-commerce transaction data.
2. **Power BI Dashboard** (`online_retails.pbix`) — a single-page interactive report built on top of the cleaned dataset, surfacing key sales KPIs and trends.

## 🗂️ Dataset

- **Source:** [Online Retail Dataset – UCI ML Repository](https://archive.ics.uci.edu/dataset/352/online+retail)
- **Format:** `.xlsx` (raw) → `.csv` (cleaned)
- **Columns:** `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`

> The raw Excel file is not included in this repo. Download it from the source above and place it in a `data/` folder before running the notebook (update the file path in the first cell accordingly).

## 🧹 ETL / Cleaning Steps

The notebook processes the raw data in the following stages:

1. **Extract the Data** – Load the raw `.xlsx` file with `pandas`.
2. **Understand the Columns** – Inspect shape, dtypes, and summary statistics.
3. **Remove Duplicate Transactions** – Identify and drop exact duplicate rows.
4. **Handle Missing CustomerID** – Quantify missing values and fill/flag them as `"Unknown"`.
5. **Convert InvoiceDate** – Cast to proper `datetime` type.
6. **Create SalesAmount** – Engineer a new column: `Quantity * UnitPrice`.
7. **Identify Cancelled Invoices** – Detect invoices starting with `"C"` (cancellations) and remove them.
8. **Handle Negative Quantity** – Remove rows with negative/invalid quantities.
9. **Standardize Product Description** – Strip whitespace, uppercase text, drop nulls.
10. **Create Year, Month, Quarter** – Engineer date-based columns for time-series analysis.
11. **Create Final Clean Dataset** – Export the cleaned data to `cleaned_online_ret.csv`.

## 📊 Power BI Dashboard

The `online_retails.pbix` file is a single-page dashboard (**"online_retail_dashboard"**) built on the cleaned dataset, featuring:

- **KPI Cards:** Total Sales, Unique Customers, Total Orders, Total Quantity
- **Line Chart:** Total Sales trend by Month
- **Table:** Total Sales by Product Description
- **Clustered Bar Chart:** Total Sales by Country
- **Bar Charts:** Total Sales by Customer, and Total Quantity by Product Description
- **Slicer:** Filter the whole report by Year

## 🛠️ Tech Stack

- Python 3, Pandas, openpyxl (ETL)
- Jupyter Notebook
- Power BI Desktop (dashboard/reporting)

## 🚀 How to Run

**ETL:**
1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
2. Install dependencies:
   ```bash
   pip install pandas openpyxl jupyter
   ```
3. Download the dataset from the UCI link above and place it in a `data/` folder.
4. Update the file path in the first cell of the notebook to point to your local copy.
5. Run the notebook:
   ```bash
   jupyter notebook online_retail_etl.ipynb
   ```
   This produces `cleaned_online_ret.csv`.

**Dashboard:**
1. Open `online_retails.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. If prompted, repoint the data source to your local `cleaned_online_ret.csv`.
3. Refresh the report.

## 📤 Output

- `cleaned_online_ret.csv` — analysis-ready dataset used by the dashboard.
- `online_retails.pbix` — interactive sales dashboard.

## 📈 Possible Next Steps

- RFM (Recency, Frequency, Monetary) customer segmentation
- Cohort / repeat-purchase analysis
- Publish the dashboard to the Power BI Service for sharing
- Add product-category and returns analysis

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
