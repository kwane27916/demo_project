# FlytBase Backend Developer Project

## Project Overview

This project is a backend system designed for managing drone operations across multiple sites. Users can manage drones, sites, and missions, facilitating efficient drone-based surveying and mapping. This system allows for CRUD operations on user accounts, drones, missions, and sites, with additional features for categorizing and filtering missions.

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Core Functionalities](#core-functionalities)
4. [Technologies Used](#technologies-used)
5. [Installation](#installation)
6. [Configuration](#configuration)
7. [Usage](#usage)
8. [API Documentation](#api-documentation)
9. [Postman Collection](#postman-collection)
10. [Project Structure](#project-structure)
11. [Future Enhancements](#future-enhancements)
12. [Contributors](#contributors)
13. [License](#license)

## Introduction

FlytBase, Inc. is a leader in drone automation software products. This backend project enables users to manage multiple drones, sites, and missions, ensuring effective and automated surveying and mapping. The project incorporates authentication, data management, and advanced filtering functionalities to support user operations.

## Features

- User authentication using JWT
- CRUD operations for users, sites, drones, and missions
- Assigning drones to specific sites
- Filtering missions by categories (path, grid/survey, corridor)
- Data validation and error handling
- Bonus: Custom categories for missions

## Core Functionalities

### User Management

- **User Registration**: Allows users to create an account with a username and password.
- **User Login**: Users can log in to the system using their credentials and receive a JWT for authentication.
- **User Information Retrieval**: Fetch user details based on user ID.

### Site Management

- **Add Site**: Create a new site with a name and location.
- **Update Site**: Modify existing site details.
- **Delete Site**: Remove a site from the user's account.
- **Retrieve Sites**: Fetch details of all sites associated with a user.

### Drone Management

- **Add Drone**: Register a new drone under a specific site.
- **Update Drone**: Modify existing drone details and reassign it to a different site.
- **Delete Drone**: Remove a drone from the user's account.
- **Retrieve Drones by Site**: Fetch all drones associated with a specific site.

### Mission Management

- **Add Mission**: Create a new mission with specific coordinates and type, and assign it to a site.
- **Update Mission**: Modify existing mission details.
- **Delete Mission**: Remove a mission from the user's account.
- **Retrieve Missions by Site**: Fetch all missions associated with a specific site.
- **Retrieve Missions by Category**: Fetch all missions associated with a specific category.

### Category Management (Bonus)

- **Add Category**: Create a custom category for missions.
- **Update Category**: Modify existing category details.
- **Delete Category**: Remove a category from the user's account.
- **Retrieve Drones by Category**: Fetch all drones associated with a specific category.

## Technologies Used

- **Node.js**: Runtime environment
- **Express**: Backend framework
- **Postman**: API testing tool
- **MongoDB**: Database
- **JWT**: Authentication

## Installation

### Prerequisites

- Node.js (>=14.x)
- npm (>=6.x) or yarn
- MongoDB

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

3. **Start MongoDB server**
    ```sh
    mongod
    ```

4. **Run the application**
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
MONGO_URI=mongodb://localhost:27017/flytbase
JWT_SECRET=your_jwt_secret
```

## Usage

### Authentication

- Obtain a JWT token using the `/auth/login` endpoint.
- Use the token to access other API endpoints.

### CRUD Operations

- Manage users, sites, drones, and missions using the relevant endpoints.
- Assign and filter missions by category.

## API Documentation

### Authentication

- **Login**
    - **POST** `/auth/login`
    - Request: `{ "username": "user", "password": "password" }`
    - Response: `{ "access_token": "JWT_TOKEN" }`

### Users

- **Create User**
    - **POST** `/users`
    - Request: `{ "username": "user", "password": "password" }`
    - Response: `{ "id": "USER_ID", "username": "user" }`

- **Get User Information**
    - **GET** `/users/:id`
    - Response: `{ "id": "USER_ID", "username": "user" }`

### Sites

- **Add Site**
    - **POST** `/sites`
    - Request: `{ "name": "Site Name", "location": "Location" }`
    - Response: `{ "id": "SITE_ID", "name": "Site Name", "location": "Location" }`

- **Update Site**
    - **PUT** `/sites/:id`
    - Request: `{ "name": "New Site Name", "location": "New Location" }`
    - Response: `{ "id": "SITE_ID", "name": "New Site Name", "location": "New Location" }`

- **Delete Site**
    - **DELETE** `/sites/:id`
    - Response: `{ "message": "Site deleted successfully" }`

### Drones

- **Add Drone**
    - **POST** `/drones`
    - Request: `{ "name": "Drone Name", "siteId": "SITE_ID" }`
    - Response: `{ "id": "DRONE_ID", "name": "Drone Name", "siteId": "SITE_ID" }`

- **Update Drone**
    - **PUT** `/drones/:id`
    - Request: `{ "name": "New Drone Name", "siteId": "NEW_SITE_ID" }`
    - Response: `{ "id": "DRONE_ID", "name": "New Drone Name", "siteId": "NEW_SITE_ID" }`

- **Delete Drone**
    - **DELETE** `/drones/:id`
    - Response: `{ "message": "Drone deleted successfully" }`

### Missions

- **Add Mission**
    - **POST** `/missions`
    - Request: `{ "name": "Mission Name", "type": "path", "siteId": "SITE_ID", "coordinates": [...] }`
    - Response: `{ "id": "MISSION_ID", "name": "Mission Name", "type": "path", "siteId": "SITE_ID", "coordinates": [...] }`

- **Update Mission**
    - **PUT** `/missions/:id`
    - Request: `{ "name": "New Mission Name", "type": "grid/survey", "coordinates": [...] }`
    - Response: `{ "id": "MISSION_ID", "name": "New Mission Name", "type": "grid/survey", "coordinates": [...] }`

- **Delete Mission**
    - **DELETE** `/missions/:id`
    - Response: `{ "message": "Mission deleted successfully" }`

- **Retrieve Missions by Site**
    - **GET** `/missions/site/:siteId`
    - Response: `{ "missions": [...] }`

- **Retrieve Missions by Category**
    - **GET** `/missions/category/:categoryId`
    - Response: `{ "missions": [...] }`

### Categories (Bonus)

- **Add Category**
    - **POST** `/categories`
    - Request: `{ "name": "Category Name" }`
    - Response: `{ "id": "CATEGORY_ID", "name": "Category Name" }`

- **Update Category**
    - **PUT** `/categories/:id`
    - Request: `{ "name": "New Category Name" }`
    - Response: `{ "id": "CATEGORY_ID", "name": "New Category Name" }`

- **Delete Category**
    - **DELETE** `/categories/:id`
    - Response: `{ "message": "Category deleted successfully" }`

### Drones by Category (Bonus)

- **Retrieve Drones by Category**
    - **GET** `/drones/category/:categoryId`
    - Response: `{ "drones": [...] }`

## Postman Collection

The Postman collection for testing the APIs can be found in the `postman_collection.json` file. Import this file into Postman to test all the endpoints.

## Project Structure

```plaintext
src/
|-- auth/
|   |-- auth.controller.ts
|   |-- auth.module.ts
|   |-- auth.service.ts
|-- users/
|   |-- users.controller.ts
|   |-- users.module.ts
|   |-- users.service.ts
|-- sites/
|   |-- sites.controller.ts
|   |-- sites.module.ts
|   |-- sites.service.ts
|-- drones/
|   |-- drones.controller.ts
|   |-- drones.module.ts
|   |-- drones.service.ts
|-- missions/
|   |-- missions.controller.ts
|   |-- missions.module.ts
|   |-- missions.service.ts
|-- categories/
|   |-- categories.controller.ts
|   |-- categories.module.ts
|   |-- categories.service.ts
|-- app.module.ts
|-- main.ts
|-- common/
|   |-- filters/
|   |-- guards/
|   |-- pipes/
```

## Contributors

- 
