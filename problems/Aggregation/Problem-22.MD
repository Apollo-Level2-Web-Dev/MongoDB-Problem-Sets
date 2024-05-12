# MongoDB aggregate - Problem 22

## Requirement

Count the number of people in each country by age groups as follows:
Calculate the percentage of the country's population in the following age groups:

- 18-29
- 30-39
- 40-49

Results must be rounded to two decimal places.


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
