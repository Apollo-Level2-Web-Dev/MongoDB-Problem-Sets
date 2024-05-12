# MongoDB Aggregate - Problem 7

## Requirement

Perform a lookup aggregation to retrieve the orders data along with the customer details for each order.



## Result

```result
{
  _id: 1,
  order_number: 'ORD-001',
  inventory: [
    {
      _id: 1,
      name: 'Alice Williams',
      email: 'alice@example.com'
    }
  ]
}
{
  _id: 2,
  order_number: 'ORD-002',
  inventory: [
    {
      _id: 2,
      name: 'Bob Anderson',
      email: 'bob@example.com'
    }
  ]
}
{
  _id: 3,
  order_number: 'ORD-003',
  inventory: [
    {
      _id: 1,
      name: 'Alice Williams',
      email: 'alice@example.com'
    }
  ]
}

```
