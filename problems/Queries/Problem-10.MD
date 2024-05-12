# MongoDB Query - Problem 10

## Requirement

Count all the people whose first payment was `$12.99` for the `cinema`.

In this lesson, you only count cases where `payments[0]` satisfy the above requirement.

## Solution

```agg
db.people.find({"payments.0.name" : "cinema", "payments.0.amount" : 12.99}).count()
```

## Result

```result
24
```
