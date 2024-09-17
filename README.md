### I. Project Description

This project involves analyzing a real-world dataset to enhance supply chain analytics. As the primary data analyst for Just In Time, your role is to address key challenges in shipment and inventory management, identify supply chain inefficiencies, and develop insightful dashboards. These dashboards will inform business stakeholders about potential problems and suggest structural business improvements.

### II. Methodology

**Business Demand Analysis**

**Requirements:** Create a dashboard to analyze business problems and improve supply chain efficiency.

**Method:** Descriptive, exploratory, and diagnostic analysis.

**Tools Used:**
- **Python:** For data preprocessing, data cleaning, exploratory data analysis (EDA), and inventory segmentation.
- **Power BI:** For creating interactive dashboards.

**Dashboards:**

- **Sales Manager:** Overview and track customer demand and product sales.
  - Includes sales, profit, orders, customers, best products, etc.
  
- **Inventory Manager:** Control inventory flow, including order fulfillment, storage, and distribution.
  - Includes warehouse inventory, customer orders, storage costs, etc.
  
- **Shipping Manager:** Oversee daily shipping and distribution operations to customers.
  - Includes orders, locations, timing, delayed shipments, etc.

**Overall Target:** Create an interactive dashboard to summarize supply chain issues and suggest solutions.

### III. Data Preprocessing

**Data Overview**

The dataset includes three tables: order_and_shipment, inventory, and fulfillment. Key information includes:

- **Customer:** General information about customers, including identifiers and addresses.
- **Order:** Information about orders, including order date, product, quantity, and order value.
- **Shipment:** Shipping information, including shipping date and mode.
- **Product:** Specific information about ordered items, including product name, category, and department.
- **Warehouse Inventory:** Information on inventory management, including monthly inventory, warehouse location, storage costs, and order fulfillment.

**Data Cleaning**

- Dropped unnecessary columns (Order Item ID, Order Time).
- Fixed data types of columns.
- Removed special characters in the Customer Country column.
- Checked for missing and duplicate values.
- Addressed product name inconsistencies between the order and inventory tables.
- Handled negative and unusually large shipping times by referencing standard shipping durations and dropping outliers.

**Feature Creation**

- Created datetime features from day, month, and year.
- Created shipment features to indicate on-time or late orders.
  - **Shipping Time:** Shipment Date - Order Date.
  - **Delayed Shipment:** Marked as late if Shipment Day - Schedule < Shipping Time.
  - **Late Shipment Rate:** Total late orders / Total orders.
- Created business performance features.
  - **Net Sales:** Gross sales - (Discount * Gross sales).
  - **Unit Price:** Gross sales / Order quantity.
  - **Profit Margin:** Total profit / Total net sales.
  - **Storage Cost:** Inventory cost per unit * Warehouse inventory.

### IV. Exploratory Data Analysis (EDA)

**Key Analysis Areas and Questions:**

**Business Performance**
- Total net sales, profit, and profit margin by the company.
- Average net sales and profit per month.
- Changes in net sales and profit over time.
- Changes in the number of orders over time.
- Changes in average order quantity and unit price over time.
- Product departments contributing the most to net sales and orders.

**Customer**
- Distribution of customers by country and market.
- Number of customers over time.
- Patterns or trends in buying behavior over time.

**Product**
- Most preferred product categories and names.
- Most profitable product categories and names.

**Inventory**
- Product departments contributing most to warehouse inventory and storage costs.
- Distribution of inventory cost per unit by product department.
- Changes in warehouse inventory and storing costs over time.
- Product names and departments contributing most to storing costs.
- Average order fulfillment.
- Average order fulfillment by product department.

**Shipment**
- Warehouses from which orders are shipped.
- Preferred shipment modes by customers.
- Shipping time for each shipment mode.
- Late shipment rate by product department and market.
- Fluctuations in late shipment rate over time.

**Summary of Findings**

- The company has had strong business performance over the past three years, with net sales of approximately $5.5 million and a profit of nearly $4 million, resulting in a profit margin of up to 72%.
- A significant decline in the number of orders has led to a sharp decrease in net sales and profit. Both metrics declined simultaneously, indicating stable costs but serious revenue issues.
- The downturn is linked to the absence of previously best-selling items (Apparel, Fanshop, Footwear, Golf).
- Customer buying behavior has changed, but overall demand has remained relatively stable.
- There may have been a supply chain disruption causing a significant drop in both revenue and storage costs.
- The company may have intentionally tested new products, leading to the removal of old best-sellers.
- Best-selling products have the longest replenishment times, while newer products like Technology and Health and Beauty have shorter times.
- The company faces issues with high late shipment rates, indicating inefficiencies in the delivery system.

### V. Hypothesis Issues Trees

**Situation:** The company had stable revenue and profit from 2015 to Q3/2017, mainly from key product departments such as Apparel, Golf, and Fanshop.

**Complication:** A sharp decline in Q4/2017 due to a supply chain incident resulted in a revenue drop from key product departments.

**Question:** How can the company recover and re-establish its business while addressing supply chain weaknesses?

**Hypotheses:**
1. **Customer Preference Change:** Customers may have changed their buying behavior.
2. **Supplier Issues:** Suppliers may have been unable to deliver products on time.
3. **Product Offerings Change:** The company may have intentionally changed its product offerings.
4. **Delayed Shipments:** High late shipment rates may have affected operations and customer loyalty.

### VI. Inventory Segmentation

**ABC XYZ Method:**

- **ABC:** Segments inventory based on value contribution (revenue).
  - **High Value:** Products contributing 80% of total net sales.
  - **Medium Value:** Products contributing 15% of the rest.
  - **Low Value:** Products contributing 5% of the rest.
- **XYZ:** Segments inventory based on demand volatility (coefficient of variation).
  - **Regular Demand:** CV < 0.25.
  - **Variable/Seasonal/Trendy Demand:** 0.25 ≤ CV ≤ 0.5.
  - **Irregular Demand:** CV > 0.5.

### VII. Suggestion

**Restore Revenue and Profit:**

**XA, YA Segments:**
- These segments are in high demand and are key revenue sources. Finding new suppliers and redesigning the supply chain to prevent future disruptions is essential. Investigate supply chain issues and identify suitable alternative suppliers.

**XB, XC Segments:**
- These segments show growth potential. Conduct market research to understand current consumption trends and demands. Analyze local and global markets to identify opportunities and optimize inventory management.

**YB, YC, ZB, ZC Segments:**
- These segments have low demand and minimal revenue contribution. Consider dropping or reducing inventory to optimize storage costs.

**Overstock and Understock:**
- Implement demand forecasting using historical sales data and market trends. Set up reorder points based on lead time, sales velocity, and desired safety stock levels. Maintain safety stock to mitigate the risk of stockouts and excessive stock accumulation.

**Market Trends:**
- In Q4/2017, customers were predominantly from the Asia Pacific market, previously Europe. Anticipate customers from the Asia Pacific in Q1/2018 and North America in subsequent quarters to optimize inventory levels and predict product life cycles for each region.

**High Late Shipment Rate:**
- Optimize the delivery system by redesigning transportation routes, such as adopting a cross-docking strategy.
- Collaborate with local logistics companies to leverage their resources and expertise, especially in distant markets.
- Establish a warehouse in a strategic logistics hub like Singapore to improve the delivery process and facilitate smoother operations across international markets.
