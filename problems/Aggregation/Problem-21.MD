# MongoDB aggregate - Problem 21

## Requirement

Count the number of people in each country by age groups as follows:

- 18-29
- 30-39
- 40-49

First of all, the number of people in each group depends on the current day. If we execute our query today or in a week, we may get different results. This is because people are getting older every day.

So it is very important to set an arbitrary date that will be used to calculate one's age.

So we will assume that the current date is: 22/06/2016


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
