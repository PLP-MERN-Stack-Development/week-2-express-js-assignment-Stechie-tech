[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19694272&assignment_repo_type=AssignmentRepo)
# Express.js RESTful API Assignment

A RESTful API built with Express.js that implements CRUD operations for a product resource, with middleware, error handling, and advanced features.

## Features

- RESTful API endpoints for product management
- Custom middleware for logging, authentication, and validation
- Comprehensive error handling
- Advanced features including filtering, pagination, and search
- Product statistics endpoint

## Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Postman, Insomnia, or curl for API testing

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory with the following variables:
```
PORT=3000
API_KEY=your-secret-api-key-123
```

4. Start the server:
```bash
npm start
```

For development with auto-reload:
```bash
npm run dev
```

## API Endpoints

### Authentication
All API endpoints require an API key to be sent in the request headers:
```
x-api-key: your-secret-api-key-123
```

### Products

#### Get All Products
```
GET /api/products
```
Query Parameters:
- `category`: Filter by category
- `page`: Page number (default: 1)
- `limit`: Items per page (default: 10)
- `search`: Search by product name

Example Response:
```json
{
  "total": 3,
  "page": 1,
  "limit": 10,
  "products": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "High-performance laptop with 16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}
```

#### Get Product by ID
```
GET /api/products/:id
```

#### Create Product
```
POST /api/products
```
Request Body:
```json
{
  "name": "New Product",
  "description": "Product description",
  "price": 99.99,
  "category": "electronics",
  "inStock": true
}
```

#### Update Product
```
PUT /api/products/:id
```
Request Body: Same as Create Product

#### Delete Product
```
DELETE /api/products/:id
```

#### Get Product Statistics
```
GET /api/products/stats
```
Example Response:
```json
{
  "totalProducts": 3,
  "categories": {
    "electronics": 2,
    "kitchen": 1
  },
  "inStock": 2,
  "outOfStock": 1,
  "averagePrice": 683.33
}
```

## Error Handling

The API uses standard HTTP status codes:
- 200: Success
- 201: Created
- 400: Bad Request
- 401: Unauthorized
- 404: Not Found
- 500: Internal Server Error

Error Response Format:
```json
{
  "error": "Error message"
}
```

## Middleware

1. **Logger Middleware**
   - Logs request method, URL, and timestamp
   - Applied to all routes

2. **Authentication Middleware**
   - Validates API key
   - Applied to all `/api` routes

3. **Validation Middleware**
   - Validates product data for POST and PUT requests
   - Checks required fields and data types

## Testing

You can test the API using tools like Postman or curl. Here's an example using curl:

```bash
# Get all products
curl -H "x-api-key: your-secret-api-key-123" http://localhost:3000/api/products

# Create a new product
curl -X POST -H "x-api-key: your-secret-api-key-123" -H "Content-Type: application/json" \
  -d '{"name":"New Product","description":"Description","price":99.99,"category":"electronics","inStock":true}' \
  http://localhost:3000/api/products
```

## Files Included

- `Week2-Assignment.md`: Detailed assignment instructions
- `server.js`: Starter Express.js server file
- `.env.example`: Example environment variables file

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all the required API endpoints
2. Implement the middleware and error handling
3. Document your API in the README.md
4. Include examples of requests and responses

## Resources

- [Express.js Documentation](https://expressjs.com/)
- [RESTful API Design Best Practices](https://restfulapi.net/)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) 