# MongoDB Query - Problem 4

## Requirement

Find all users over `30` whose favorite color is `"green"`.



## Result

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
{
  _id: ObjectId("64ed4ed7345377d730c0aca3"),
  name: 'Benjamin Hill',
  email: 'benjaminhill@example.com',
  age: 31,
  address: {
    street: '753 Maple St',
    city: 'Boston',
    state: 'MA',
    zipcode: '02101'
  },
  favorites: {
    color: 'green',
    food: 'steak',
    movie: 'The Lord of the Rings'
  },
  friends: [
    {
      name: 'Mila Wright',
      email: 'milawright@example.com'
    },
    {
      name: 'Logan King',
      email: 'loganking@example.com'
    }
  ]
}
```