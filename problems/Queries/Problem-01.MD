# MongoDB Query - Problem 1

## Requirement

Find all users who are located in `New York`.

## Solution

```agg
db.users.find({ "address.city": "New York" });
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
    zipcode: '10001'
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
    zipcode: '10001'
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
    zipcode: '10001'
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
