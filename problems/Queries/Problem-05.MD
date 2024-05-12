# MongoDB Query - Problem 5

## Requirement

Count all the people named `Pauline Fournier`.

## Solution

```agg
db.people.find({"firstName": "Pauline", "lastName": "Fournier"}).count()
```

## Result

```result
67
```
