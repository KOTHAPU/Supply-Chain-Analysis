### USA Sales Data Exploratory Data Analysis (EDA)
This project performs a comprehensive Exploratory Data Analysis (EDA) on a USA sales dataset to clean the data, handle missing values and outliers, and extract meaningful business insights regarding sales channels, logistics performance, and financial metrics.

📊 Project Overview
The notebook processes a dataset containing over 100,000 order records (later cleaned and filtered). It covers the end-to-end data preparation pipeline, including advanced date imputation, currency cleaning, and outlier capping using the IQR method.

🛠️ Technologies Used
Python 3.x

Pandas: Data manipulation and analysis.

NumPy: Numerical operations and handling nulls.

Matplotlib & Seaborn: Data visualization and statistical plotting.

Scipy (Stats): Statistical analysis.

Regex (re): String cleaning and pattern matching for IDs and Order Numbers.

🗂️ Dataset Description
The source file USA_sales_data.csv includes the following features:

Order Details: Order Number, Sales Channel, Order Quantity, Discount Applied.

Logistics: Warehouse Code, Procured Date, Order Date, Ship Date, Delivery Date.

Financials: Unit Cost, Unit Price, Currency Code.

Identifiers: Sales Team ID, Customer ID, Store ID, Product ID.

🚀 Data Cleaning Pipeline
1. Handling Missing Values
Order Numbers: Rows with missing Order_Number were dropped as they are unique identifiers.

Categorical Data: Missing Sales_Channel and Warehouse_Code were filled with "Unknown".

Advanced Date Imputation:

Converted columns to datetime objects.

Used median offsets to fill missing dates (e.g., estimating Order_Date based on Ship_Date minus the median shipping lag).

Financials: Cleaned currency symbols ($, ,) and filled missing Unit_Cost, Unit_Price, and Order_Quantity with their respective medians.

2. Feature Engineering
Created several calculated columns to improve business analysis:

Financial Metrics: Total_Price, Total_Cost, Revenue, Profit, and Profit_Margin.

Logistics Metrics:

Order_Processing_Time: Days between Order and Shipping.

Shipping_Time: Days between Shipping and Delivery.

Total_Delivery_Time: Total cycle from Order to Delivery.

Holding_Time: Days between Procurement and Shipping.

3. Consistency & Logic Checks
Removed duplicates (approx. 7,269 rows).

Enforced business logic:

Removed orders where Delivery_Date was before Ship_Date.

Removed orders where Unit_Price was less than Unit_Cost to ensure data integrity for profit analysis.

Standardized Order_Number format and Sales_Channel naming conventions.

4. Outlier Management
Identified outliers in numerical columns using the Interquartile Range (IQR) method.

Capping: Values falling below the lower limit or above the upper limit were capped to the boundary values to prevent extreme skews in analysis.

📈 Visualizations
The notebook includes:

Boxplots: Used before and after capping to visualize the distribution of numerical data and the impact of outlier handling.

Distribution Analysis: Examining the frequency of orders across different sales channels.

💾 Output
The final cleaned and processed dataset is exported as:
cleaned_order_data.csv
