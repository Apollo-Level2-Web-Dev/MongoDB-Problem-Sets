# MongoDB Query - Problem 12

## Requirement

Count all the `female` who spent more than `$100` on `shoes` and more than `$50` on `pants` in one bill.

## Solution

```agg
db.people.find({$and: [
{"sex": "female"},
{"payments": {$elemMatch: {"name": "shoes", "amount": {$gt:100}}}},
{"payments": {$elemMatch: {"name": "pants", "amount": {$gt:50}}}}
]}).count()

```

## Result

```result
913
```
