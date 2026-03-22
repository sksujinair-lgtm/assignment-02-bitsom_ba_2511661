## Anomaly Analysis

### Insert Anomaly
In the dataset, a new product cannot be added unless an order exists because product details (product_id, product_name, category, unit_price) are stored along with order_id.

For example:
There is no way to insert a new product like (product_id = P999, product_name = "New Item") unless we create a row with an order_id.

Columns involved:
product_id, product_name, category, unit_price, order_id

---

### Update Anomaly
Customer details are repeated across multiple rows. Updating customer information in one row but not others leads to inconsistency.

For example:
customer_id = CUST1001 appears in multiple rows such as:
- Row with order_id = ORD1027
- Row with order_id = ORD1002

If customer_email is updated in one row but not the other, inconsistent data will exist.

Columns involved:
customer_id, customer_name, customer_email, customer_city

---

### Delete Anomaly
Deleting an order can result in loss of important customer or product data.

For example:
If the row with order_id = ORD1027 is deleted and that is the only record for that customer or product, then:
- Customer details (customer_id, customer_name, etc.)
- Product details (product_id, product_name)

will also be lost.

Columns involved:
order_id, customer_id, product_id
