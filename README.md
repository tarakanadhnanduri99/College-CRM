## College CRM (Django)

Lightweight College CRM to manage faculty profiles with photo uploads, built using Django. Includes CRUD operations, Django Admin, static/media setup, and a simple, clean UI.

### Features
- Faculty CRUD: create, list, update, delete
- Profile photo upload (stored under `media/teachers/`)
- Django Admin for back-office management
- Reusable templates and organized static assets

### Tech Stack
- Python 3.13
- Django 5.x
- SQLite (default)
- Django Templates, HTML/CSS
- Pillow (image uploads)

### Project Structure
```
crm/
  school/
    manage.py
    school/
      settings.py
      urls.py
      wsgi.py
    teachers/
      models.py
      views.py
      urls.py
    templates/
      index.html
      header.html
    static/
      css/styles.css
    media/
      teachers/
```

### Getting Started (Windows PowerShell)
1) Clone and enter the project
```
git clone <your-repo-url>
cd crm/school
```

2) Create and activate a virtual environment
```
python -m venv crmenv
crmenv\Scripts\activate
```

3) Install dependencies
```
pip install -U django pillow
```

4) Run migrations and start the server
```
python manage.py migrate
python manage.py runserver
```

5) Open the app
```
http://127.0.0.1:8000/
```

### Admin (optional)
Create a superuser and log in at `/admin/`:
```
python manage.py createsuperuser
```

### Core URLs
```
/                      -> List all faculty
/add-teacher/          -> Create faculty
/update-teacher/<id>   -> Update faculty
/delete/<id>           -> Delete faculty
/admin/                -> Django Admin
```

### Data Model
`teachers.models.Teacher`
- `name`: CharField(100)
- `subject`: CharField(100)
- `contact`: CharField(15)
- `email`: EmailField(unique=True)
- `image`: ImageField(upload_to="teachers/", blank=True, null=True)

### Static & Media
- Static files served via `STATIC_URL` and collected to `STATIC_ROOT` (local dev uses `STATICFILES_DIRS`).
- Uploaded images served via `MEDIA_URL` from `MEDIA_ROOT`. Ensure these are configured in `school/school/settings.py` and mapped in `school/school/urls.py` (already included for dev).

### Notes
- Default DB is SQLite located at `school/db.sqlite3`.
- For production, configure a real DB, static hosting, media storage, and `ALLOWED_HOSTS`.
  
### Author
Developed by Venkata Taraka Nadh Nanduri


