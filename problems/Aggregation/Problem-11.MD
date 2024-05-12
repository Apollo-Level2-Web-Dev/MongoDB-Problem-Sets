# MongoDB Aggregate - Problem 11

## Requirement

Find the user(s) with the longest name.

## Solution

```agg
db.challenges.aggregate([{
  $addFields: {
    "nameLength": { $strLenCP: "$name" }
  }},
{ "$sort": { "nameLength": -1 } },
{$limit:1}
])

```

## Result

```result
{
  _id: ObjectId("64ed4ed7345377d730c0ac9f"),
  name: 'William Martinez',
  email: 'williammartinez@example.com',
  age: 36,
  address: {
    street: '654 Maple St',
    city: 'San Francisco',
    state: 'CA',
    zipcode: '94101'
  },
  favorites: {
    color: 'orange',
    food: 'pasta',
    movie: 'The Matrix'
  },
  friends: [
    {
      name: 'Sophia Wilson',
      email: 'sophiawilson@example.com'
    },
    {
      name: 'James Thompson',
      email: 'jamesthompson@example.com'
    }
  ],
  nameLength: 16
}
```
