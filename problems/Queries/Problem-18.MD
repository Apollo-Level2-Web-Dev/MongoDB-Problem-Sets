# MongoDB Query - Problem 18

## Requirement

Add an element to the payments of people who are in `France` with the following structure:

```struc
{
 category: "relax",
 name: "disco",
 amount: 5.06
}

```

## Solution

```agg
db.people.updateOne({"address.country" : "France"},{$addToSet: {"payments": {"category": "relax", "name": "disco", "amount": 5.06}}})
```

```agg
db.people.updateMany({"address.country" : "France"},{$addToSet: {"payments": {"category": "relax", "name": "disco", "amount": 5.06}}})
```

```agg
db.people.find({"address.country" : "France"}).pretty()
```

## Result

```result
{
 category: "relax",
 name: "disco",
 amount: 5.06
}

```
