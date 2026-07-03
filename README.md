# week7-database-assignment

<img width="765" height="591" alt="Screenshot 2026-07-03 at 4 12 55 PM" src="https://github.com/user-attachments/assets/01a93d9a-f9cc-4876-a7bf-474f50b95ac7" />

## Design collections for: {USE inventory-DB}
- Users
<img width="871" height="749" alt="Screenshot 2026-07-03 at 4 49 42 PM" src="https://github.com/user-attachments/assets/48a92196-53b5-4797-9cd9-dca4d0746205" />
<img width="1165" height="530" alt="Screenshot 2026-07-03 at 5 03 55 PM" src="https://github.com/user-attachments/assets/3e93767f-c69b-4082-af30-c98b3d10fa46" />


- Products
db.createCollection("products", {
   validator: {
      $jsonSchema: {
         bsonType: "object",
         required: [ "name", "sku", "price", "stock" ],
         properties: {
            name: { bsonType: "string" },
            sku: { bsonType: "string" },
            price: { bsonType: "double" },
            stock: { bsonType: "int" }
         }
      }
   }
});

- Orders
<img width="1302" height="390" alt="Screenshot 2026-07-03 at 4 57 49 PM" src="https://github.com/user-attachments/assets/b85c05fb-271d-49a3-864d-964eaa2c1fbc" />


## Use embedded documents or references where appropriate.
### Write the following MongoDB queries:
#### Insert a new user

Insert a new product


Create a new order


Find all orders for a user
''' db.users.find()'''
''' db.products.find()'''
''' db.orders.find()'''

Update product stock
<img width="1078" height="426" alt="Screenshot 2026-07-03 at 4 54 18 PM" src="https://github.com/user-attachments/assets/15a3cc5f-d4b3-43c3-ba0f-a2c55965eecf" />

Delete an order

##Write one aggregation query to calculate:
Total amount spent by each user or
Total sales per product
```
db.orders.aggregate([
  {
    "$group": {
      "_id": "$userId",
      "totalSpent": { "$sum": "$totalAmount" },
      "orderCount": { "$sum": 1 }
    }
  },
  {
    "$lookup": {
      "from": "users",
      "localField": "_id",
      "foreignField": "_id",
      "as": "userDetails"
    }
  },
  {
    "$unwind": "$userDetails"
  },
  {
    "$project": {
      "_id": 0,
      "userId": "$_id",
      "userName": "$userDetails.name",
      "userEmail": "$userDetails.email",
      "totalSpent": 1,
      "orderCount": 1
    }
  }
]);

