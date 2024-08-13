<div align="center">
  <h1>FastAPI Application Documentation</h1>
  <div>
    <img src="https://img.shields.io/badge/-Python-black?style=for-the-badge&logoColor=white&logo=python&color=FFD700" alt="typescript" />
  </div>
  <h3 align="center">A FastAPI Implimentation</h3>
</div>

# Overview
This documentation covers the implementation details and usage of a FastAPI application designed for managing authentication, workouts, and routines. The application uses SQLAlchemy for database management, and the CORS middleware is configured to allow cross-origin requests from specified origins.

## <a name="table">Table of Contents</a>
1. Getting Started
2. Middlware
3. Routes
  - Health Check
  - Authentication Routes
  - Workout Routes
  - Routine Routes
4. Database Configuration

## Getting Started
<h3>Prerequisites</h3>
To run this FastAPI application, ensure you have the following installed:
- Python 3.7+
- FastAPI
- SQLAlchemy
- Pydantic
- Uvicorn
- CORS Middleware

<h3>Installation</h3>
1. Clone the repository:

```bash
git clone https://github.com/TshiamoTodd/fastapi-backend.git
cd fastapi-backend
```

2. Install dependancies:

```bash
pip install -r requirements.txt
```

3. Run the application:

```bash
uvicorn main:app --reload
```

<h3>Directory Structure</h3>


## Middleware

<h3>CORS Middleware</h3>
The application uses the CORSMiddleware to handle Cross-Origin Resource Sharing (CORS). This is necessary to allow frontend applications hosted on different origins to communicate with the API.

- Allowed Origins: `http://localhost:3000`
- Allowed Methods: All (`GET`, `POST`, `PUT`, `DELETE`, etc.)
- Allowed Headers: All
- Allow Credentials: True

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=['http://localhost:3000'],
    allow_credentials=True,
    allow_methods=['*'],
    allow_headers=['*'],
)
```

## Routes
<h3>Health Check</h3>

**Endpoint:** `GET /`
This endpoint is used to verify that the application is running and healthy.

**Response:**
- `200 OK`: Returns the message `Health check complete`

```python
@app.get("/")
def health_check():
    return 'Health check complete'
```

<h3>Authentication Routes</h3>

**Router:** `auth.router`
The authentication router is responsible for managing user authentication operations such as registration, login, and token management.

```python
app.include_router(auth.router)
```

<h3>Workout Routes</h3>

**Router:** `workouts.router`
The workouts router handles all operations related to managing workout routines and exercises.

```python
app.include_router(workouts.router)
```

<h3>Routine Routes</h3>

**Router:** `routine.router`
The routines router manages user-specific workout routines, including creation, modification, and deletion of routines.

```python
app.include_router(routines.router)
```

## Database Configuration
The application uses SQLAlchemy for ORM (Object-Relational Mapping) with a SQLite database. The database models are created and managed using SQLAlchemy's `Base` class.

- Database Engine: The database connection is managed by the SQLAlchemy `engine`, which is bound to the `Base` metadata for model creation.

```python
from .database import Base, engine

Base.metadata.create_all(bind=engine)
```

Ensure that the database connection settings are correctly configured in your environment for the application to function properly.

## Conclusion
This FastAPI application provides a robust structure for managing user authentication, workouts, and routines. The documentation provides a basic understanding of how to set up, run, and interact with the API. For more advanced configurations and additional features, refer to the FastAPI and SQLAlchemy documentation.





