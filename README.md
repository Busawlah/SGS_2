# SGS_2
A NoSQL collection, schema and API endpoints for a shopping app. 

## Question
Design the NoSQL schemas for a shopping app.

**User story**: As a shopper, I want to be able to browse a catalog of products and add items to my shopping cart. I also want to be able to view the contents of my cart and adjust the quantity of items in my cart. Finally, I want to be able to place an order and receive confirmation of my order.



Tasks:

1. Analyze the requirements for the shopping app, including the entities (e.g. products, customers, orders) and their relationships.
2. Design the NoSQL schema for the shopping app based on the requirements.
3. Create a repository and push the schema designs.
4. Add the possible API endpoints to the README.md of the GitHub repository.
5. Submit your GitHub link.

## Solution

### Requirements for the schema, API endpoints and collection:
- A catalog of products that can be browsed by shoppers
- The ability for shoppers to add items to their cart and adjust quantities
- The ability for shoppers to view the contents of their cart and adjust quantities
- The ability for shoppers to place an order and receive confirmation.

![schema](https://user-images.githubusercontent.com/111570881/222977947-72c88eb5-7d23-4550-acdf-83141c9aa4b2.png)

### Entities
- Products
- Customers
- Orders
- Cart


### Relationship between the Entities
- Each customer can have one or many orders
- Each order can have one or many products
- Each customer can have one cart
- Each cart can have one or many products
- Each product can have one or many orders

#### Customer Collection:
```
{

  "_id": ObjectId("..."),
  "name": "Tim Cook",
  "email": "tim.cook@example.com",
  "address": "123 Billy St",
  "cart": ObjectId("..."),
  "orders": [
    ObjectId("..."),
    ObjectId("...")
]
}
```

#### Product Collection:
```
{
  "_id": ObjectId("..."),
  "name": "Product 1",
  "description": "This is product 1",
  "price": 15.70,
  "image_url": "https://example.com/product1.jpg"
}
```

#### Order Collection:
```
{
    "_id": ObjectId("..."),
    "customer": ObjectId("..."),
    "items": [
    {
    "product": ObjectId("..."),
    "quantity": 2
    },
    {
    "product": ObjectId("..."),
    "quantity": 1
    }
    ],
    "total": 32.97,
    "status": "pending",
    "created_at": ISODate("...")
}
```

#### Cart Collection:
```
{
  "_id": ObjectId("..."),
  "customer": ObjectId("..."),
  "items": [
    {
    "product": ObjectId("..."),
    "quantity": 2
    },
    {
    "product": ObjectId("..."),
    "quantity": 1
    }
  ]
}
```

In this schema, the `Customer` collection stores information about the customers, including their `name`, `email`, and `address`. Each customer has a cart and can have one or many orders. The `Product` collection stores information about the products, including the `name`, `description`, `price`, and `image URL`. The `Order` collection stores information about the orders, including the customer ID, items, total price, status, and creation date. The `Cart` collection stores the items that a customer has added to their `cart`, including the product ID and quantity.

## API End points

### Customers

**`GET /api/customers`**: Get a list of all customers

**`GET /api/customers/:id`**: Get a specific customer by ID

**`POST /api/customers`**: Create a new customer

**`PUT /api/customers/:id`**: Update a specific customer by ID

**`DELETE /api/customers/:id`**: Delete a specific customer by ID


### Products

**`GET /api/products`**: Get a list of all products

**`GET /api/products/:id`**: Get a specific product by ID

**`POST /api/products`**: Create a new product

**`PUT /api/products/:id`**: Update a specific product by ID

**`DELETE /api/products/:id`**: Delete a specific product by ID


### Orders

**`GET /api/orders`**: Get a list of all orders

**`GET /api/orders/:id`**: Get a specific order by ID

**`POST /api/orders`**: Create a new order

**`PUT /api/orders/:id`**: Update a specific order by ID

**`DELETE /api/orders/:id`**: Delete a specific order by ID


### Carts

**`GET /api/carts/:id`**: Get the cart for a specific customer by customer ID

**`POST /api/carts/:id/items`**: Add an item to the cart for a specific customer by customer ID

**`PUT /api/carts/:id/items/:itemId`**: Update the quantity of an item in the cart for a specific customer by customer ID and item ID

**`DELETE /api/carts/:id/items/:itemId`**: Remove an item from the cart for a specific customer by customer ID and item ID
