# MongoDB aggregate - Problem 21

## Requirement

Count the number of people in each country by age groups as follows:

- 18-29
- 30-39
- 40-49

First of all, the number of people in each group depends on the current day. If we execute our query today or in a week, we may get different results. This is because people are getting older every day.

So it is very important to set an arbitrary date that will be used to calculate one's age.

So we will assume that the current date is: 22/06/2016

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
  }
]).pretty()

```

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
        $divide: [
          { $subtract: [ "$currDate", "$birthDate" ] },
          (365 * 24*60*60*1000)
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
                    { $lte: [ "$age", 29 ]  } ] },
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
                    { $lte: [ "$age",  49 ] } ] },
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
  }
]).pretty()

```

## Result

```result
{
	"_id": {
		"country": "Poland",
		"ageRange": "18-29"
	},
	"count": 30742.0
} {
	"_id": {
		"country": "France",
		"ageRange": "18-29"
	},
	"count": 31853.0
} {
	"_id": {
		"country": "Poland",
		"ageRange": "40-49"
	},
	"count": 34800.0
} {
	"_id": {
		"country": "France",
		"ageRange": "40-49"
	},
	"count": 35758.0
} {
	"_id": {
		"country": "Poland",
		"ageRange": "30-39"
	},
	"count": 33220.0
} {
	"_id": {
		"country": "France",
		"ageRange": "30-39"
	},
	"count": 33627.0
}

```
