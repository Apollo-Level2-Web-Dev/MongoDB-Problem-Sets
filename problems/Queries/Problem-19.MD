# MongoDB Query - Problem 19

## Requirement

Delete all of everyone's `market` fields.

## Solution

```agg
db.people.updateMany({},{$unset: {"wealth.market" : ""}})
```

## Result

```result

```
