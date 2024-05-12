# MongoDB aggregate - Problem 19

## Requirement

Write a query to find all people with one or more transactions worth less than $5. The returned results only include the fields firstName, lastName and the payments array containing ALL elements with amount less than 5$.


## Result

```result
{
 "_id": "5768667dbab6cf2f2fb5b63e",
 "firstName": "Igor",
 "lastName": "Kowalczyk",
 "payments": [{
   "category": "food",
   "name": "store",
   "amount": 4.54
  },
  {
   "category": "food",
   "name": "store",
   "amount": 4.56
  },
  {
   "category": "food",
   "name": "store",
   "amount": 3.05
  }
 ]
}

```
