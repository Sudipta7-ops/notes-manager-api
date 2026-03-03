# Notes Manager API

A RESTful Notes Management API built using Django and Django REST Framework with JWT Authentication.

This project demonstrates backend API development including authentication, CRUD operations, and clean project architecture.

---

## Overview
This API is built as a backend portfolio project to demonstrate production-ready REST architecture.

The API allows users to:

- Register and authenticate using JWT
- Create notes
- Retrieve all notes
- Retrieve a single note
- Update notes
- Delete notes

Authentication is handled using JSON Web Tokens (JWT).

---

## Tech Stack

- Python
- Django
- Django REST Framework
- Simple JWT
- SQLite (default Django database)

---

## Features

- User authentication with JWT
- Token-based protected routes
- Create note
- Retrieve all notes
- Retrieve note by ID
- Update note
- Delete note
- Serializer-based validation
- RESTful API design

---

## Project Structure

notes-manager-api/

│  
├── notes/              # Notes app  
├── notes_api/          # Project configuration  
├── manage.py  
└── README.md  

---

## Requirements

- Python 3.10+
- pip
- virtual environment (recommended)

## Installation

1. Clone the repository

```
git clone https://github.com/Sudipta7-ops/notes-manager-api.git
cd notes-manager-api
```   

3. Create virtual environment
```
python -m venv venv  
```
3. Activate virtual environment

Windows:  
```
venv\Scripts\activate  
```
Mac/Linux: 
```
source venv/bin/activate
``` 

4. Install dependencies
```
pip install -r requirements.txt
```

5. Run migrations
```
python manage.py migrate  
```
6. Start server
```
python manage.py runserver  
```
---

## Authentication

Obtain access and refresh tokens:

POST /api/token/
POST /api/token/refresh/

After obtaining the access token, include it in the request header:

Authorization: Bearer <your_access_token>

---

## API Endpoints

Notes:

- GET /notes/
- POST /notes/
- GET /notes/<id>/
- PUT /notes/<id>/
- DELETE /notes/<id>/

---

## Example Note Request Body
```
{
  "title": "My First Note",
  "content": "This is a sample note."
}
```
---

## Learning Outcomes

- JWT Authentication implementation
- DRF ViewSets and Serializers
- Protected API routes
- Django project structuring
- Database migrations
- Backend API design principles

---

## Future Improvements

- Pagination
- Filtering and search
- Role-based permissions
- Docker support
- Cloud deployment
