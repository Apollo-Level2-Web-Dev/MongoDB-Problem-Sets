# MongoDB aggregate - Problem 15

## Requirement

What is the most popular address and how many people live there?

## Solution

```agg
db.people.aggregate([
 { $group: { _id: {country: "$address.country", city: "$address.city", postalCode: "$address.postalCode", street: "$address.street" }, total: { $sum: 1 } } },
 { $sort : {total: -1}},
 { $limit : 1}
]).pretty()
```

## Result

```result
{
 "_id": {
  "country": "Poland",
  "city": "Warsaw",
  "postalCode": "02-495",
  "street": "Aleje Jerozolimskie"
 },
 "total": 5744.0
}
```
