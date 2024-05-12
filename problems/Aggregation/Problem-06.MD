# MongoDB Aggregate - Problem 6

## Requirement

Calculate the average age of users with a favorite `"pizza"` food.

## Solution

```agg
db.challenges.aggregate([
  // pipeline 1 --> people who loves pizza
  {
    $match: { "favorites.food": "pizza" },
  },
  // pipeline 2 --> average age of that group
  {
    $group: {
      _id: null,
      average: { $avg: "$age" },
    },
  },
  // pipeline 3 --> closest integer
  {
    $project: {
      _id: 0,
      average: { $floor: { $toInt: "$average" } },
    },
  },
]);

```

## Result

```result
{
  average: 25
}
```