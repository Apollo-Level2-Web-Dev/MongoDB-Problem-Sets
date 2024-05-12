# MongoDB Query - Problem 14

## Requirement

Count all the `female` from `Paris` and `male` from `Cracow` that have all of the following properties:

- `flat`
- `house`
- `land`

At least one of the properties must be valued at more than `$2,000,000`, and none of the properties under `$500,000`.

_Hint, assets are stored in the field "wealth.realEstates"_

## Solution

```agg
db.people.find({$and: [
 {$or: [ {$and: [ {"sex" : "female"}, {"address.city": "Paris"}  ] },
  {$and: [ {"sex" : "male"}, {"address.city": "Cracow"} ] } ] },
 {"wealth.realEstates": {$elemMatch: {"type": "flat"}}},
 {"wealth.realEstates": {$elemMatch: {"type": "house"}}},
 {"wealth.realEstates": {$elemMatch: {"type": "land"}}},
 {"wealth.realEstates": {$elemMatch: {"worth": {$gt: 2000000}}}},
 {"wealth.realEstates": {$not: {$elemMatch: {"worth": {$lt: 500000}}}}}
]}).count()

```

## Result

```result
23
```
