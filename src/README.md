# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities
- View activities and participants without signing in
- Sign in as a teacher to register or unregister students

Teacher passwords are supplied through `TEACHER_CREDENTIALS` and are never stored in the source tree. Set `COOKIE_SECURE=true` when serving the app over HTTPS.

## Getting Started

1. Configure teacher credentials in the environment. Use a JSON object mapping teacher usernames to passwords; do not commit real credentials to the repository.

   ```
   export TEACHER_CREDENTIALS='{"teacher1":"replace-with-a-strong-password"}'
   ```

2. Install the dependencies:

   ```
   pip install -r ../requirements.txt
   ```

3. Run the application from this directory:

   ```
   uvicorn app:app --reload
   ```

4. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity                                             |

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

All data is stored in memory, which means data will be reset when the server restarts.
