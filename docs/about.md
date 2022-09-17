# About

### What is Dore?

Simply put, Dore is a fake data generation tool.

### Why is it called Dore?

No particular reason. I just wanted to share my thoughts on how we should have
spelt `door`.

### What can you do with it?

Dore allows you to define the details of your target data in a config file, known as the **Manifest**, and Dore
takes care of generating this data for you. <br>

With Dore, you can:
* Generate fake data for **multiple models across multiple protocols with complex schema dependencies with just a 
  single command**. <br>
  For example, you can set up your entire database with data for all tables with FK/PK integrity constraints in a single 
  command.
  
  
* Generate fake data with **dependencies/hierarchy between models regardless of the protocol**. <br> 
  For example, you can have a column in a MySQL table be dependent/have a FK relationship on a field in an 
  Elasticsearch index.
  

* Support for generating data for attributes that are **nested to arbitrary depth**. **Nested attributes can in turn be 
  dependent** or have their values derived from attributes of models in other protocols. <br>
  For example, you can have a MongoDB 
  collection which has a field that derives its value from a row of a PostgreSQL table or another MongoDB collection's 
  doc.