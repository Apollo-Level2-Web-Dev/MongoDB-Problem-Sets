# MongoDB aggregate - Problem 18

## Requirement

There is a country where the average payment at a restaurant is the highest and a country where the average payment at a restaurant is the lowest. How many times more people in the first country spend than people in the second?

## Solution

```agg
db.people.aggregate([
 { $unwind: "$payments" },
 { $match: { "payments.name" : "restaurant" }},
 { $group: {
  _id: "$address.country",
  avgAmount: { $avg: "$payments.amount"} } },
 { $group: { _id: null,
            "minAmount" : {"$min" : "$avgAmount" },
            "maxAmount" : {"$max" : "$avgAmount" } } },
 { "$addFields" : { "diff" : { "$divide" : [ "$maxAmount", "$minAmount" ] } } }
]).pretty()

```

## Result

```result
{
 "_id": null,
 "diff": 1.23419013367179
}
```
