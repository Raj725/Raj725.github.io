+++
title = "Most Useful Neo4j String Functions"
authors = ['Rajendra Kadam']
date = 2022-07-02T16:52:29+00:00
lastmod = 2024-02-13T22:28:17+05:30
draft = false
series = ['Neo4j Basics']
categories = ['Neo4j']
tags = ['Neo4j', 'Neo4j String Functions']
url = "/neo4j/most-useful-neo4j-string-functions/"
featuredImage = "/wp-content/uploads/2022/07/Screenshot-2022-07-02-at-9.19.33-PM.png"
excerpt = 'In this post, we will see some of the most used Neo4j String functions, like converting string to numbers(integer/float), date, and list'
summary = 'In this post, we will see some of the most used Neo4j String functions, like converting string to numbers(integer/float), date, and list'
+++

While working with the data and databases oftentimes we have to deal with the Strings.  In this post, I will try to cover some of the most used Neo4j String functions.


## 1. Convert neo4j string to number

This happens to everyone. We load the data into the database and then realize that we didn’t mention the data type for the Integer or Float properties/fields.

Most of the time we delete the database, fix the data type in the data load queries, and re-upload the whole data. This method works well for small datasets, but what if you have an extensive dataset, it takes a lot of time to load the data, or it’s a Production database and you can’t delete it. Unlike other schema-based databases, we can convert the Neo4j property types on the fly.

We will consider a **Product** node type for example. Let’s assume there are only 3 properties: name, price, and quantity. The name is a String field, Price is a Float field and quantity is a number field, by mistake, we upload all the properties as strings.

Let’s create a product node with all the properties as String, and see how to convert price and quantity to numbers.


```SQL
CREATE (p:Product{name: "Notebook", price: "49.99", quantity: "4"})
```

### String to Integer

You can now use the **toInteger** function to convert the **quantity** property from String to Integer.


```SQL
MATCH (p:Product)
SET p.quantity = toInteger(p.quantity);
```

Execute the above Cypher query in the Neo4j and observe the output, it will show the number of properties set and the time it took to execute the query.

![](/wp-content/uploads/2022/07/Screenshot-2022-07-02-at-8.31.29-PM.png)
String to Integer in Neo4j

### Running the update query in batches

The above query updates all the nodes in a single transaction. You may get a low heap memory error if your database is huge. You can convert the above query into auto-committing transactions of smaller sizes. Following query run in transactions of 10000 rows.

```SQL
:auto MATCH (p:Product)
CALL {
    WITH p
    SET p.quantity = toInteger(p.quantity)
} IN TRANSACTIONS OF 10000 ROWS;
```

### String to Float

You can now use the **toFloat** function to convert the **price** property from String to Float.

```SQL
MATCH (p:Product)
SET p.price = toFloat(p.price);
```

## 2. Convert neo4j string to date

There’s limited support in Cypher for converting string to date. Cypher only supports yyyy-MM-dd format strings e.g. 2022-06-30. You can use the date() function to convert dates in **yyyy-MM-dd** format to the date type.

```SQL
MATCH (e:Event)
SET e.date = date(e.date);
```

#### **What if your date is not in the yyyy-MM-dd format?**

Let’s assume your date is in dd-MM-yyyy format e.g. 30-06-2022. You can split the string into a day, month, and year components and use **date()** function to create a date as shown in the following Cypher snippet.

```SQL
MATCH (e:Event)
WITH e, [date_component in split(e.date, "-") | toInteger(date_component)] AS date_components
SET e.date = date({day: date_components[0], month: date_components[1], year: date_components[2]})
```

Alternatively, you can use the simpler function from the APOC library apoc.date.parse. This function allows parsing almost all the formats of dates such as a long date format “30 June 2022”.

```SQL
MATCH (e:Event)
WITH e, apoc.date.parse(e.date, "ms", "dd MMMMM yyyy") AS ms
SET e.date = date(datetime({epochmillis: ms}))
```

## 3. Convert the neo4j string to a list

Let’s assume you have a Car node in the database, and you created the **“colors”** property as a string but it needs to be a list. You can contact the existing colors property and an **empty list ([])** to convert it to a list.

```SQL
MATCH (c:Car)
SET c.colors = c.colors + [];
```

If you have delimiter-separated values you can use the split() function to convert them to a list.

```SQL
RETURN split("black,white", ",") as colors
```

## 4. Convert other data types to neo4j string

You can use the **toString()** function to convert any other data type to String. This can be used for any data type like an integer, float, boolean, string, point, duration, date, time, localtime, localdatetime, or datetime value to a string.

## Conclusion

I hope this tutorial helped you in working with Neo4j strings. Please comment if you face any issues or need any help with anything related to Neo4j.

Please refer to [Neo4j documentation](https://neo4j.com/docs/cypher-manual/current/functions/string) for more String functions.
