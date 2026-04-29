# Notes API - Django REST API

A Django REST Framework API for managing notes.

## Local Setup

### 1. Create Virtual Environment
```bash
python -m venv venv
```

### 2. Activate Virtual Environment

**Windows (PowerShell):**
```powershell
.\venv\Scripts\Activate.ps1
```

**Windows (Command Prompt):**
```cmd
venv\Scripts\activate.bat
```

**Mac/Linux:**
```bash
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Create .env File
Copy `.env.example` to `.env` and update with your local values:
```bash
cp .env.example .env
```

### 5. Run Migrations
```bash
python manage.py migrate
```

### 6. Create Superuser (Optional)
```bash
python manage.py createsuperuser
```

### 7. Run Development Server
```bash
python manage.py runserver
```

Server runs at: `http://localhost:8000`

## Deployment to Render

### Prerequisites
- GitHub account with the repository pushed
- Render account (free tier available at https://render.com)

### Step 1: Connect GitHub Repository
1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click "New +" → "Web Service"
3. Connect your GitHub account and select this repository

### Step 2: Configure Service
- **Name:** notes-api (or your preferred name)
- **Environment:** Python 3
- **Build Command:** `bash build.sh`
- **Start Command:** `gunicorn notes_api.wsgi`
- **Plan:** Free (or paid if needed)

### Step 3: Add Environment Variables
Set these in Render Dashboard (Settings → Environment):

```
DEBUG=false
SECRET_KEY=your-very-secret-key-here
DB_ENGINE=postgresql
DB_NAME=notes_db
DB_USER=notes_user
DB_PASSWORD=your-db-password
ALLOWED_HOSTS=your-app-name.onrender.com
CORS_ALLOWED_ORIGINS=https://your-frontend-domain.com
CSRF_TRUSTED_ORIGINS=https://your-frontend-domain.com
PYTHON_VERSION=3.11
```

### Step 4: Create PostgreSQL Database
1. In Render Dashboard, click "New +" → "PostgreSQL"
2. Choose a name (e.g., `notes-db`)
3. Select Free plan
4. After creation, copy the connection details
5. Use these values for DB environment variables

### Step 5: Link Database to Web Service
1. Go to your Web Service settings
2. Under "Environment," add the database connection variables OR
3. Use the PostgreSQL database's connection string format

### Step 6: Deploy
1. Push to GitHub (connected to Render)
2. Render automatically deploys on push
3. Or click "Deploy" in Render Dashboard

### Environment Variables Explained

| Variable | Description |
|----------|-------------|
| `DEBUG` | Set to `false` for production |
| `SECRET_KEY` | Generate a strong secret key for Django |
| `DB_*` | PostgreSQL database connection details |
| `ALLOWED_HOSTS` | Your Render domain and any custom domains |
| `CORS_ALLOWED_ORIGINS` | Frontend URL for CORS |
| `CSRF_TRUSTED_ORIGINS` | Frontend URL for CSRF protection |

### Generate Secret Key

```python
from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())
```

Or use an online generator: https://djecrety.ir/

## API Endpoints

- Admin Panel: `/admin/`
- API Root: `/api/`

## Troubleshooting

### Migrations Not Applied
Check Render logs and ensure `build.sh` is executable:
```bash
chmod +x build.sh
```

### Static Files Not Loading
Ensure `STATIC_ROOT` is configured and run:
```bash
python manage.py collectstatic --noinput
```

### Database Connection Issues
- Verify PostgreSQL is running
- Check environment variable values
- Ensure firewall allows connection

### CORS Errors
- Add frontend URL to `CORS_ALLOWED_ORIGINS`
- Add frontend URL to `CSRF_TRUSTED_ORIGINS`

## Production Checklist

- [ ] Generate and set a strong `SECRET_KEY`
- [ ] Set `DEBUG=False`
- [ ] Configure `ALLOWED_HOSTS` with your domain
- [ ] Set up PostgreSQL database
- [ ] Configure CORS and CSRF origins
- [ ] Enable HTTPS (Render does this by default)
- [ ] Test all API endpoints
- [ ] Set up monitoring/logging
- [ ] Back up database regularly

## Files Created for Deployment

- `Procfile` - Process configuration for Render
- `build.sh` - Build script for deployment
- `render.yaml` - Render configuration (optional)
- `.env.example` - Environment variables template
- `requirements.txt` - Python dependencies

## Support

For Render documentation: https://render.com/docs
For Django documentation: https://docs.djangoproject.com/
