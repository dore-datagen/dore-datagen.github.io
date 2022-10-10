# The E-Commerce Schema

Let's say we want to generate fake data in a MySQL database named `Dore_Ecommerce` for the following schema:

<figure markdown>
  ![Image title](../assets/ecommerce-schema.svg)
  <figcaption>Ecommerce schema</figcaption>
</figure>



The schema contains two tables:

* **Customer**

    Contains details of customers of the ecommerce. 
    
    Each customer is uniquely identified by a `customer_id` and has a name which is stored in the `customer_name` 
    column.

2. **Order**

    Contains details of orders placed with the ecommerce. 

    Each order is uniquely identified by an `order_id` and is placed on a certain date which is stored in the 
    `order_date` column. Since orders are placed *by* customers, each order is associated with a `customer_id` 
    which identifies one of the customers in the Customer table.

Note that the schema mentions a *Foreign Key* relationship between **Order.customer_id** and 
**Customer.customer_id**. Generating fake data for schemas with dependencies between columns in a database agnostic 
way is one of the core problems that Dore was designed to solve.

<hr>

[ ➡ Next: Dore Manifest](/tutorial/dore_manifest/){.md-button}

<hr>
