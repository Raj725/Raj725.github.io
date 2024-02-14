+++
title = "How To Clear Or Delete Neo4j Database?"
authors = ['Rajendra Kadam']
date = 2022-07-05T14:02:35+00:00
lastmod = 2024-02-13T22:28:17+05:30
draft = false
series = ['Neo4j Basics']
categories = ['Neo4j']
tags = ['Neo4j']
keywords =  ["Clear Neo4j", "Delete Neo4j Database"]
url = "/neo4j/clear-or-delete-neo4j-database/"
featuredImage = "/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.12.42-PM.png"
excerpt = "You will learn about the best ways to clear or delete Neo4j database as per specific needs. Neo4j DELETE and  REMOVE Clauses."
summary = "You will learn about the best ways to clear or delete Neo4j database as per specific needs. Neo4j DELETE and  REMOVE Clauses."
+++

I am sharing the best ways to clear or delete the Neo4j database as per your specific needs.

## Neo4j Remove Clause

The **REMOVE** clause is used to remove properties from nodes or relationships. It is also used to remove labels from the nodes.

#### Remove Node properties

There are 2 ways to remove the property from a node. You can either use a REMOVE clause or a SET clause. Using SET, You can set the property value as null and it will remove the property because Neo4j doesn’t allow storing null properties. Storing null is equivalent to removing it.

![](http://64.23.162.152/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM-1024x740.png)
Screenshot: Remove Node Properties

**1. Remove node property using REMOVE Clause**

```SQL
MATCH (p:Product)
REMOVE p.discount;
```

**2. Remove node property using SET clause**

```SQL
MATCH (p:Product)
SET p.name=null;
```

**3. Remove all node properties.** REMOVE clause can not be used to remove all the properties. Instead, SET can be used to set node = empty map, which will remove all the properties from node.

```SQL
MATCH (p:Product)
SET p={};
```

#### Remove Relationship properties

Removing properties from the relationship is identical to removing properties from the nodes. You just need to match the relationship and use the above syntax. For example:

```SQL
MATCH (n:Product)-[r:HAS_DISCOUNT]->(d:Discount)
REMOVE r.occasion
```

#### Remove a label from a node

```SQL
MATCH (n:Product)
REMOVE n:Product
```

## Neo4j Delete Clause

The `<strong>DELETE</strong>` is used to delete nodes, relationships, or paths.

#### Delete Relationships

We may need this query when you accidentally created incorrect relationships or you decided to change the data model.

```SQL
MATCH (:Product)-[c:HAS_CATEGORY]->(:Category)
DELETE c
```

#### Delete Nodes

Please note that we can not delete a node without deleting the connected relationships. We should either delete all the relationships first or delete them along with the node or use DETACH DELETE on a node that will detach node from connected node and delete it. **OPTIONAL MATCH** clause is used to make sure that nodes without relationships are also deleted, without **OPTIONAL MATCH** nodes having no relationships will not match the pattern and will not be deleted.

```SQL
MATCH (p:Product)
OPTIONAL MATCH (p)-[r:HAS_CATEGORY]->(:Category)
DELETE p, r
```

If there are no relationships to the node you can simply delete the node as follows:

```SQL
MATCH (p:Product)
DELETE p
```

### Completely Clear or Delete Neo4j data

```SQL
MATCH (n)
DETACH DELETE n
```

Above Cypher snippet works fine for small databases but for big databases, you need to delete the data in auto-commiting transactions which deletes data in multiple transactions and prevents the Neo4j throwing out of memory error. The following query does not work for older versions of the Neo4j(< version 4.4). If it doesn’t work for you, you can use APOC Library to delete the database using the periodic commit procedure.

```SQL
:auto MATCH (n)
CALL {
    WITH n
    DETACH DELETE n
} IN TRANSACTIONS OF 100000 ROWS
```

![](http://64.23.162.152/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.30.11-PM.png)
Delete Neo4j data with auto committing Transactions

##### References:

1. Neo4j [REMOVE](https://neo4j.com/docs/cypher-manual/current/clauses/remove/) documentation
2. Neo4j [DELETE](https://neo4j.com/docs/cypher-manual/current/clauses/delete/) documentation

<div class="wp-block-uagb-table-of-contents uagb-toc\_\_align-left uagb-toc\_\_columns-1 uagb-block-3f75a281 " data-scroll= "1" data-offset= "30" style="" >
