# MongoDB Query - Problem 13

## Requirement

Count all the people from `Warsaw`, `Poland` who have been to the `cinema` but never to the `disco`.

## Solution

```agg
db.people.find({$and: [
{"address.city": "Warsaw"},
{"address.country": "Poland"},
{"payments": {$elemMatch: {"name": "cinema"}}},
{"payments": {$not: {$elemMatch: {"name": "disco"}}}}
]}).count()

```

## Result

```result
13352
```
