# MongoDB Aggregate - Problem 5

## Requirement

Group users by their favorite movie and retrieve the average age in each movie group.

## Solution

```agg
db.users.aggregate([
  // pipeline 1 --> group user by favorite movie
  // and return their average age in each group
  {
    $group: {
      _id: "$favorites.movie",
      average: { $avg: "$age" },
    },
  },
]);
```

## Result

```result
{
  _id: 'The Lion King',
  average: 27
}
{
  _id: 'The Matrix',
  average: 36
}
{
  _id: 'Inception',
  average: 22
}
{
  _id: 'Pulp Fiction',
  average: 29
}
{
  _id: 'The Shawshank Redemption',
  average: 25.333333333333332
}
{
  _id: 'The Dark Knight',
  average: 45
}
{
  _id: 'The Avengers',
  average: 33
}
{
  _id: 'The Lord of the Rings',
  average: 31
}
{
  _id: 'Forrest Gump',
  average: 25
}
```
