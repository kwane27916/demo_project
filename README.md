# User Management API

## Objective

Develop a user management API using Node.js and Express.js with TypeScript and link the API to a database.

## Table of Contents

1. [Requirements](#requirements)
2. [Technologies Used](#technologies-used)
3. [Installation](#installation)
4. [Configuration](#configuration)
5. [Usage](#usage)
6. [API Documentation](#api-documentation)
7. [Testing](#testing)
8. [Live Demo](#live-demo)
9. [Contributors](#contributors)

## Requirements

- Implement CRUD operations for managing users.
- Utilize Node.js for backend development.
- Use Express.js for API creation with TypeScript.
- Link the API to a database (e.g., MongoDB, PostgreSQL).
- Write test cases for the API endpoints using Jest.
- Ensure proper error handling and validation for API requests.
- Document the API endpoints using tools like Swagger or OpenAPI.

## Technologies Used

- **Node.js**
- **Express.js** (with TypeScript)
- **MongoDB** or **PostgreSQL**
- **Jest** (for testing)
- **Swagger** or **OpenAPI** (for API documentation)

## Installation

### Prerequisites

- Node.js (>=14.x)
- npm (>=6.x) or yarn
- MongoDB or PostgreSQL

### Steps

1. **Clone the repository**
    ```sh
    git clone https://github.com/your-repository.git
    cd your-repository
    ```

2. **Install dependencies**
    ```sh
    npm install
    # or
    yarn install
    ```

3. **Run the application**
    ```sh
    npm run start:dev
    # or
    yarn start:dev
    ```

## Configuration

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```plaintext
PORT=3000
DATABASE_URI=your_database_uri
JWT_SECRET=your_jwt_secret
```

## Usage

### CRUD Operations

- Create, Read, Update, and Delete users using the API endpoints.

### API Documentation

- **Swagger** or **OpenAPI** documentation can be accessed at `/api-docs`.

## Testing

### Running Tests

```sh
npm run test
# or
yarn test
```

## Contributors

- [Dhyey Vora](https://github.com/DhyeyVora-1706)
