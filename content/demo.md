## Demonstration Overview
{:#demo}

In our demonstration, we will offer the live evaluation of a set of GraphQL-LD queries.
All of these queries, together with a guide to run the demonstration can be found as
a [gist](https://gist.github.com/rubensworks/9d6eccce996317677d71944ed1087ea6){:.mandatory}.

For example, [](#query) and [](#context) contain respectively a query and context
that will produce the results from [](#results) when executing against a DBpedia endpoint.

<figure id="query" class="listing">
````/code/query.txt````
<figcaption markdown="block">
GraphQL query to find all bands that Michael Jackson has written a song for.
</figcaption>
</figure>

<figure id="context" class="listing">
````/code/context.txt````
<figcaption markdown="block">
JSON-LD context for the query in [](#query).
</figcaption>
</figure>

<figure id="results" class="listing">
````/code/results.txt````
<figcaption markdown="block">
Results of the GraphQL query in [](#query), together with the JSON-LD context from [](#context).
</figcaption>
</figure>
