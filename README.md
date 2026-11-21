# MCA Semester I - Practical 9: FastAPI CRUD Application with SQLite Persistence
**Course:** Python & Relational Programming  
**Student:** Sahil Surendra Shirke  

## Overview
Built a full CRUD REST API using **FastAPI**, **Pydantic**, and **SQLite** (`sqlite3`) with automatic database initialization via FastAPI `lifespan` events and dependency-injected database sessions (`Depends(get_db)`).

## Files Included
- `init_db.py` — Standalone SQLite script that initializes `students.db` and creates the `students` table with `UNIQUE` and `CHECK(marks >= 0 AND marks <= 100)` constraints.
- `main.py` — FastAPI application implementing full CRUD endpoints (`POST`, `GET`, `PUT`, `DELETE`) with parameterized SQL queries and `sqlite3.IntegrityError` handling.

## Implemented Endpoints
- `GET /` — Health check confirming the FastAPI SQLite application is running
- `POST /students` — Inserts a new validated student record into SQLite (`400` on duplicate roll number)
- `GET /students` — Fetches all student records from the database
- `GET /students/{student_id}` — Fetches a single student by ID (`404` if not found)
- `PUT /students/{student_id}` — Updates an existing student record (`404` if not found, `400` on duplicate roll number)
- `DELETE /students/{student_id}` — Deletes a student record by ID (`404` if not found)

## How to Run
    python3 init_db.py
    uvicorn main:app --reload
