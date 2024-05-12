# MongoDB aggregate - Problem 20

## Requirement

Write a query to calculate the total value that a person has paid by each category.


## Result

```result
{
 "_id": {
  "$oid": "576865c0bab6cf2f2fb39d7a"
 },
 "firstName": "Lea",
 "lastName": "Bernard",
 "totalPayments": [{
   "category": "clothes",
   "amount": 315
  },
  {
   "category": "food",
   "amount": 5.57
  },
  {
   "category": "health",
   "amount": 28.22
  },
  {
   "category": "relax",
   "amount": 836.55
  }
 ]
},

```
