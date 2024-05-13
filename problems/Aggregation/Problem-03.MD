# MongoDB Aggregate - Problem 3

## Requirement

Count the number of users whose favorite movie is `"The Shawshank Redemption"`.

## Solution

```agg
db.users.aggregate([
  // pipeline 1 --> people who loves The Shawshank Redemption.
  {
    $match: { "favorites.movie": "The Shawshank Redemption" },
  },
  // pipeline 2 --> calculates the people who loves that movie
  {
    $count: "total",
  },
]);
```

## Result

```result
{
  total: 3
}
```
