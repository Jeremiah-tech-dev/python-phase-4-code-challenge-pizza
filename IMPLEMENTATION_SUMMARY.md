# Pizza Restaurant API - Implementation Summary

## Completed Tasks

### 1. Models (server/models.py)
- **Restaurant Model**: Added relationships and serialization rules
  - `restaurant_pizzas` relationship with cascade delete
  - `pizzas` association proxy
  - Serialization rules to prevent recursion

- **Pizza Model**: Added relationships and serialization rules
  - `restaurant_pizzas` relationship with cascade delete
  - `restaurants` association proxy
  - Serialization rules to prevent recursion

- **RestaurantPizza Model**: Added relationships, foreign keys, and validation
  - `pizza_id` and `restaurant_id` foreign keys
  - Relationships to both Restaurant and Pizza
  - Price validation (must be between 1 and 30)
  - Serialization rules to prevent recursion

### 2. Routes (server/app.py)
- **GET /restaurants**: Returns all restaurants with id, name, and address
- **GET /restaurants/<int:id>**: Returns a single restaurant with nested restaurant_pizzas and pizza details
- **DELETE /restaurants/<int:id>**: Deletes a restaurant and its associated restaurant_pizzas
- **GET /pizzas**: Returns all pizzas with id, name, and ingredients
- **POST /restaurant_pizzas**: Creates a new restaurant_pizza with validation

### 3. Database Setup
- Created database tables using db.create_all()
- Seeded database with initial data
- All 11 tests passing successfully

## How to Run

1. Install dependencies:
   ```bash
   /usr/bin/python3 -m venv venv
   venv/bin/pip install Flask Flask-SQLAlchemy Flask-Migrate Flask-RESTful sqlalchemy-serializer Faker pytest
   ```

2. Initialize and seed the database:
   ```bash
   cd server
   ../venv/bin/python init_db.py
   ../venv/bin/python seed.py
   ```

3. Run the Flask application:
   ```bash
   ../venv/bin/python app.py
   ```

4. Run tests:
   ```bash
   cd ..
   venv/bin/python -m pytest -x server/testing/
   ```

## Test Results
All 11 tests passed:
- Restaurant GET routes (3 tests)
- Restaurant DELETE routes (2 tests)
- Pizza GET route (1 test)
- RestaurantPizza POST route (2 tests)
- RestaurantPizza validation (3 tests)
