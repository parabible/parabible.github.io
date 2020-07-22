---
title: pt 3
subtitle: Graph Databases
---


Previous we ...<XXX>. There is actually a better solution than either of these options that makes querying a lot more straightforward. I have barely begun to delve into what is possible in this area so there may be better ways of structuring things than I am doing here but bear with me (and let me know how things can be done better).

# Graph Databases

The solution is graph databases. Instead of relational databases, where each word is represented as a node and the nodes are ordered/sorted by a keyin that row, in graph dbs, each word will be represented as a "node". Each node has edges that connect it to other nodes. This is what makes graph dbs different. In graph dbs, you traverse through the data. In relational dbs, there is not really traversal. You have to join tables to find relationships between rows.

Let's visualise...


# Advantages

1. Structure is intuitive

2. Querying is simple


# The Problem

1. RAM

2. Familiarity (learning curve)


# Conclusion

If it were feasible to spend time learning how to use graph dbs, I would do it. But I already know how relational dbs work. I know what their limits are and when I'm likely to hit them and I know how to scale them in certain respects. The familiarity I have with them makes graph dbs require inordinate investment. I have the same problem with really using the dvorak keyboard layout. I spent a short while learning it and got up to 50/60wpm but I normally type in the range of 80 to 100wpm. Getting to that speed (even if my dvorak typing would one day surpass my qwerty speed is not worth the time investment to me). Maybe this calculation is wrong but I have other things to spend time on... (pay me to learn about graph dbs, and I'll do it :D).

And there may be a couple of tricks up the realational db sleeve that we can pull out to make things better...
