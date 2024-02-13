+++
title = "What is Cypher Query Language?"
draft = false
author = "Rajendra Kadam"
date = 2022-03-30T18:15:42+00:00
lastmod = 2024-02-13T22:28:17+05:30
featuredImage = "/wp-content/uploads/2022/03/what-is-cypher-query-language.jpg"
authors = ['Rajendra Kadam']
tags = ['Neo4j','Cypher', 'Cypher Query Language']
categories = ['Neo4j']
series = ['Neo4j Basics']
excerpt = 'Cypher Query Language is Neo4j’s graph query language. It allows users to perform various CRUD operations(create, read, update, and delete) on the graph databases.'
summary = "Cypher Query Language is Neo4j’s graph query language. It allows users to perform various CRUD operations(create, read, update, and delete) on the graph databases."
+++

## What is Cypher Query Language?

**Cypher Query Language** is a declarative query language for interacting with graph databases, developed by Neo4j. It is used to create, modify, and query graph data stored in a Neo4j database.


Cypher uses a simple, human-readable syntax that allows developers to express complex queries in a concise manner. It also provides a set of built-in functions and operators that can be used to manipulate and transform data.

Cypher is designed to be expressive and flexible, making it a powerful tool for working with graph data. It is widely used in a variety of applications, including social networking, recommendation engines, fraud detection, and more.

The good thing about Cypher query language is that it’s very easy to learn and master. It’s very expressive and declarative.

Cypher’s syntax provides an easy way to find patterns of nodes and relationships in the graph.

Here is an example of a Cypher query that retrieves all nodes in a graph:

```Cypher
MATCH (n)
RETURN n
```

In Cypher, a graph is made up of nodes and relationships. Nodes represent entities or objects in the graph, and relationships connect nodes and represent the relationships between them.

Cypher uses the MATCH clause to specify patterns in the graph that we want to retrieve or modify. For example, the following query retrieves all nodes with the label “Person” that have a relationship with a node with the label “Movie“:

```Cypher
MATCH (p:Person)-[r]->(m:Movie)
RETURN p, r, m
```

The RETURN clause specifies which nodes and relationships we want to return as part of the query results.

Cypher also provides a variety of built-in functions and operators that can be used to manipulate and transform data. For example, the following query uses the TO_UPPER function to return the names of all nodes with the label “Person” in uppercase:

```Cypher
MATCH (p:Person)
RETURN TO_UPPER(p.name)
```

Cypher also supports creating and deleting nodes and relationships, as well as modifying the properties of nodes and relationships. For example, the following query creates a new node with the label “Person” and the property “name” set to “Alice”:

```Cypher
CREATE (p:Person {name: 'Alice'})
RETURN p
```
Overall, Cypher is a powerful and flexible query language that makes it easy to work with graph data stored in a Neo4j database.

It’s worth noting that Cypher is not the only query language for interacting with graph databases. Some other popular graph query languages include Gremlin and SPARQL.

## Usage of Cypher

Cypher is the primary query language for interacting with Neo4j, a popular graph database management system. Neo4j is a native graph database, meaning that it is specifically designed to store and query graph data. It is widely used in a variety of applications, including social networking, recommendation engines, fraud detection, and more.

Cypher is not limited to the Neo4j database. In addition to Neo4j, some other databases also support Cypher as a query language.

Cypher is an open-source project. You can find out more about the open Cypher projects on the [Open Cypher Website](http://opencypher.org/).

Many projects use the [Cypher query language](https://www.opencypher.org/projects/), some of those are:

* AgensGraph
* AnzoGraph
* Memgraph
* RedisGraph
* SAP HANA Graph

These are just a few examples of databases that support Cypher. There are many others as well, and the list is constantly growing as more and more organizations adopt graph databases and Cypher for a variety of applications.


## **What are some Common clauses and expressions used in Cypher**?

Cypher queries are composed of clauses and expressions, which are used to specify patterns in the graph, transform and manipulate data, and return results. Here are some examples of common clauses and expressions used in Cypher:

* MATCH: Specifies patterns in the graph that we want to retrieve or modify.
* WHERE: Filters the results of a query based on certain conditions.
* RETURN: Specifies which nodes and relationships we want to return as part of the query results.
* CREATE: Creates new nodes and relationships in the graph.
* DELETE: Deletes nodes and relationships from the graph.
* SET: Modifies the properties of nodes and relationships.

Cypher also provides a wide range of built-in functions and operators that can be used to manipulate and transform data. For example, we can use the **`TO_UPPER`** function to convert strings to uppercase, or the **`AVG`** function to calculate the average of a set of numbers.


## **How to Learn Cypher Query Language?**

The best way to learn anything is to start using it.

I would suggest you install any of the above graph databases. I prefer Neo4j because it’s very easy to start with. Neo4j also provides ready-to-use Neo4j sandboxes. There are plenty of resources like the[ Neo4j Blog](https://neo4j.com/developer/cypher/), Youtube channels, and online courses to learn Neo4j.

I hope you got the idea about Cypher Query Language. This is an introductory post I will add more Cypher-related posts here.

Your feedback and suggestions for the future are much appreciated.

## Posts related to Cypher:
