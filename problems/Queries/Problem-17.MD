# MongoDB Query - Problem 17

## Requirement

Find everyone who has one or more transactions worth less than `$5`.

The returned results only include the `firstName`, `lastName` and `payments` fields containing only the first word whose amount is less than 5$.


## Result

```result
[
 {
  "_id": "576865c1bab6cf2f2fb39daa",
  "firstName": "Nicolas",
  "lastName": "Bernard",
  "payments": [{
   "category": "food",
   "name": "store",
   "amount": 3.47
  }]
 },
 {
  "_id": "576865c1bab6cf2f2fb39dbe",
  "firstName": "Kacper",
  "lastName": "Dabrowski",
  "payments": [{
   "category": "food",
   "name": "store",
   "amount": 3.16
  }]
 },
 ...
 {
  "_id": "576865c1bab6cf2f2fb39fc6",
  "firstName": "Camille",
  "lastName": "Robert",
  "payments": [{
   "category": "food",
   "name": "store",
   "amount": 4.39
  }]
 }
]

```
