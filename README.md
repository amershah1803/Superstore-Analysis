# Superstore-Analysis


# Superstore Data Analysis

## 📊 Project Overview

This project analyzes the **Superstore dataset** to understand sales performance, profitability, customer behavior, product performance, regional trends, shipping, discounts, and potential sources of profit loss.

The analysis combines **Python, Pandas, SQLite, SQL, Power BI and Matplotlib** to move from data cleaning and exploratory analysis to deeper investigation of business anomalies.

A key focus of the project was not only identifying where sales were high, but understanding **where high sales were not translating into high profit — and why**.

---

## 🎯 Objectives

* Analyze overall sales and profitability
* Identify high-performing and underperforming categories and sub-categories
* Compare sales and profit across regions, states, and cities
* Analyze customer and product-level performance
* Investigate the relationship between discounts and profitability
* Analyze shipping time and shipping modes
* Identify seasonal sales and profit trends
* Detect anomalies where sales performance and profit performance differ significantly
* Drill down into specific states, products, customers, and sub-categories to understand the reasons behind losses

---

## 🛠️ Tools & Technologies

* **Python**
* **Pandas** – Data cleaning, transformation, aggregation, and analysis
* **SQLite** – Data storage and SQL-based analysis
* **SQL** – KPI calculations, grouping, ranking, filtering, and business analysis
* **Matplotlib** – Data visualization
* **Power BI** – Interactive dashboard and business visualization
* **Jupyter Notebook / Google Colab**

---
## 📊 Power BI Dashboard

An interactive Power BI dashboard was created to visualize the key findings from the Superstore analysis.

**Dashboard includes:**
- Sales & Profit KPIs
- Category & Sub-Category Performance
- Regional & State-Level Analysis
- Customer Profitability
- Product Performance
- Discount vs Profitability
- Monthly Sales & Profit Trends

---
## 📁 Dataset

The analysis uses the **Sample Superstore dataset**, containing transactional information including:

* Order and shipping dates
* Customer information
* Segment
* Geographic information
* Product and category information
* Sales
* Quantity
* Discount
* Profit

The dataset contains **9,994 transaction records**.

---

## 🧹 Data Preparation

Before performing the analysis, the dataset was cleaned and transformed using Pandas.

Key preprocessing steps included:

* Removed leading and trailing spaces from text columns
* Converted `Order Date` and `Ship Date` into datetime format
* Rounded Sales and Profit values
* Converted Discount values into percentage representation
* Created a `Ship Days` column using the difference between Ship Date and Order Date
* Loaded the cleaned dataset into a **SQLite database** for SQL analysis

The cleaned dataset was also exported as:

`superstorecleaned_data.csv`

---

## 📌 Key Performance Indicators

| KPI                 |          Value |
| ------------------- | -------------: |
| Total Sales         | **$2,297,340** |
| Total Profit        |   **$286,340** |
| Total Orders        |      **5,009** |
| Total Customers     |        **793** |
| Total Products      |      **1,862** |
| Average Order Value |    **$229.87** |

The overall profit margin based on total sales is approximately **12.46%**.

---

# 🔍 Analysis & Insights

## 1. Category Performance

Technology generated the highest sales and profit among the three major categories.

| Category        |    Sales |   Profit |
| --------------- | -------: | -------: |
| Technology      | $836,219 | $145,423 |
| Furniture       | $742,003 |  $18,444 |
| Office Supplies | $719,118 | $122,473 |

### Key Finding

**Furniture is the major profitability concern.** Although Furniture generated more than **$742K in sales**, it produced only about **$18.4K in profit**, a margin of approximately **2.49%**.

This large sales-to-profit gap led to a deeper investigation of discounts, sub-categories, products, and states.

---

## 2. Sub-Category Analysis

### Highest-profit sub-categories

* **Copiers:** $55,618 profit
* **Phones:** $44,490 profit
* **Accessories:** $41,928 profit
* **Paper:** $34,053 profit
* **Binders:** $30,200 profit overall

### Loss-making sub-categories

* **Tables:** -$17,733 profit
* **Bookcases:** -$3,479 profit
* **Supplies:** -$1,187 profit

Tables were a major concern, generating approximately **$207K in sales while producing a $17.7K loss**.

