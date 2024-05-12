# MongoDB aggregate - Problem 22

## Requirement

Count the number of people in each country by age groups as follows:
Calculate the percentage of the country's population in the following age groups:

- 18-29
- 30-39
- 40-49

Results must be rounded to two decimal places.

## Solution

```agg
db.people.aggregate([
  {
    $set: {
      currDate: {
        $dateFromString: {
          dateString: "2016-06-22",
          format: "%Y-%m-%d"
        }
      }
    }
  },
  {
    $set: {
      age: {
        $subtract: [
          { $year: "$currDate" },
          { $year: "$birthDate" }
        ] } }
  },
  {
    $group: {
      _id: {
        country: "$address.country",
        ageRange: {
          $switch: {
            branches: [
              { case: { $and: [
                    { $gte: [ "$age", 18 ] },
                    { $lte: [ "$age", 29 ] } ] },
                then: "18-29"
              },
              {
                case: { $and: [
                    { $gte: [ "$age", 30 ] },
                    { $lte: [ "$age", 39 ] } ] },
                then: "30-39"
              },
              {
                case: { $and: [
                    { $gte: [ "$age", 40 ] },
                    { $lte: [ "$age", 49 ] } ] },
                then: "40-49"
              }
            ],
            default: "Unknown"
          }
        }
      },
      count: { $sum: 1 }
    }
  },
  {
    $sort: { "_id.country": 1 }
  },
  {
    $group: {
      _id: "$_id.country",
      sum: { $sum: 1 },
      ageRange: { $push: "$_id.ageRange" } }
  },
  {
    $project: {
      _id: 0,
      country: "$_id",
      sum: 1,
      ageRange: 1 }
  },
  {
    $unwind: { path: "$ageRange" }
  },
  {
    $group: {
      _id: {
        ageRange: "$ageRange",
        country: "$country" },
      individualSum: { $sum: 1 },
      sum: { $first: "$sum" } }
  },
  {
    $project: {
      _id: 1,
      percentage: {
        $multiply: [ { $round: [
              { $divide: [ "$individualSum", "$sum" ] },
              2 ] },
          100 ] } }
  }
]).pretty()

```

db.people.aggregate([
{
$set: {
      currDate: {
        $dateFromString: {
          dateString: "2016-06-22",
          format: "%Y-%m-%d"
        }
      }
    }
  },
  {
    $set: {
      age: {
        $divide: [
          { $subtract: [ "$currDate", "$birthDate" ] },
          (365 *24*60*60*1000)
        ] } }
  },
  {
    $group: {
      _id: {
        country: "$address.country",
ageRange: {
$switch: {
            branches: [
              { case: { $and: [
                    { $gte: [ "$age", 18 ] },
{ $lte: [ "$age", 29 ] } ] },
then: "18-29"
},
{
case: { $and: [
                    { $gte: [ "$age", 30 ] },
{ $lte: [ "$age", 39 ] } ] },
then: "30-39"
},
{ case: { $and: [
                    { $gte: [ "$age", 40 ] },
{ $lte: [ "$age", 49 ] } ] },
then: "40-49"
}
],
default: "Unknown"
}
}
},
count: { $sum: 1 }
    }
  },
  {
    $sort: { "_id.country": 1 }
  },
  {
    $group: {
      _id: "$\_id.country",
sum: { $sum: 1 },
      ageRange: { $push: "$\_id.ageRange" } }
},
{
$project: {
      _id: 0,
      country: "$\_id",
sum: 1,
ageRange: 1 }
},
{
$unwind: { path: "$ageRange" }
},
{
$group: {
      _id: {
        ageRange: "$ageRange",
country: "$country" },
      individualSum: { $sum: 1 },
      sum: { $first: "$sum" } }
},
{
$project: {
      _id: 1,
      percentage: {
        $multiply: [ { $round: [
              { $divide: [ "$individualSum", "$sum" ] },
2 ] },
100 ] } }
}
]).pretty()

```agg

```

## Result

```result
{
 "_id": {
  "country": "Poland",
  "ageRange": "18-29"
 },
 "percent": 31.13
} {
 "_id": {
  "country": "Poland",
  "ageRange": "40-49"
 },
 "percent": 35.24
} {
 "_id": {
  "country": "Poland",
  "ageRange": "30-39"
 },
 "percent": 33.64
} {
 "_id": {
  "country": "France",
  "ageRange": "18-29"
 },
 "percent": 31.46
} {
 "_id": {
  "country": "France",
  "ageRange": "40-49"
 },
 "percent": 35.32
} {
 "_id": {
  "country": "France",
  "ageRange": "30-39"
 },
 "percent": 33.22
}

```
