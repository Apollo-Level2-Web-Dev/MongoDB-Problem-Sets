# MongoDB Aggregate - Problem 4

## Requirement

Update the zipcode of the user with the email `"johndoe@example.com"` to `"10002"`.

## Solution

```agg
db.challenges.aggregate([
  // pipeline 1 --> find user by emaal
  {
    $match: { email: "johndoe@example.com" },
  },
  // pipeline 2 --> update the zipcode
  {
    $set: { "address.zipcode": "10002" },
  },
]);
```

## Result

```result
{
  _id: ObjectId("64ed4ed7345377d730c0ac99"),
  name: 'John Doe',
  email: 'johndoe@example.com',
  age: 28,
  address: {
    street: '123 Main St',
    city: 'New York',
    state: 'NY',
    zipcode: '10002'
  },
  favorites: {
    color: 'blue',
    food: 'pizza',
    movie: 'The Shawshank Redemption'
  },
  friends: [
    {
      name: 'Jane Smith',
      email: 'janesmith@example.com'
    },
    {
      name: 'Mike Johnson',
      email: 'mikejohnson@example.com'
    }
  ]
}
{
  _id: ObjectId("64ed4ed7345377d730c0ac9a"),
  name: 'Pohn Doe',
  email: 'johndoe@example.com',
  age: 30,
  address: {
    street: '123 Main St',
    city: 'New York',
    state: 'NY',
    zipcode: '10002'
  },
  favorites: {
    color: 'blue',
    food: 'pizza',
    movie: 'The Shawshank Redemption'
  },
  friends: [
    {
      name: 'Jane Smith',
      email: 'janesmith@example.com'
    },
    {
      name: 'Mike Johnson',
      email: 'mikejohnson@example.com'
    }
  ]
}
{
  _id: ObjectId("64ed4ed7345377d730c0ac9b"),
  name: 'Dohn Doe',
  email: 'johndoe@example.com',
  age: 18,
  address: {
    street: '123 Main St',
    city: 'New York',
    state: 'NY',
    zipcode: '10002'
  },
  favorites: {
    color: 'blue',
    food: 'pizza',
    movie: 'The Shawshank Redemption'
  },
  friends: [
    {
      name: 'Jane Smith',
      email: 'janesmith@example.com'
    },
    {
      name: 'Mike Johnson',
      email: 'mikejohnson@example.com'
    }
  ]
}
```