## Medical Reminder API - README
- For this project, you'll be building an API to manage medication reminders for users, ensuring they keep track of their prescriptions and dosage schedules.
## Project Overview
![m r](https://github.com/user-attachments/assets/b919cd71-0db0-43d5-ab7f-f92662d306bb)
## In this repository
- There is a Flask application where you will be working on the backend functionality.
    - The database models are defined, and your task will involve creating routes to interact with these models.
    - There are tests included to validate your code. - - You can run them using pytest.

## Features of the API:

- Manage user profiles and their medications.
- Set up reminders for users to take their medications.
- Track medication dosage and frequency.


## Technologies Used
Backend (Flask):

    Flask: Lightweight Python web framework for building RESTful APIs.
    Flask-SQLAlchemy: ORM for database interaction.
    Flask-JWT-Extended: Token-based authentication for securing API routes.
    SQLite/PostgreSQL: Database to store user data and reminders.
    Alembic: Database migrations.
    Flask-CORS: Cross-Origin Resource Sharing to connect Flask API with React frontend.

Frontend (React):

    React: JavaScript library for building interactive user interfaces.
    React Router: For navigating between different pages in the app.
    CSS: For styling and responsive design.

## Setup

Prerequisites

    Python 3.8+
    Node.js 14+
    npm (Node Package Manager)

## Installation
## Backend Setup (Flask)

    Clone the repository:

    bash

- git clone https://github.com/stevedev-ops/phase-4-project.git
- cd stevedev-ops/phase-4-project

- Set up a virtual environment and install dependencies:

- bash

- python3 -m venv venv
- source venv/bin/activate  # On Windows: venv\Scripts\activate
- pip install -r requirements.txt

- Set up environment variables (create a .env file in the server directory):

- bash

- touch .env

- Add the following configuration to .env:

bash

- DATABASE_URI=sqlite:///reminders.db  # or use a PostgreSQL URI
- SECRET_KEY=your_secret_key
- JWT_SECRET_KEY=your_jwt_secret_key

Initialize the database:

bash

flask db init
flask db migrate
flask db upgrade

Start the Flask server:

bash

    flask run

## Frontend Setup (React)

    Navigate to the frontend directory:

    bash

cd ../client

Install the dependencies:

bash

npm install

Start the React development server:

bash

npm start


## The relationships between these models are:

  - A User can have multiple Medications and Reminders.
  - A Medication belongs to a User and can have multiple Reminders.
  - A Reminder is associated with one or more - Medications through MedicationReminder.

## Validations

    User:
        user_name and email are required.
    Medication:
        medication_name is required.
    Reminder:
        Ensures the reminder settings follow a specific schedule format.

## Routes

Set up the following routes. Make sure to return JSON data in the format specified along with the appropriate HTTP verb.

Recall you can specify fields to include or exclude when serializing a model instance to a dictionary using to_dict() (don't forget the comma if specifying a single field).

NOTE: If you choose to implement a Flask-RESTful app, you need to add code to instantiate the Api class in server/app.py.

- GET /users

- Return a list of all users:

json

[
  {
    "id": 1,
    "user_name": "John Doe",
    "email": "johndoe@example.com",
    "gender": "Male",
    "phone_number": "+123456789"
  }
]

## GET /users/

Return details of a specific user, along with their medications and reminders:

json

{
  "id": 1,
  "user_name": "John Doe",
  "email": "johndoe@example.com",
  "medications": [
    {
      "id": 1,
      "medication_name": "Aspirin",
      "dosage": "500mg",
      "frequency": "Twice a day"
    }
  ],
  "reminders": [
    {
      "id": 1,
      "reminder_time": "08:00 AM"
    }
  ]
}

## POST /users

Create a new user:

json

{
  "user_name": "Jane Smith",
  "email": "janesmith@example.com",
  "phone_number": "+987654321",
  "gender": "Female"
}

## GET /medications

Return all medications for all users:

json

[
  {
    "id": 1,
    "medication_name": "Aspirin",
    "dosage": "500mg",
    "frequency": "Twice a day",
    "user_id": 1
  }
]

## POST /medications

Add a new medication for a specific user:

json

{
  "medication_name": "Ibuprofen",
  "dosage": "200mg",
  "frequency": "Once a day",
  "user_id": 1
}

## GET /reminders

Return all reminders for all users:

json

[
  {
    "id": 1,
    "reminder_time": "08:00 AM",
    "user_id": 1
  }
]

## POST /reminders

Create a reminder for a specific medication:

json

{
  "reminder_time": "08:00 AM",
  "medication_id": 1,
  "user_id": 1
}

## PATCH /reminders/

Update the time for a specific reminder:

json

{
  "reminder_time": "09:00 AM"
}

## Testing

- Run the tests using:

- bash



