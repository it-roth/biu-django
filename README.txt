# My Project

Django REST Framework Backend + Vue.js Frontend

## 1. Project Structure

```text
my-project/
├── backend/
│   ├── manage.py
│   ├── requirements.txt
│   ├── config/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── asgi.py
│   │   └── wsgi.py
│   └── api/
│       ├── migrations/
│       ├── admin.py
│       ├── apps.py
│       ├── models.py
│       ├── serializers.py
│       ├── tests.py
│       ├── urls.py
│       └── views.py
│
├── frontend/
│   ├── src/
│   │   ├── App.vue
│   │   ├── main.js
│   │   └── components/
│   ├── public/
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

## 2. Requirements

Install these before starting:

- Python
- Node.js and npm
- Visual Studio Code (recommended)

## 3. Backend Setup (Django)

Open a terminal in the project root.

Create the backend folder and Django project if they do not exist:

```bash
mkdir backend
cd backend
python -m venv .venv
```

Activate the virtual environment.

**Windows PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

Install dependencies separately:

```bash
pip install django
pip install djangorestframework
pip install django-cors-headers
```

Create the Django project and app only once:

```bash
django-admin startproject config .
python manage.py startapp api
```

### Run Backend

```bash
python manage.py migrate
python manage.py runserver
```

Backend URL: http://127.0.0.1:8000

## 4. Backend Files to Edit

| File | Purpose |
|---|---|
| `config/settings.py` | Configure installed apps, database, middleware, and CORS |
| `config/urls.py` | Connect application URLs to the main project |
| `api/models.py` | Define database models and tables |
| `api/serializers.py` | Convert model data to and from JSON |
| `api/views.py` | Implement API logic and CRUD operations |
| `api/urls.py` | Define API endpoints |
| `api/admin.py` | Register models in Django Admin |
| `api/tests.py` | Write automated tests |
| `manage.py` | Run Django management commands |

**Note:** Create `api/serializers.py` and `api/urls.py` if they do not exist.

## 5. Frontend Setup (Vue.js + Vite)

From the project root, create the frontend only if it does not already exist:

```bash
npm create vite@latest frontend -- --template vue
```

Install dependencies:

```bash
cd frontend
npm install
```

### Run Frontend

```bash
npm run dev
```

Frontend URL: http://localhost:5173

## 6. Frontend Files to Edit

| File | Purpose |
|---|---|
| `src/App.vue` | Main Vue page and UI |
| `src/main.js` | Initialize the Vue application |
| `src/components/` | Reusable UI components |
| `package.json` | Frontend dependencies and scripts |
| `vite.config.js` | Configure Vite development server |

## 7. Connect Frontend to Backend

Example API URL:

```javascript
const API_URL = "http://127.0.0.1:8000/api/";
```

Use `fetch()` or Axios in Vue components to request data from Django.

Allow the frontend origin in `config/settings.py`:

```python
CORS_ALLOWED_ORIGINS = [
    "http://localhost:5173",
]
```

Also add `"rest_framework"`, `"corsheaders"`, and `"api"` to `INSTALLED_APPS`, and add `"corsheaders.middleware.CorsMiddleware"` near the top of `MIDDLEWARE`.

## 8. Local URLs

- Frontend: http://localhost:5173
- Backend API: http://127.0.0.1:8000/api/
- Django Admin: http://127.0.0.1:8000/admin/

Create an admin account with:

```bash
python manage.py createsuperuser
```

## 9. Important Notes

- Run backend commands from the `backend/` directory.
- Run frontend commands from the `frontend/` directory.
- Start the backend and frontend in separate terminals.
- Run project creation commands only once.
- Django uses SQLite by default unless you configure another database.
- Configure authentication, permissions, and production security before deployment.
