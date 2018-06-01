## Architecture
{:#architecture}

Our approach has been implemented as two standalone modules:

* **GraphQL to SPARQL algebra**: Parses a GraphQL query to SPARQL algebra.
* **SPARQL results to tree**: Converts SPARQL query results to a tree structure.

These modules will be explained in more detail hereafter.
We plugged these modules into the [Comunica](cite:cites comunica) framework
as modules for parsing queries and serializing results.

[](#fig-architecture) shows an overview of our approach,
where GraphQL queries and JSON-LD contexts are passed to our _GraphQL to SPARQL algebra_ module,
the resulting SPARQL algebra is queried with Comunica,
and the results are shaped with the _SPARQL results to tree_ module.

<figure id="fig-architecture">
<img src="img/architecture.svg" alt="[GraphQl-LD Architecture]">
<figcaption markdown="block">
Flow of GraphQL queries and JSON-LD contexts to SPARQL algebra, to SPARQL results, and to a tree shape.
</figcaption>
</figure>

Just like Comunica, our modules are implemented in JavaScript,
and are compatible with the API specification
by the [RDFJS W3C community group](https://www.w3.org/community/rdfjs/){:.mandatory}.
This enables interaction between different JavaScript applications that supports this API.

### GraphQL to SPARQL algebra

The _GraphQL to SPARQL algebra_ module is responsible for parsing a GraphQL query to SPARQL algebra,
based on a JSON-LD context.
The conversion algorithm is based on translating GraphQL's tree-based structures to links of triple patterns in SPARQL.

Triple patterns are however not sufficient to express all of GraphQL's features.
For instance, GraphQL allows queries to contain reusable [fragments](http://facebook.github.io/graphql/October2016/#sec-Validation.Fragments){:.mandantory}.
These fragments are reusable query blocks, which must be applied on a certain type.
If this type does not match, then the fragment will be ignored.
We consider fragments to use the left-join semantics, which translates to the `OPTIONAL` keyword in SPARQL.
Furthermore, GraphQL queries also allow pagination with the `first` and `offset`,
which we translate to SPARQL `OFFSET` and `LIMIT`.

This module is available under the open MIT license on [GitHub](https://github.com/rubensworks/graphql-to-sparql.js){:.mandatory},
where more information on the conversion process can be found.

### SPARQL results to tree

The _SPARQL results to tree_ module can convert SPARQL query results to a tree-based structure.
This is done by splitting combining variables prefix-based,
and aggregating results in a tree structure.
In order to determine whether a certain variable binding should be seen as an array or a single value,
we reguire a mapping to be passed inside the context that defines which variables are singular.
If variables are not defined in this mapping, they are considered plural by default.

This module is also available under the open MIT license on [GitHub](https://github.com/rubensworks/sparqljson-to-tree.js){:.mandatory}.