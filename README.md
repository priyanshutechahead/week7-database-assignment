# week7-database-assignment

<img width="765" height="591" alt="Screenshot 2026-07-03 at 4 12 55 PM" src="https://github.com/user-attachments/assets/01a93d9a-f9cc-4876-a7bf-474f50b95ac7" />

## Design collections for: {USE inventory-DB}
- Users
'''({
  "_id": ObjectId(""),
  "name": "string",
  "email": "string",
  "number": "string",
  "userid": "string"
  "password": "string"
  "shippingAddress": {
    "street": "string",
    "city": "string",
    "zip": "string"
  },
  "createdAt": "date"
});```

- Products
'''db.users.insertOne({
  "_id": ObjectId(""),
  "name": "string",
  "description": "string",
  "category": "string",
  "brand": "string",
  "price": "string",
  "status": "string",
  "createdAt": "DATE"
});```

- Orders

## Use embedded documents or references where appropriate.
### Write the following MongoDB queries:
#### Insert a new user

Insert a new product
'''db.orders.insertOne({
  "_id": Objectid,
  "userId": Objectid,
  "orderDate": "DATE",
  "items": [
    {
      "productId": ObjectId,
      "name": "mechanical keyboard", 
      "price": 500,
      "quantity": 2
    }
  ],
  "totalAmount": 1000,
  "status": "Processing"
});```

Create a new order


Find all orders for a user
''' db.users.find()'''
''' db.products.find()'''
''' db.orders.find()'''
Update product stock

Delete an order

##Write one aggregation query to calculate:
Total amount spent by each user or
Total sales per product
Deliverables
MongoDB schema
Sample documents
CRUD queries
One aggregation query