---

## 3. Regional Performance

### Sales by Region

| Region  |    Sales |
| ------- | -------: |
| West    | $725,511 |
| East    | $678,828 |
| Central | $501,253 |
| South   | $391,748 |

### Profit by Region

| Region  |   Profit |
| ------- | -------: |
| West    | $108,383 |
| East    |  $91,518 |
| South   |  $46,721 |
| Central |  $39,718 |

The **West** is the strongest region in both sales and profit.

---

## 4. State-Level Analysis

California and New York are the strongest states by both sales and profit. However, several high-sales states show significant profitability problems.

### Highest Sales

* California — **$457,728**
* New York — **$310,911**
* Texas — **$170,187**
* Washington — **$138,656**

### Major Profitability Anomalies

| State            |    Sales |       Profit | Sales Rank | Profit Rank |
| ---------------- | -------: | -----------: | ---------: | ----------: |
| **Texas**        | $170,187 | **-$25,715** |          3 |          49 |
| **Pennsylvania** | $116,522 | **-$15,550** |          5 |          47 |
| **Ohio**         |  $78,253 | **-$16,963** |          8 |          48 |
| **Illinois**     |  $80,162 | **-$12,607** |          7 |          46 |

These states were selected for deeper analysis because their sales rankings were much stronger than their profit rankings.

---

## 5. Sales vs Profit Anomaly Detection

A custom Python function was developed to compare the ranking of entities based on **Sales vs Profit**.

The function:

1. Groups the dataset by a selected dimension
2. Calculates total Sales
3. Calculates total Profit
4. Assigns rankings to both
5. Calculates the absolute difference between Sales Rank and Profit Rank
6. Sorts the results by the largest ranking difference

This approach was applied to:

* Ship Mode
* Sub-Category
* Category
* Customers
* Cities
* States
* Regions

This helped identify areas where **strong sales performance was not necessarily associated with strong profitability**.

---

## 6. Discount vs Profitability

One of the strongest patterns identified in the analysis was the relationship between discount levels and profit.

| Discount | Avg. Sales |  Avg. Profit |
| -------: | ---------: | -----------: |
|       0% |    $226.76 |       $66.89 |
|      10% |    $578.46 |       $96.01 |
|      15% |    $530.00 |       $27.23 |
|      20% |    $209.09 |       $24.70 |
|      30% |    $454.67 |  **-$45.65** |
|      32% |    $536.70 |  **-$88.52** |
|      40% |    $565.18 | **-$111.90** |
|      45% |    $498.64 | **-$226.64** |
|      50% |    $892.61 | **-$310.73** |
|      60% |     $48.18 |  **-$43.07** |
|      70% |     $97.19 |  **-$95.91** |
|      80% |     $56.54 | **-$101.82** |

### Key Finding

Higher discounts can increase sales value while simultaneously pushing profitability into negative territory. This pattern became particularly important when investigating Furniture, Tables, Machines, and the underperforming states.

---

# 🔎 Key Insights & Answers

## 7. Why is Furniture generating high sales but very low profit?

Furniture generated **$742,003 in sales** but only **$18,444 in profit**, resulting in a profit margin of approximately **2.49%**.

Furniture also had the highest average discount among the three major categories:

| Category        | Avg. Discount | Profit Margin |
| --------------- | ------------: | ------------: |
| Technology      |        13.23% |        17.39% |
| Office Supplies |        15.73% |        17.03% |
| Furniture       |    **17.39%** |     **2.49%** |

When Furniture was analyzed by discount level, average profitability fell sharply at higher discounts.

### Answer

**Furniture's low profitability is strongly associated with aggressive discounting.** The problem becomes particularly severe at discounts of 30% and above.

---

## 8. Why are Tables losing money?

| Sub-Category |        Sales |       Profit |     Margin |
| ------------ | -----------: | -----------: | ---------: |
| Chairs       |     $328,453 |      $26,586 |      8.09% |
| Furnishings  |      $91,704 |      $13,070 |     14.25% |
| Bookcases    |     $114,879 |      -$3,479 |     -3.03% |
| **Tables**   | **$206,967** | **-$17,733** | **-8.57%** |

The analysis found that Table transactions can be profitable at low/no discount but become loss-making at higher discounts.

