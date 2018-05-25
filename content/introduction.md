## Introduction
{:#introduction}

The [SPARQL query language](spec:sparqllang) is a W3C recommendation for querying RDF data.
While this language has gained a lot of attention in the research domain,
its widespread usage within commercial applications remains limited.
One of the reasons for this is many developers
are not experienced in the handling of (RDF) triples.
Instead, they are better equiped to handle nested objects.
Furthermore, more libraries and frameworks exist for the latter.

In order to bridge this gap between RDF and developers, several works have been proposed
to simplify the definition of queries and the shaping of results.
[_sparql-to-jsonld_](cite:cites sparqltojsonld) is a tool that converts the output
of SPARQL queries to [JSON-LD](cite:cites jsonld) documents,
where JSON-LD is an RDF serialization that uses the developer-friendly JSON format.
This tool still requires the SPARQL syntax to be used for defining queries.
Recently, an approach was introduced that also builds upon the concepts of JSON-LD
to define SPARQL queries in JSON-LD, after which the [SPARQL query results are shaped to the desired JSON shape](cite:cites transformingjsonsparql).
While this last approach tackles both the problem of query definition and result shaping,
it still requires developers to have basic knowledge about triple patterns
and the domain-specific language that is introduced by the approach.

GraphQL has however proven to be a popular query language among developers.
In 2015, the [GraphQL framework](cite:cites graphql) was introduced by Facebook
as an alternative way of querying data through interfaces.
It is often being positioned as an alternative to [RESTful interfaces](cite:cites rest),
as it is able to replace multiple REST calls with a single tree-like query.
Since then, GraphQL has been gaining increasing attention among developers,
partly due to its simplicity in usage, and its large collection of supporting tools.
One major disadvantage of GraphQL compared to SPARQL is the fact that it has no notion of semantics,
i.e., it requires an interface-specific schema.
This therefore makes it difficult to combine GraphQL data that originates from different sources,
which is further complicated by the fact that GraphQL has no notion of global identifiers,
which _is_ possible in RDF through the use of URIs.
Furthermore, GraphQL is however not as expressive as SPARQL,
as [GraphQL queries represent trees](cite:cites graphqlsemantics),
and not full graphs as in SPARQL.

In this work, we introduce _GraphQL-LD_, an approach for extending GraphQL queries with a JSON-LD context,
so that they can be used to evaluate queries over RDF data.
This results in a query language that is less expressive than SPARQL,
but can still achieve many of the typical data retrieval tasks in applications.
Our approach consists of an algorithm that translates GraphQL-LD queries to [SPARQL algebra](cite:cites spec:sparqllang).
This allows such queries to be used as an alternative input to SPARQL engines,
and thereby opens up the world of RDF data to the large amount of people that already know GraphQL.
Furthermore, results can be translated into the GraphQL-prescribed shapes.
The only additional requirement is their queries would now also need a JSON-LD context,
which could be provided by external domain experts.

In related work, [HyperGraphQL](cite:cites hypergraphql) was introduced as a way to expose access to RDF sources
through GraphQL queries and emit results as JSON-LD.
The difference with our approach is that HyperGraphQL requires a service to be set up
that acts as a intermediary between the GraphQL client and the RDF sources.
Instead, our approach enables agents to directly query RDF sources by translating GraphQL queries client-side.

In the next section, we summarize the architecture of our approach and the SPARQL algebra translation algorithm.
After that, we explain our demonstration in [](#demo), after which we conclude in [](#conclusions).
