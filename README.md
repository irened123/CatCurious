# CatCurious API

## Overview
The **CatCurious API** is a Flask-based RESTful API designed for cat enthusiasts to interact with a database of cats. It allows users to add, delete, and retrieve information about cats, while also integrating external APIs to provide additional details such as pictures, lifespan, and random cat facts.

---

## Acknowledgment
This repository is a **forked version of a collaborative project** originally developed by **me, Jay Patel**, and **Letitia Caspersen** for Boston University's CS411 Software Engineering course. The original repository can be found [here](https://github.com/tenjx10/CatCurious).

---

## Set Up
To run this application, please generate a key from The Cat API. We also used the Cat Fact API, which does not require a key. Please set up and activate a virtual environment using setup_venv.sh and run the docker script run_docker.sh. To run the unit tests specifically, please run via the unit test branch, not the main branch. Once again, to view pictures of our passing smoke and unit tests, please see the grading folder on the main branch. 

---

## ROUTES:

### Route: `/api/create-cat`
- **Request Type**: POST
- **Purpose**: Adds a new cat to the database.
- **Request Body**:
  - `name` (String): The cat's name.
  - `breed` (String): The cat's breed.
  - `age` (Integer): The cat's age.
  - `weight` (Integer): The cat's weight.
- **Response Format**:
  - **Success Response Example**:
    - Code: 201
    - Content: `{ "status": "success", "cat": "Fluffy" }`
  - **Error Response Example**:
    - Code: 400
    - Content: `{ "error": "Invalid input, all fields are required with valid values" }`

### Route: `/api/clear-cats`
- **Request Type**: DELETE
- **Purpose**: Clears all cats from the database.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success" }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to clear cats" }`

### Route: `/api/delete-cat/<int:cat_id>`
- **Request Type**: DELETE
- **Purpose**: Deletes a cat from the database by its ID.
- **Path Parameter**:
  - `cat_id` (Integer): The ID of the cat to delete.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success" }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to delete cat" }`

### Route: `/api/get-cat-by-id/<int:cat_id>`
- **Request Type**: GET
- **Purpose**: Retrieves a cat from the database by its ID.
- **Path Parameter**:
  - `cat_id` (Integer): The ID of the cat.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "cat": { "name": "Fluffy", "breed": "Persian", "age": 3, "weight": 5 } }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to retrieve cat" }`

### Route: `/api/get-cat-by-name/<str:cat_name>`
- **Request Type**: GET
- **Purpose**: Retrieves a cat from the database by its name.
- **Path Parameter**:
  - `cat_name` (String): The name of the cat.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "cat": { "name": "Fluffy", "breed": "Persian", "age": 3, "weight": 5 } }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to retrieve cat" }`

### Route: `/api/init-db`
- **Request Type**: POST
- **Purpose**: Initializes or recreates database tables.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "message": "Database initialized successfully." }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "status": "error", "message": "Failed to initialize database." }`

### Route: `/api/get-affection-level/<string:breed>`
- **Request Type**: GET
- **Purpose**: Retrieves the affection level of a cat breed.
- **Path Parameter**:
  - `breed` (String): The breed of the cat.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "breed": "Persian", "affection_level": 5 }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to fetch affection level" }`

### Route: `/api/get-cat-facts/<int:num_facts>`
- **Request Type**: GET
- **Purpose**: Retrieves a number of random cat facts.
- **Path Parameter**:
  - `num_facts` (Integer): The number of facts to retrieve.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "facts": ["Cats sleep 70% of their lives.", "Cats can rotate their ears 180 degrees."] }`
  - **Error Response Example**:
    - Code: 400
    - Content: `{ "error": "Num_facts must be a positive integer." }`

### Route: `/api/get-cat-pic/<string:breed>`
- **Request Type**: GET
- **Purpose**: Retrieves a picture of a cat breed.
- **Path Parameter**:
  - `breed` (String): The breed of the cat.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "cat_picture_url": "https://link_to_cat_picture.jpg" }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to fetch cat picture" }`

### Route: `/api/get-cat-lifespan/<string:breed>`
- **Request Type**: GET
- **Purpose**: Retrieves the lifespan of a cat breed.
- **Path Parameter**:
  - `breed` (String): The breed of the cat.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "breed": "Persian", "lifespan": "12-16 years" }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to fetch cat lifespan" }`

### Route: `/api/get-random-cat-image`
- **Request Type**: GET
- **Purpose**: Retrieves a random cat image.
- **Response Format**:
  - **Success Response Example**:
    - Code: 200
    - Content: `{ "status": "success", "cat_image_url": "https://random_cat_image.jpg" }`
  - **Error Response Example**:
    - Code: 500
    - Content: `{ "error": "Failed to fetch random cat image" }`
