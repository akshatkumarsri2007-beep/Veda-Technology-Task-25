# Veda-Technology-Task-25
# Multi-Table Sales Analysis (Northwind) using SQL

An end-to-end relational analysis of the classic **Northwind** dataset. Orders, order details, products, categories, customers and employees are combined with SQL JOINs to answer real business questions about revenue, customers, products and sales performance.

> Project completed as **Task 25 (Level 2)** of the Data Analytics Internship at **Veda Technology**.

---

## Objective

Combine the orders, products and customers tables and apply relational analysis from start to finish:

- Join multiple tables correctly and **validate the joins**
- **Avoid double counting** (one order has many product lines)
- Calculate key business metrics (revenue, orders, customers, average order value)
- Produce **5 business insights** backed by SQL

## Tech Stack

| Tool | Purpose |
|------|---------|
| SQL (SQLite) | Joins, aggregation, analysis |
| Python (pandas) | Loading CSV files into SQLite |
| Google Colab | Running the notebook |
| matplotlib | Charts for the report |

## Dataset

The Northwind sample database: a fictional trading company with orders from **July 1996 to May 1998**.

| Table | Rows | Description |
|-------|------|-------------|
| `orders` | 830 | One row per order |
| `order_details` | 2,155 | Product lines inside each order |
| `products` | 77 | Product catalogue |
| `categories` | 8 | Product categories |
| `customers` | 91 | Customer companies (89 placed orders) |
| `employees` | 9 | Sales employees |

**Revenue definition (after discount):**

```
revenue = unitPrice * quantity * (1 - discount)
```

Original amounts are in US dollars. The PDF report converts them to Indian rupees at an assumed rate of **Rs. 95 per USD** (approximate rate, October 2026).



## Join Validation

Row counts and totals were checked before and after joining to make sure no rows were lost or duplicated.

| Check | Expected | Result |
|-------|----------|--------|
| `order_details` rows | 2,155 | 2,155 |
| Distinct orders | 830 | 830 |
| Total revenue (USD) | 1,265,793.02 | 1,265,793.02 |
| Rows with missing product or customer | 0 | 0 |

**Double counting was avoided by:**
- Counting orders with `COUNT(DISTINCT orderID)`, never `COUNT(*)`
- Not summing `freight` (an order-level value) across order lines

## Results

| Metric | Value |
|--------|-------|
| Total revenue | $1,265,793 (about Rs. 12.03 crore) |
| Total orders | 830 |
| Customers who ordered | 89 |
| Average order value | $1,525 (about Rs. 1.45 lakh) |

## Key Insights

**1. USA and Germany drive the business.**
USA ($245,585) and Germany ($230,285) together bring in about **38%** of all revenue. Austria is third with only 40 orders, which means a very high value per order.

**2. Beverages and Dairy are the top categories.**
Beverages ($267,868) and Dairy Products ($234,507) make up about **40%** of revenue. Grains/Cereals and Produce are the weakest.

**3. One product is a major revenue source.**
Cote de Blaye earns $141,397 (**11.2%** of revenue) from just 24 orders because of its very high unit price.

**4. Margaret Peacock is the top employee.**
156 orders worth $232,891, the highest of all employees.

**5. Revenue grew strongly into 1998.**
Comparing January to April, revenue in 1998 is up **121%** over 1997. April 1998 was the best month overall. (May 1998 looks low only because the data ends on 6 May.)

## Recommendations

- Focus sales and marketing on the USA and Germany, and study why Austria has such high value per order.
- Protect the supply of Beverages and Dairy.
- Reduce dependence on a single high-priced product by promoting other top sellers.
- Share the practices of top employees with the rest of the team.
- Retain the largest customers to keep the 1998 momentum.

## Project Structure

```
.
├── data/                 # Northwind CSV files
├── notebook.ipynb        # Google Colab notebook with SQL queries
├── Northwind_Sales_Analysis_Report.pdf
└── README.md
```

## What I Learned

- How to join several tables safely and verify the result with row counts
- Why `COUNT(DISTINCT ...)` matters when a parent table has multiple child rows
- How order-level values (like freight) can be inflated after a join
- How to turn SQL output into clear business insights

- LinkedIn: [your-profile](https://www.linkedin.com/in/your-profile)
