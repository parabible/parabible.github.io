---
subtitle: Making relational databases work for us
---

The real bottleneck in relational dbs is <querying multiple words>. Because large joins are expensive, this is especially true when those words being queried are common. The strength of <my initial approach> with JSON in memory was that doing intersections on arrays is *really quick*. So now I want to see if there's some way to leverage those ideas with a relational db.

# Idea 1: Intersect Multiple Result Sets

The first idea is to do mulitple queries for each word and then intersect those sets of results. Immediately the potential issues are obvious when multiple words are too common. It would be great if we could sort beforehand but sorting requires the query to complete anyway and so doesn't really help us performance-wise.

Here's an implementation of the idea

# Idea 2: Make Postgres do the Intersection

If only there were some way to get the intersection to happen in postgres. One of the major advantages of this is that we might be able to get a hosted db solution and then just stream results straight from the postgres server to the client.

The answer comes in the form of Pl/SQL (the scourge of our existence, tbh). 

Here's a function that intersects two sets.

Unfortunately, there's no VARIADIC for arrays (only for other types). So we have to create an equivalent function each time a new "number-of-words" is queried (i.e. xxx).


Here's an implementation.
