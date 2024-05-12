# MongoDB aggregate - Problem 16

## Requirement

How many people in each country have ever paid at a restaurant?

## Solution

```agg
db.people.aggregate([
 { $match: { "payments": { $elemMatch: { "name" : "restaurant" } } } },
 { $group: { _id: "$address.country", visits: { $sum: 1 } } },
 { $sort : { visits: -1 } }
]).pretty()

```

## Result

```result
{
 "_id": "France",
 "visits": 53126.0
} {
 "_id": "Poland",
 "visits": 46971.0
}

```
