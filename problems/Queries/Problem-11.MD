# MongoDB Query - Problem 11

## Requirement

Count all the people who have `never been to the cinema` (no cinema payments yet).

## Solution

```agg
db.people.find({"payments": {$not: {$elemMatch : {"name":"cinema"}}}} ).count()
```

## Result

```result
79996
```
