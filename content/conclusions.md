## Conclusions
{:#conclusions}

Through this work, we propose GraphQL-LD as a technique for combining the worlds of GraphQL and the Semantic Web.
We provide an implementation of this approach, and demonstrate this with a set of example queries.

In future work, we intend to formalize our algorithm for converting GraphQL queries to SPARQL algebra.
Furthermore, we intend to improve the way in which our _SPARQL results to tree_ module determines which variables
should be considered singular or plural.
OWL's InverseFunctionalProperty or JSON-LD framework are potential options that we consider for this.

In summary, this work allows developers who are able to work with GraphQL
to query the Linked Open Data cloud.
Furthermore, GraphQL can also be used an an alternative to SPARQL.
Even though it is less expressive than SPARQL, it can lead to simpler queries for certain cases.
