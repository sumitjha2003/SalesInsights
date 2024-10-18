# **Sales Insights of Data Analysis – AtliQ Hardware**

## **Overview**  
This project analyzes the sales performance of *AtliQ Hardware*, an Indian company supplying computer hardware and peripherals. The sales director faced challenges tracking regional sales efficiently, leading to declining performance. The goal was to develop a **data-driven dashboard** using MySQL and Power BI to provide actionable insights, helping managers make better decisions and improve business growth.

---

## **Project Execution Summary**

### **AIMS Grid (Project Planning)**  
- **Purpose**: Provide automated sales insights for data-driven decision-making.  
- **Stakeholders**: Sales Director, Marketing, IT, Customer Service, Data Teams.  
- **Outcome**: Interactive dashboard to replace manual reporting.  
- **Success Metrics**:  
  - 10% cost savings from improved decisions.  
  - 20% time saved by automating data gathering.  

### **Execution Flow**  
The project followed structured steps: data discovery, cleaning, analysis using SQL, transformation in Power BI, and dashboard creation.

---

## **Data Analysis Using MySQL**

Data was imported into **MySQL** to identify patterns, filter incorrect values, and assess performance by region. Some key queries include:  
- **Retrieve all customers**:  
  ```sql
  SELECT * FROM sales.customers;
  ```
- **Revenue for Chennai in 2020**:  
  ```sql
  SELECT SUM(sales_amount) 
  FROM sales.transactions 
  INNER JOIN sales.date ON transactions.order_date = date.date 
  WHERE date.year = 2020 AND market_code = 'Mark001';
  ```
- **Filter invalid transactions**:  
  ```sql
  SELECT * FROM sales.transactions WHERE sales_amount < 0 OR currency = 'USD';
  ```

---

## **Data Cleaning & ETL Process**  
Data from MySQL was loaded into **Power BI** for transformation:  
1. **Filtered Null & Invalid Values**: Cleaned tables with blank entries and negative sales amounts.  
2. **Currency Conversion**:  
   USD values were converted to INR for consistent reporting. Formula used in Power Query:  
   ```  
   if [currency] = "USD" then [sales_amount] * 75 else [sales_amount]
   ```  
3. **Removed Duplicates**: Unnecessary duplicates of currency fields were deleted for clarity.

---

## **Data Modeling**  
A **star schema** was built to efficiently connect transactions, customers, markets, and dates, ensuring optimal data relationships for the dashboard.

---

## **DAX Metrics and Insights**  
Key metrics used in Power BI:  
- **Revenue**:  
  ```dax
  SUM('sales transactions'[sales_amount])
  ```
- **Profit Margin %**:  
  ```dax
  DIVIDE([Total Profit Margin], [Revenue], 0)
  ```
- **Revenue YoY Comparison**:  
  ```dax
  CALCULATE([Revenue], SAMEPERIODLASTYEAR('sales date'[date]))
  ```

---

## **Dashboard & Visualization in Power BI**

The dashboard provided visual insights into revenue, profit margins, and regional performance. Some key metrics include:
- Revenue and profit trends by region and product.
- Year-over-year (YoY) comparison of key financial indicators.
- Profit contribution percentage across various business segments.

---

## **Tools & Technologies Used**  
1. **MySQL**: For database management and analysis.  
2. **Microsoft Power BI**: For interactive dashboards and reporting.  
3. **Power Query**: For data transformation.  
4. **DAX (Data Analysis Expressions)**: For building custom metrics.

---

## **Conclusion**  
This project automated the sales reporting process, providing quick insights through an interactive dashboard. The improved visibility enabled managers to take data-backed decisions, driving business growth efficiently.

---