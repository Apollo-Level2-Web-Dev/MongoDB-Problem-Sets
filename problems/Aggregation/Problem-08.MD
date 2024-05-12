# MongoDB Aggregate - Problem 8

## Requirement

Group users by their favorite color and retrieve the count of users in each color group.

## Solution

```agg
db.challenges.aggregate([
  {$group: {"_id":"$favorites.color", name: {$push:"$name"},totalUser: {$sum:1}}},
  {$sort:{"totalUser":-1}}
]);
```

## Result

```result
{
  _id: 'blue',
  name: [
    'John Doe',
    'Pohn Doe',
    'Dohn Doe',
    'Ava Moore'
  ],
  totalUser: 4
}
{
  _id: 'green',
  name: [
    'David Wilson',
    'Benjamin Hill'
  ],
  totalUser: 2
}
{
  _id: 'purple',
  name: [
    'Olivia Johnson',
    'Charlotte Lee'
  ],
  totalUser: 2
}
{
  _id: 'orange',
  name: [
    'William Martinez'
  ],
  totalUser: 1
}
{
  _id: 'yellow',
  name: [
    'Ethan Anderson'
  ],
  totalUser: 1
}
{
  _id: 'pink',
  name: [
    'Mia Taylor'
  ],
  totalUser: 1
}
```