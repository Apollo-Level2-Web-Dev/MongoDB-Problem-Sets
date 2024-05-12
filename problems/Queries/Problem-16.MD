# MongoDB Query - Problem 16

## Requirement

Finds all people with firstName = `'Thomas'` and returns only the following fields: `_id`, `firstName` and `lastName`.

## Solution

```agg
db.people.find({"firstName": "Thomas"}, {"firstName": 1, "lastName": 1}).pretty()
```

## Result

```result
[
 {
  "_id": "576865c1bab6cf2f2fb39d7e",
  "firstName": "Thomas",
  "lastName": "Lambert"
 },
 {
  "_id": "576865c1bab6cf2f2fb39d9a",
  "firstName": "Thomas",
  "lastName": "Fournier"
 },
 ...
 {
  "_id": "576865c2bab6cf2f2fb3a058",
  "firstName": "Thomas",
  "lastName": "Simon"
 }
]

```
