# Ecom Microservice GraphQL

## Project Overview

The **Ecom Microservice GraphQL** project is a comprehensive e-commerce solution built using a microservices architecture. It leverages various technologies and frameworks, including Node.js, Express, MongoDB, Kafka, and GraphQL, to create a scalable and efficient platform for managing users, products, and orders.

![WhatsApp Image 2024-10-17 at 21 53 32_2d732b15](https://github.com/user-attachments/assets/64bb3f84-8196-4639-a67f-135067d25515)



## Key Features

- **User Management**: User registration, login, and authentication.
- **Product Management**: Create, read, update, and delete products.
- **Order Management**: Manage customer orders efficiently.
- **GraphQL API Gateway**: Unified entry point for all services using GraphQL for data fetching.
- **Kafka Integration**: Asynchronous communication between microservices using Kafka for event-driven architecture.
- **Docker Support**: Containerized services for easy deployment and scalability.

  
## Technologies Used

- Node.js: Backend runtime environment.
- Express: Web framework for building APIs.
- MongoDB: NoSQL database for data storage.
- Kafka: Distributed event streaming platform for asynchronous communication.
- GraphQL: Query language for APIs and runtime for executing those queries.
- Docker: Containerization platform to run the application in isolated environments.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/ecom-microservice-graphql.git
   cd ecom-microservice-graphql
    ```

2.    ## Install Dependencies

Navigate to each service directory and install the dependencies using the following commands:

```bash
cd user-service
npm install
 ```
```bash
cd ../product-service
npm install
```
```bash
cd ../order-service
npm install
```
```bash
cd ../graphql-gateway
npm install
```
3. ## Configure Environment Variables: 
Create a .env file in each service directory as needed, or copy the .env.example provided.

## user-service:
```bash
MONGODB_URI=mongodb://mongodb:27017/user-service
PORT=3001
JWT_SECRET=your_jwt_secret_key_here
KAFKA_BROKER=kafka:9092
```

## product-service:
```bash
MONGODB_URI=mongodb://mongodb:27017/user-service
PORT=3001
JWT_SECRET=your_jwt_secret_key_here
KAFKA_BROKER=kafka:9092
```

## order-service:
```bash
MONGODB_URI=mongodb://mongodb:27017/order-service
PORT=3003
JWT_SECRET=your_jwt_secret_key_here
KAFKA_BROKER=kafka:9092
```

## graphql-gateway:
```bash
PORT=4000
KAFKA_BROKER=kafka:9092
```

4.  ## Start Services: Use Docker Compose to start all services:

```bash
docker-compose up -d
```

5. ## Access the Services:

User Service

```bash
http://localhost:3001/users
```

Product Service:

```bash
http://localhost:3002/products
```

Order Service:

```bash
http://localhost:3003/orders
```

GraphQL Gateway:

```bash
http://localhost:4000/graphql
```




## Testing

Use Postman or a similar tool to test the endpoints for user registration, product management, and order management.


## Project Structure

```bash
ecom-microservice-graphql/
├── user-service/              # User management microservice
│   ├── src/
│   │   ├── controllers/
│   │   │   └── userController.js      # Handles incoming requests for users
│   │   ├── models/
│   │   │   └── userModel.js           # User schema and Mongoose model
│   │   ├── routes/
│   │   │   └── userRoutes.js          # Routes for user-related actions
│   │   ├── services/
│   │   │   └── userService.js         # Business logic for users
│   │   ├── events/
│   │   │   ├── userProducer.js        # Produces Kafka events for user actions
│   │   │   └── userConsumer.js        # Consumes Kafka events related to users
│   │   └── app.js                     # Main entry point (Express setup)
│   ├── tests/
│   │   └── user.test.js               # Unit and integration tests for user-service
│   ├── Dockerfile                     # Dockerfile for user-service
│   ├── package.json                   # Package dependencies
│   └── .env.example                   # Example environment variables
│
├── product-service/           # Product management microservice
│   ├── src/
│   │   ├── controllers/
│   │   │   └── productController.js   # Handles product-related requests
│   │   ├── models/
│   │   │   └── productModel.js        # Product schema and Mongoose model
│   │   ├── routes/
│   │   │   └── productRoutes.js       # Routes for product-related actions
│   │   ├── services/
│   │   │   └── productService.js      # Business logic for products
│   │   ├── events/
│   │   │   ├── productProducer.js     # Produces Kafka events for products
│   │   │   └── productConsumer.js     # Consumes Kafka events related to products
│   │   └── app.js                     # Main entry point (Express setup)
│   ├── tests/
│   │   └── product.test.js            # Unit and integration tests for product-service
│   ├── Dockerfile                     # Dockerfile for product-service
│   ├── package.json                   # Package dependencies
│   └── .env.example                   # Example environment variables
│
├── order-service/             # Order management microservice
│   ├── src/
│   │   ├── controllers/
│   │   │   └── orderController.js     # Handles order-related requests
│   │   ├── models/
│   │   │   └── orderModel.js          # Order schema and Mongoose model
│   │   ├── routes/
│   │   │   └── orderRoutes.js         # Routes for order-related actions
│   │   ├── services/
│   │   │   └── orderService.js        # Business logic for orders
│   │   ├── events/
│   │   │   ├── orderProducer.js       # Produces Kafka events for orders
│   │   │   └── orderConsumer.js       # Consumes Kafka events related to orders
│   │   └── app.js                     # Main entry point (Express setup)
│   ├── tests/
│   │   └── order.test.js              # Unit and integration tests for order-service
│   ├── Dockerfile                     # Dockerfile for order-service
│   ├── package.json                   # Package dependencies
│   └── .env.example                   # Example environment variables
│
├── graphql-gateway/           # GraphQL API Gateway
│   ├── src/
│   │   ├── schemas/
│   │   │   └── index.js               # GraphQL schemas for user, product, and order
│   │   ├── resolvers/
│   │   │   └── index.js               # GraphQL resolvers
│   │   └── server.js                  # Apollo Server setup for GraphQL
│   ├── tests/
│   │   └── graphql.test.js            # Unit and integration tests for GraphQL API
│   ├── Dockerfile                     # Dockerfile for GraphQL API Gateway
│   ├── package.json                   # Package dependencies
│   └── .env.example                   # Example environment variables
│
├── kafka/                     # Kafka setup and configurations
│   ├── topics/
│   │   └── topicConfig.json           # Kafka topics configuration (user, product, order events)
│   └── consumers/
│       ├── userConsumer.js            # Kafka consumer for user-related events
│       ├── productConsumer.js         # Kafka consumer for product-related events
│       └── orderConsumer.js           # Kafka consumer for order-related events
│
├── docker-compose.yml         # Main Docker Compose for all services (microservices, GraphQL, Kafka, MongoDB)
├── package.json               # Package dependencies for the root directory
├── package-lock.json          # Package lock for the root directory
├── README.md                  # Documentation for the entire project
└── .env.example               # Main environment variables example for the root project



