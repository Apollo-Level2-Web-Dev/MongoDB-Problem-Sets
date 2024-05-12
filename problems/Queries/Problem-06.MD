# MongoDB Query - Problem 6

## Requirement

Count all people whose name is `Pauline Fournier` and who were born before `January 1, 1970`.

## Solution

```agg
db.people.find({"firstName": "Pauline", "lastName": "Fournier", "birthDate": {$lt: ISODate("1970-01-01")}} ).count()
```

## Result

```result
9
```
