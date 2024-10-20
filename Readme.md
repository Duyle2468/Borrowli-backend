# API Introduction

This is the backend API for the **Order Food** project.

- **Authentication**: Login, Register, Logout
- **Account**: Get personal information, Update personal information
- **Dish**: Read, Add, Edit, Delete a dish
- **Media**: Upload images
- **Test API**

> **Important note**: Occasionally, pull the latest code from my GitHub repo as I might update the API logic while recording videos.

> In the `server/.env` file, there's a `COOKIE_MODE` property. Set it to `true` if you want to use cookies for server-side authentication.

## Technologies Used

- Node.js
- Fastify
- Sqlite

## Setup

Simply clone this repository, navigate to the folder, install the packages, and run the command:

```bash
cd server
npm i
npm run dev
If you want to run the production version, use the following commands:

bash
Copy code
npm run build
npm run start
To view the database, open Prisma Studio using the command:

bash
Copy code
npx prisma studio
It will run at http://localhost:5555.
```

The source code includes a .env file for configuration. You can change the backend API port in this file, with the default set to port 4000.

When you upload images, they will be stored in the /uploads directory within the server folder.

Response Format
Responses are returned in JSON format and always include a message field. Additionally, there may be data or errors fields.

Successful Response Example
json
Copy code
{
"data": {
"id": 2,
"name": "Iphone 11",
"price": 20000000,
"description": "Description for iPhone 11",
"image": "http://localhost:4000/static/bec024f9ea534b7fbf078cb5462b30aa.jpg",
"createdAt": "2024-03-11T03:51:14.028Z",
"updatedAt": "2024-03-11T03:51:14.028Z"
},
"message": "Product created successfully!"
}
Error Response Example
If the request body is incorrectly formatted, the server will return a 422 error.

For example, if the price field is missing from the request body:

json
Copy code
{
"message": "A validation error occurred when validating the body...",
"errors": [
{
"code": "invalid_type",
"expected": "number",
"received": "undefined",
"path": ["price"],
"message": "Required",
"field": "price"
}
],
"code": "FST_ERR_VALIDATION",
"statusCode": 422
}
For other errors, the server will return the error in the message field, like:

json
Copy code
{
"message": "Data not found!",
"statusCode": 404
}
API Details
The API runs by default at http://localhost:4000. If you want to change the port, you can do so in the .env file.

For most POST, PUT requests, the body must be in JSON format, and the Content-Type: application/json header must be included.

For image uploads, the request should be in form-data format.

User authentication for APIs is done through session tokens. These session tokens are JWTs, and the JWT secret key is stored in the .env file and used to create and verify tokens.

For APIs that require user authentication, such as the Account API group, you need to send the accessToken to the server through the Authorization: "Bearer <accessToken>" header.

Test API: To check if the API is working
GET /test: Returns a message confirming the API is working.
Real-time API
POST /guest/orders: Create a new order.
Quick Postman Setup
Currently, there's no Postman collection file available, but I will update it after finishing the course.

I have saved a file called NextJs Free API.postman_collection.json in the server folder. You can import this file into Postman to get my collection. Then, create a new environment, set the host variable to http://localhost:4000, and select this environment when calling the API.

Default Accounts
Admin account: admin@order.com | 123456
User accounts:

phuminhdat@gmail.com | 123123
buianhson@gmail.com | 123123
ngocbichhuynh@gmail.com | 123123
binhnguyen@gmail.com | 123123
go
Copy code

You can now copy the whole block and paste it directly into your `readme.md`.

```

```
