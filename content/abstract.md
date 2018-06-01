## Abstract
<!-- Context      -->
The Linked Open Data cloud has the potential of significantly
enhancing and transforming end-user applications.
For example, the use of URIs to identify things allows data joining between separate data sources.
Most popular (Web) application frameworks, such as React and Angular
have limited support for querying the Web of Linked Data,
which leads to a high-entry barrier for Web application developers.
Instead, these developers increasingly use the highly popular GraphQL query language
for retrieving data from GraphQL APIs,
because GraphQL is tightly integrated into these frameworks.
<!-- Need         -->
In order to lower the barrier for developers towards Linked Data consumption,
<!-- Task         -->
the Linked Open Data cloud needs to be queryable with GraphQL as well.
<!-- Object       -->
In this article, we introduce a method for transforming GraphQL queries coupled with a JSON-LD context to SPARQL,
and a method for converting SPARQL results to the GraphQL query-compatible response.
We demonstrate this method by implementing it into the Comunica framework.
<!-- Findings     -->
<!-- Conclusion   -->
This approach brings us one step closer towards widespread
Linked Data consumption for application development.
<!-- Perspectives -->

