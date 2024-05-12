# MongoDB Query - Problem 15

## Requirement

Count all the people who have exactly `10` transactions.

## Solution

```agg
db.people.find({"payments": {$size: 10}}).count()
```

## Result

```result
179972
```
