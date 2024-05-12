# MongoDB Query - Problem 2

## Requirement

Find the user(s) with the email "<johndoe@example.com>" and retrieve their favorite movie.



## Result

```result
{
  _id: ObjectId("64ed4ed7345377d730c0ac99"),
  email: 'johndoe@example.com',
  favorites: {
    movie: 'The Shawshank Redemption'
  }
}
{
  _id: ObjectId("64ed4ed7345377d730c0ac9a"),
  email: 'johndoe@example.com',
  favorites: {
    movie: 'The Shawshank Redemption'
  }
}
{
  _id: ObjectId("64ed4ed7345377d730c0ac9b"),
  email: 'johndoe@example.com',
  favorites: {
    movie: 'The Shawshank Redemption'
  }
}
```