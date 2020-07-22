---
title: Solution 1: A Sparsem, Wide Relational Table
---

The most obvious solution to structuring tagged biblical data is to put every word on its own row and give each piece of data a column. That would look something like this:

h1 | h2 | h3
---
x  | y  | z

# Practical Implications

1. empty values all over the place
2. adding new types of data = new columns

Because in reality it looks like this:

XXX sample table (scrollable)?

# Querying

1. Querying individual words is easy (even with multiple attributes)
Make sure you index...

2. Querying a set of words gets exponentially more expensive
