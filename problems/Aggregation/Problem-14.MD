# MongoDB aggregate - Problem 14

## Requirement

Count the number of people in each country.

## Solution

```agg
db.people.aggregate([
 { $group: { _id: "$address.country", total: { $sum: 1 } } },
 { $sort : {total: -1}}
]).pretty()
```

## Result

```result
{
 "_id": "France",
 "total": 101238.0
} {
 "_id": "Poland",
 "total": 98762.0
}
```
