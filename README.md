# Notes Manager API

A RESTful API for managing personal notes with JWT authentication, built with Django REST Framework.

---

## Live Demo

**Base URL:** https://notes-manager-api-3hd6.onrender.com

> Note: Free tier — may take 50 seconds to wake up on first request.

---

## Tech Stack

- Python
- Django 6.0
- Django REST Framework
- Simple JWT (JSON Web Token Authentication)
- SQLite
- Whitenoise (static files)
- Gunicorn
- Render (deployment)

---

## API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/token/ | Get access + refresh token |
| POST | /api/token/refresh/ | Refresh access token |

### Notes (JWT required)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/notes/ | List all notes |
| POST | /api/notes/ | Create a note |
| GET | /api/notes/{id}/ | Get a note |
| PUT | /api/notes/{id}/ | Update a note |
| DELETE | /api/notes/{id}/ | Delete a note |

---

## Local Setup

\\\ash
git clone https://github.com/Sudipta7-ops/notes-manager-api.git
cd notes-manager-api
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
\\\

---

## Author

**Sudipta Barik** — [LinkedIn](https://linkedin.com/in/sudipta-barik) | [GitHub](https://github.com/Sudipta7-ops)
