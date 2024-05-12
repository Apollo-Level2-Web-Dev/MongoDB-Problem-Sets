# MongoDB Query - Problem 8

## Requirement

Count all the people who have `no credits`.

You can find credits in the field `wealth.credits`., this field is an array, because people can have one or more credits, if the array is empty then there are no credits.

## Solution

```agg
db.people.find({"wealth.credits": {$size: 0}}).count()
```

## Result

```result
83089
```