For example, in the Central region:

| Discount |   Sales |      Profit |
| -------: | ------: | ----------: |
|       0% | $16,845 |  **$2,965** |
|      30% | $15,758 | **-$2,215** |
|      50% |  $6,549 | **-$4,311** |

In the East, Tables generated **$29,720 in sales at a 40% discount but lost $9,838**.

Several individual Table products also produced significant losses, including:

* **Chromcraft Bull-Nose Wood Oval Conference Tables & Bases** — **-$2,876**
* **Bush Advantage Collection Racetrack Conference Table** — **-$1,933**
* **Balt Solid Wood Round Tables** — **-$1,202**
* **BoxOffice By Design Rectangular and Half-Moon Meeting Room Tables** — **-$1,149**
* **Riverside Furniture Oval Coffee Table** — **-$1,148**

### Answer

**Tables are not losing money because of weak sales. High discounts are eroding the profit generated by those sales, with several individual products contributing substantial losses.**

---

## 9. Why are Machines generating sales but very little profit?

Machines generated approximately:

* **$189,242 Sales**
* **$3,387 Profit**
* **1.79% Profit Margin**

The average Machine discount was approximately **30.61%**.

The regional analysis showed that Machines could be profitable at lower discounts but became heavily loss-making at high discounts. For example, in the East, Machine sales at **0% discount generated $20,918 profit**, while sales at **70% discount generated -$13,989 profit**.

### Answer

**Machines are another strong example of the sales-to-profit problem. Higher discounts are associated with a sharp deterioration in profitability, turning otherwise profitable Machine sales into losses.**

---

## 10. Why is Texas generating high sales but negative profit?

Texas generated:

* **$170,187 Sales**
* **-$25,715 Profit**

Texas ranked **3rd in sales but 49th in profit**, creating a **46-position sales-to-profit ranking difference**.

The state was then drilled down from **State → Category → Sub-Category → Product → Discount → Profit**.

### Main loss-making sub-categories in Texas

| Sub-Category   |   Sales |       Profit | Avg. Discount |
| -------------- | ------: | -----------: | ------------: |
| **Binders**    |  $9,042 | **-$14,705** |           80% |
| **Appliances** |  $2,408 |  **-$6,150** |           80% |
| Furnishings    |  $3,769 |      -$3,312 |           60% |
| Machines       | $19,548 |      -$2,666 |           40% |
| Chairs         | $26,568 |      -$2,513 |           30% |
| Bookcases      | $14,491 |      -$2,390 |           32% |
| Tables         | $15,758 |      -$2,215 |           30% |

### Answer

The biggest contributors to Texas's loss were **Binders and Appliances**, followed by Furnishings, Machines, Chairs, Bookcases, and Tables.

The strongest warning signs were the **80% average discounts for Binders and Appliances**, which corresponded with substantial negative profits.

Texas therefore demonstrates how high sales can hide serious product-level profitability problems.

---

## 11. Why is Pennsylvania generating negative profit?

Pennsylvania generated **$116,522 in sales** but **-$15,550 in profit**.

### Main loss-making sub-categories

| Sub-Category |   Sales |      Profit | Avg. Discount |
| ------------ | ------: | ----------: | ------------: |
| **Binders**  |  $6,269 | **-$4,576** |           70% |
| **Phones**   | $19,707 | **-$3,606** |           40% |
| Bookcases    |  $5,229 |     -$2,896 |           50% |
| Tables       |  $8,052 |     -$2,588 |           40% |
| Machines     |  $2,134 |     -$2,219 |           70% |
| Chairs       | $18,722 |     -$1,991 |           30% |
| Supplies     |  $6,710 |     -$1,459 |           20% |
| Storage      | $11,786 |     -$1,434 |           20% |

### Answer

Pennsylvania's losses are spread across several sub-categories. **Binders are the largest contributor to the loss**, followed by Phones, Bookcases, Tables, Machines, and Chairs.

High discounts are again visible in the worst-performing areas, especially **Binders at 70% and Machines at 70%**.

---

## 12. Why is Ohio generating negative profit?

Ohio generated **$78,253 in sales** but **-$16,963 in profit**.

### Main loss-making sub-categories

