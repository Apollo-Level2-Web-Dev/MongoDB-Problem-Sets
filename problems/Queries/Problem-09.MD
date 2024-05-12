# MongoDB Query - Problem 9

## Requirement

Count everyone who spent exactly `$12.99` on the `cinema`.

All payments are stored in the payments array field, let's take a look at the structure of the elements in this array to write a reasonable query.

## Solution

```agg
db.people.find({"payments" :
    { $elemMatch: { "name" : "cinema", "amount" : 12.99 } } }).count()

```

## Result

```result
270
```
