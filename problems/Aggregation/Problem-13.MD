# MongoDB Aggregate - Problem 13

## Requirement

Find the user(s) with the highest number of friends.

## Solution

```agg
db.challenges.aggregate([
    {$project: { "name": 1, "numFriend": { $size:"$friends" }}},
    { "$sort": { "numFriend": -1 } },
    {$limit:1}
])
```

## Result

```result
{
  _id: ObjectId("64ed4ed7345377d730c0ac99"),
  name: 'John Doe',
  numFriend: 2
}
```
