# MongoDB aggregate - Problem 19

## Requirement

Write a query to find all people with one or more transactions worth less than $5. The returned results only include the fields firstName, lastName and the payments array containing ALL elements with amount less than 5$.

## Solution

```agg
db.people.find(
{ "payments.amount": {$lt: 5}},
{ firstName: 1,
    lastName: 1,
    payments: {$elemMatch: {amount: { $lt: 5 } } } }
).pretty()

```

```agg
db.people.aggregate([
 { $unwind: "$payments"},
 { $match: { "payments.amount": {$lt: 5} } },
 { $group: { _id: { _id: "$_id", firstName: "$firstName", lastName: "$lastName" },
      payments : {
   "$addToSet" : {
    category: "$payments.category",
    name: "$payments.name",
    amount: "$payments.amount"} } } },
 { $project: { _id: 1, firstName: 1, lastName: 1, payments: 1 }}
]).pretty()

```

```agg
db. people.aggregate([
  {
    $unwind: "$payments"
  },
  {
    $match: {
      "payments.amount": {
        $lt: 5
      }
    }
  },
  {
    $group: {
      _id: {
        _id: "$_id",
        firstName: "$firstName",
        lastName: "$lastName"
      },
      payments: {
        "$push": {
          category: "$payments.category",
          name: "$payments.name",
          amount: "$payments.amount"
        }
      }
    }
  },

])

```

## Result

```result
{
 "_id": "5768667dbab6cf2f2fb5b63e",
 "firstName": "Igor",
 "lastName": "Kowalczyk",
 "payments": [{
   "category": "food",
   "name": "store",
   "amount": 4.54
  },
  {
   "category": "food",
   "name": "store",
   "amount": 4.56
  },
  {
   "category": "food",
   "name": "store",
   "amount": 3.05
  }
 ]
}

```