| Sub-Category |   Sales |       Profit | Avg. Discount |
| ------------ | ------: | -----------: | ------------: |
| **Machines** |  $8,978 | **-$11,770** |           70% |
| Phones       | $14,634 |      -$2,778 |           40% |
| Tables       |  $7,888 |      -$2,715 |           40% |
| Binders      |  $1,917 |      -$1,401 |           70% |
| Bookcases    |  $2,076 |      -$1,360 |           50% |
| Chairs       | $10,143 |        -$649 |           30% |
| Storage      |  $7,266 |        -$275 |           20% |

### Answer

**Machines are the dominant reason for Ohio's poor profitability**, contributing **-$11,770**, which accounts for a large portion of the state's total loss.

Phones, Tables, Binders, and Bookcases also contributed losses, with high discounts appearing repeatedly among the worst-performing sub-categories.

---

## 13. What about Illinois?

Illinois generated **$80,162 in sales** but **-$12,607 in profit**.

The largest losses came from:

| Sub-Category |   Sales |      Profit | Avg. Discount |
| ------------ | ------: | ----------: | ------------: |
| **Binders**  |  $4,540 | **-$7,207** |           80% |
| Tables       |  $6,549 |     -$4,311 |           50% |
| Furnishings  |  $2,880 |     -$2,632 |           60% |
| Appliances   |    $973 |     -$2,484 |           80% |
| Chairs       | $14,560 |     -$1,578 |           30% |

### Answer

**Binders are the largest source of Illinois's loss**, followed by Tables, Furnishings, and Appliances. The highest-loss areas also carry some of the highest discount levels.

---

## 14. Which customers generate high sales but poor profit?

The customer-level Sales vs Profit ranking revealed large mismatches between revenue and profitability.

| Customer             | Sales Rank | Profit Rank | Rank Difference |
| -------------------- | ---------: | ----------: | --------------: |
| **Sean Miller**      |          1 |         604 |         **603** |
| **Becky Martin**     |         13 |         601 |         **588** |
| **Grant Thornton**   |         22 |         610 |         **588** |
| **Natalie Fritzler** |         32 |         602 |         **570** |
| **Sean Braxton**     |         37 |         605 |         **568** |
| **Peter Fuller**     |         25 |         582 |         **557** |
| **Zuschuss Carroll** |         38 |         595 |         **557** |
| **Joseph Holt**      |         39 |         583 |         **544** |
| **Joseph Airdo**     |         63 |         590 |         **527** |
| **Cindy Stewart**    |         87 |         611 |         **524** |

### Answer

These customers show that **high customer revenue does not necessarily mean high customer value**.

For example, **Sean Miller ranked #1 in sales but only #604 in profit**.

---

## 15. What is causing losses for these high-sales customers?

When the 10 customers with the largest Sales-vs-Profit ranking differences were analyzed by sub-category:

| Sub-Category |       Sales |       Profit | Profit Margin |
| ------------ | ----------: | -----------: | ------------: |
| Accessories  |      $5,418 |       $1,608 |        29.68% |
| Chairs       |      $5,914 |         $463 |         7.83% |
| Paper        |        $995 |         $392 |        39.40% |
| Phones       |      $2,176 |         $162 |         7.44% |
| Bookcases    |      $6,233 |         $134 |         2.15% |
| Storage      |      $2,738 |        -$218 |        -7.96% |
| Supplies     |      $4,736 |      -$1,040 |       -21.96% |
| Appliances   |      $2,134 |      -$1,296 |       -60.73% |
| Binders      |      $4,179 |      -$1,485 |       -35.53% |
| Tables       |      $9,858 |      -$1,966 |       -19.94% |
| **Machines** | **$52,978** | **-$18,356** |   **-34.65%** |

### Answer

**Machines were by far the largest source of losses among these high-sales customers.** They generated nearly **$53K in sales but produced an $18.4K loss**.

Tables, Binders, Appliances, and Supplies also contributed to the losses.

This suggests that the issue is not necessarily the customers themselves — **their product mix and the discounts applied to those products are major contributors to negative profitability**.

---

## 16. Example: Sean Miller

Sean Miller ranked **#1 in total sales** but only **604th in profit**.

The transaction-level investigation shows that highly discounted Machine purchases contributed heavily to the profitability problem.

