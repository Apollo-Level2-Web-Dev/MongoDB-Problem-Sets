# MongoDB Aggregate - Problem 12

## Requirement

Calculate each state's total number of users in the address field.

## Solution

```agg
db.challenges.aggregate([
  {$group: {"_id":"$address.state",totalUser: {$sum:1}}},
  {$sort:{"totalUser":1}}
]);
```

## Result

```result
{
  _id: 'FL',
  totalUser: 1
}
{
  _id: 'GA',
  totalUser: 1
}
{
  _id: 'WA',
  totalUser: 1
}
{
  _id: 'IL',
  totalUser: 1
}
{
  _id: 'CA',
  totalUser: 1
}
{
  _id: 'TX',
  totalUser: 2
}
{
  _id: 'NY',
  totalUser: 3
}
```
