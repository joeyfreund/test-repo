---
---

xnlogic is a powerful web framework for applications that are backed by a graph database. 

![XN Stack](https://dl.dropboxusercontent.com/s/sew1hvjfeclxhrv/XN_stack.png)
      

## Features

 * Written in [JRuby](http://jruby.org/).
 * Works with any [Blueprints](https://github.com/tinkerpop/blueprints/wiki) graph database, such as Neo4j, OrientDB, TinkerGraph, and many more.
 * Uses [Pacer](https://github.com/pangloss/pacer), a super-fast graph traversal and stream processing library.
 * [Rich Data Modeling](#data-modeling)
 * [REST API](#rest-api)
 * [User & permission management](#user--permission-management)
 * [History graph](#history-graph)
 * [Enterprise Integrations](#enterprise-integrations)
     
----

## Data Modeling

xnlogic has a simple, yet powerful, data model.
 * Parts are modules, containing extended functionality, that be attached (i.e. mixed-in) to graph elements.
 * Models are defined as lists of parts. 
 * Vertices in the graph correspond to model objects.
 * Relations (i.e. edges) are defined at the part level (i.e. from one part to another part).

This allows you to model your data in a flexible and modular way, without being limited to the traditional hierarchical class structure.

To get an idea of how we model data with xnlogic, consider the following simple domain, with two models, `iPhone` and `AppleWatch`.


| Model        | Parts     |
| ------------ | --------- |
| `iPhone`     | `TouchScreen`, `Antenna` |
| `AppleWatch` | `TouchScreen`, `Band`    |

An `iPhone` is made up of `TouchScreen` and `Antenna` parts, while an `AppleWatch` 
is made up of `TouchScreen` and `Band`.

For a more detailed example, see [[Structuring-an-application]].


## REST API

xnlogic creates a REST API that gives you full access to its graph querying and data modeling power.

From basic searches across your data
```
# Get all iphones
GET /model/iphone
# Get all touch enabled devices
GET /is/touchscreen
# Get all touch enabled devices that are also Bluetooth enabled
GET /is/touchscreen,bluetooth
```
To easily running complex queries
```
GET /model/user/first/to/recommended_products
```

For more details, see the [REST API docs](REST-API).


## User & Permission Management

xnlogic comes with [[User And Permission Management]] already baked in.
 * Allows you to define groups and users.
 * Gives you granular control over access permissions - Different permissions are granted to users/groups, by part.
 * Built using xnlogic models and parts, which means that it is easily extensible.
 * Tested and used in production environments.

## History Graph

xnlogic allows you to get a snapshot of your data at any point in time. 
And it does it efficiently!

## Enterprise Integrations

xnlogic is designed to play nicely with other systems.
 * Integration with an external authentication system (such as Microsoft Exchange Server or any OAuth server) is built in.
 * Data model include integration points with external data stores.