### Answer

**Sean Miller is a high-revenue but low-profit customer.** This demonstrates why a customer should not be classified as valuable based on sales alone.

---

## 17. Seasonal Sales Analysis

Monthly sales were analyzed across the dataset, with strong sales periods around:

* March
* August
* September
* November
* December

These trends can help align promotional and inventory strategies with seasonal demand.

---

## 18. Shipping Analysis

Shipping performance was analyzed using the calculated `Ship Days` metric.

| Ship Mode      | Average Ship Days |
| -------------- | ----------------: |
| First Class    |              2.18 |
| Same Day       |              0.04 |
| Second Class   |              3.24 |
| Standard Class |              5.01 |

Regional shipping times were also compared to identify geographic differences in delivery performance.

---

# 💡 Business Recommendations

### 1. Control high discounts

Review discounts of **30%+** carefully, especially for Tables, Machines, Bookcases, Binders, and Appliances.

### 2. Review loss-making sub-categories by state

The state analysis shows that the problematic sub-category differs by market:

| State            | Major Loss Driver(s)                         |
| ---------------- | -------------------------------------------- |
| **Texas**        | Binders, Appliances, Furnishings, Machines   |
| **Pennsylvania** | Binders, Phones, Bookcases, Tables, Machines |
| **Ohio**         | Machines, Phones, Tables, Binders            |
| **Illinois**     | Binders, Tables, Furnishings, Appliances     |

This supports a **state-specific profitability strategy** rather than a single national discount policy.

### 3. Evaluate customers using profit, not only sales

High-revenue customers should be evaluated using:

**Sales + Profit + Discount + Product Mix**

### 4. Review loss-making products

Create a product-level profitability report and flag products that repeatedly generate negative profit.

### 5. Focus on profitable growth

Technology is the strongest major category in both sales and profit. Growth strategies should consider sustainable margins rather than sales volume alone.

### 6. Use targeted promotions

Instead of broad discounts, promotions should be targeted to products and customers where the expected margin can support the discount.

---

# 📈 Visualizations

The notebook includes visual analysis of:

* Monthly sales trends
* Monthly profit trends
* Sales by category
* Sales and profit by sub-category
* Sales and profit by state
* Sales and profit by region
* Sales distribution
* Profit distribution
* Sales box plot
* Profit box plot
* Shipping-days distribution
* Discount vs profit relationships
* Category-level monthly trends
* Furniture-specific trends

---

# 🔬 Analytical Approach

The project follows a structured analytics workflow:

```text
Raw Superstore Data
        ↓
Data Cleaning & Transformation
        ↓
Exploratory Data Analysis
        ↓
SQLite Database Creation
        ↓
SQL-Based KPI Analysis
        ↓
Category / Region / State Analysis
        ↓
Customer & Product Analysis
        ↓
Sales vs Profit Rank Comparison
        ↓
Anomaly Detection
        ↓
Discount & Profitability Investigation
        ↓
State / Product-Level Drill Down
        ↓
Business Insights & Recommendations
```

---

# 📂 Project Structure

```text
Superstore-Data-Analysis/
│
├── 10k_dataset.ipynb
├── superstorecleaned_data.csv
├── README.md
└── Sample - Superstore.csv
```

---

# 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-link>
cd Superstore-Data-Analysis
```

### 2. Install dependencies

```bash
pip install pandas matplotlib
```

### 3. Open the notebook

```bash
jupyter notebook 10k_dataset.ipynb
```

or open the notebook using **Google Colab**.

### 4. Run the notebook

Make sure the Superstore CSV file is available at the path expected by the notebook before running the analysis.

---

# 📌 Conclusion

This project demonstrates how combining **Python, Pandas, SQL, SQLite, and data visualization** can turn transactional data into actionable business insights.

Rather than focusing only on revenue, the analysis investigates the relationship between **sales, profit, discounts, customers, products, geography, and shipping** to identify where revenue growth is masking profitability problems.

The strongest recurring pattern is:

**High Discount → Lower Profitability → Potential Loss**

This pattern is particularly visible in **Furniture, Tables, Machines, Binders, and several state-level problem areas**.

The project ultimately demonstrates a core principle of business analytics:

> **High sales do not always mean high profitability.**
