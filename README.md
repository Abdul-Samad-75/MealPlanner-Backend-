
# API Documentation

## User Routes

### POST /api/register
**Purpose:** Creates a new user account.

#### Request Body:
- `name` (string): The user's name.
- `email` (string): The user's email address.
- `password` (string): The user's password.

#### Response:
- **Status 201 (Created):**
  ```json
  {"msg": "User created successfully"}
  ```
- **Status 400 (Bad Request):**
  ```json
  {"msg": "User already exists"}
  ```
- **Status 500 (Internal Server Error):**
  ```json
  {"msg": "error message"}
  ```

### POST /api/login
**Purpose:** Logs in an existing user.

#### Request Body:
- `email` (string): The user's email address.
- `password` (string): The user's password.

#### Response:
- **Status 200 (OK):**
  ```json
  {"token": "..."}
  ```
- **Status 404 (Not Found):**
  ```json
  {"msg": "User does not exist"}
  ```
- **Status 400 (Bad Request):**
  ```json
  {"msg": "Invalid password"}
  ```
- **Status 500 (Internal Server Error):**
  ```json
  {"msg": "error message"}
  ```

## Recipe Routes

### GET /api/
**Purpose:** Retrieves all recipes.

#### Response:
- **Status 200 (OK):** A JSON array of all recipes.
- **Status 500 (Internal Server Error):**
  ```json
  {"message": "Failed to fetch recipes", "error": "error details"}
  ```

### GET /api/search?name=<recipe_name>
**Purpose:** Search recipes by name.

#### Query Parameters:
- `name` (string): The recipe name to be searched.

#### Response:
- **Status 200 (OK):** A JSON array of matched recipes.
- **Status 500 (Internal Server Error):**
  ```json
  {"message": "Failed to fetch recipes", "error": "error details"}
  ```

### GET /api/filter?mealType=<mealType>&dietaryPreference=<dietaryPreference>
**Purpose:** Filter recipes by meal type and dietary preference.

#### Query Parameters:
- `mealType` (string): Meal type.
- `dietaryPreference` (string): Dietary preference.

#### Response:
- **Status 200 (OK):** A JSON array of matched recipes.
- **Status 500 (Internal Server Error):**
  ```json
  {"message": "Failed to fetch recipes", "error": "error details"}
  ```

### GET /api/sortby?sortbyCalories=<sortOrder>
**Purpose:** Sort recipes by calories in ascending (ASC) or descending (DESC) order.

#### Query Parameter:
- `sortOrder` (string): Sort order (ASC or DESC).

#### Response:
- **Status 200 (OK):** A JSON array of sorted recipes.
- **Status 500 (Internal Server Error):**
  ```json
  {"message": "Failed to fetch recipes", "error": "error details"}
  ```

## General Notes
- All routes should be prefixed with the `/api` endpoint. For example, to access the `register` route, call `/api/register`.
- All routes use JSON for request and response payloads.
- All routes require an authentication token sent in the `Authorization` header.
