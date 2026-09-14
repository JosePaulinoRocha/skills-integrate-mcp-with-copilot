# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher-only signup and unregister actions
- Teacher login with credentials stored in `teachers.json`
- Public activity browsing without login

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| GET    | `/auth/login`                                                      | Verify teacher credentials using HTTP Basic authentication           |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Teacher-only signup for an activity                                |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Teacher-only unregister action                                    |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

Activity data is currently stored in memory, which means it will be reset when
the server restarts. Teacher credentials are loaded from `teachers.json`.

The sample development credential is `teacher` / `mergington-teacher`; replace
it before deploying outside local development.
