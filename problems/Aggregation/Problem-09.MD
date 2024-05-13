# MongoDB Aggregate - Problem 9

## Requirement

Find the most common favorite food among all users.

## Solution

```agg
db.users.aggregate([
  {$group: {"_id":"$favorites.food",totalUser: {$sum:1}}},
  {$sort:{"totalUser":-1}},
  {$limit:1}
]);
```

## Result

```result
{
  _id: 'pizza',
  totalUser: 3
}
```
