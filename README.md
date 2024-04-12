# data_warehouse

## Star Schema
It consists of a fact table surrounded by dimension tables. 
- Fact Table: This central table holds the primary data in the schema. It typically contains quantitative data (e.g., sales amount, quantity sold, etc.) and foreign keys to related dimension tables. Each record in the fact table represents a specific event or transaction, such as a sale, a call, or a visit.

- Dimension Tables: These tables contain descriptive attributes associated with the data in the fact table. Dimension tables provide context to the measures in the fact table. For example, in a sales scenario, dimension tables might include information such as product details (product name, category, etc.), customer details (customer ID, name, location, etc.), time (date, month, year, etc.), and geographical details (region, country, etc.).

"a dimensional model is actually a data warehouse applications programming interface (API)"
Kimball-style dimensional model allows us to skip the practice of up-front modeling, and instead opt to model as little as we need to


## Kimball dimensional data modeling
Ralph Kimball('https://en.wikipedia.org/wiki/Ralph_Kimball')’s dimensional data modeling defines three types of fact tables: 


1. Transaction fact tables
2. Periodic snapshot tables (Because modern MPP columnar data warehouses are so powerful, we don’t create periodic snapshot fact tables for reports that are not as regularly used. )
3. Accumulating snapshot tables (rare in practice)
4. Timespan fact table — but it’s only used for special circumstances
### Transaction fact tables
a customer or business process does some thing; you want to capture the occurrence of that thing, and so you record a transaction in your data warehouse and you’re good to go.  

This is best illustrated with a simple example. Let’s imagine that you’re running a convenience store, and you have an electronic point of sales (POS) system that records each sale that you make.  

you receive a transaction, you record the transaction in your fact table, and this becomes the basis of your reporting. In many ways, a transaction fact table is the default type of fact table that we’re used to thinking about.

### Periodic snapshot tables

A row in a periodic snapshot fact table captures some sort of periodic data — for instance, a daily snapshot of financial metrics, or perhaps a weekly summary of accounts receivable, or a monthly tally of inventory numbers.

The 'level of resolution’ is the period, not the individual transaction. Note that if no transactions occur during a certain period, a new row must be inserted into the periodic snapshot table, even if every fact that is saved is a null!  

Periodic snapshot tables tend to contain an incredibly large number of fields. This is because any reasonably interesting metric may be shoved into the period table. You can sort of imagine a scenario where you start out with aggregated sales, revenue, and cost of good sold on a weekly period, but as time goes by, management asks you to add other facts like inventory levels, account payable metrics, and other interesting measurements.

### Accumulating snapshot tables

order fulfillment pipeline diagram('https://www.holistics.io/blog/content/images/2020/05/business_value_pipeline_kimball.png')
order fulfillment accumulating fact('https://www.holistics.io/blog/content/images/2020/05/accumulating_fact_table_kimball.png')
- lag indicators
  Using a single table, management would be able to see if the lag times in its production are increasing or decreasing over time. They can use such business intelligence to determine which steps are the most problematic in their production process. And they can take action on the bits that are most worrying to them. (these ideas have been adapted to the software world under the terminology of ‘lean’)
  
