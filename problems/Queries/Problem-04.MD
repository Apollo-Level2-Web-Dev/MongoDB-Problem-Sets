# MongoDB Query - Problem 4

## Requirement

Find the user(s) with the highest age.

## Solution

```agg
db.users.find().sort({age:-1}).limit(1) // for Highest age
db.users.find().sort({age:+1}).limit(1) // for Lowest age
```

## Result

Highest age

```result
{
  _id: ObjectId("64ed4ed7345377d730c0ac9d"),
  name: 'David Wilson',
  email: 'davidwilson@example.com',
  age: 45,
  address: {
    street: '789 Elm St',
    city: 'Chicago',
    state: 'IL',
    zipcode: '60001'
  },
  favorites: {
    color: 'green',
    food: 'steak',
    movie: 'The Dark Knight'
  },
  friends: [
    {
      name: 'Emily Brown',
      email: 'emilybrown@example.com'
    },
    {
      name: 'Daniel Taylor',
      email: 'danieltaylor@example.com'
    }
  ]
}
```

Lowest age

```result
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
