---
title: part 2
---

I discussed the most obvious option for structuring... here...

Another option is to make a really long table with three columns:

wid | key | value

The Primary Key is a combination of wid and key

This makes for an extraordinarily long table because every data point is a new row in this table.

# In Practice

You may be thinking, how can you query this table? Actually, it's not difficult if you knew how to query multiple words on the previous table. If you only want words that match a single criterion, it's relatively easy:



Even if you want to match on multiple criteria, it just requires the same kind of self-joins as we saw in the previous post (although now just for a single word):



Querying multiple words becomes a lot more cumbersome, though:

# Conclusion

Actually, this is an antipattern. XXX

The sparse wide table is a much better solution. But there may be an even better solution...



