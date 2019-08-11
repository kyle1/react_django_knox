# React/Django/Redux/REST template with Knox

## About
This is a project template for a React/Django/Redux/REST web app using Knox token authentication. The template includes a login page, a user registration page, and a main dashboard page. The template and instructions were created primarily for personal use but may help others get started.

## Get started
```bash
git clone https://github.com/kyleoverstreet/react_django_knox.git
```

**Rename the following directories:**
* react_django_knox
* react_django_knox/projectname
* react_django_knox/projectname/appname
* react_django_knox/projectname/frontend/src/components/appname
* react_django_knox/projectname/projectname
    
**Edit the following files:**

react_django_knox/package.json
```json
"scripts": {
  "dev": "webpack --mode development ./projectname/frontend/src/index.js --output ./projectname/frontend/static/frontend/main.js",
  "build": "webpack --mode production ./projectname/frontend/src/index.js --output ./projectname/frontend/static/frontend/main.js"
},
```

react_django_knox/projectname/manage.py
```python
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'projectname.settings')
```

react_django_knox/projectname/projectname/settings.py
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    ...
    'appname'
]
```

```python
ROOT_URLCONF = ‘projectname.urls’
```

```python
WSGI_APPLICATION = ‘projectname.wsgi.application’
```

```python
DATABASES = {
    # 'default': {
    #     'ENGINE': 'django.db.backends.sqlite3',
    #     'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    # }
    'default': {
        'ENGINE': 'sql_server.pyodbc',
        'NAME': 'dbname',
        'HOST': 'KYLE-PC\SQLEXPRESS',
        'OPTIONS': {
            'driver': 'ODBC Driver 17 for SQL Server'
        }
    }
}
```

react_django_knox/projectname/projectname/settings.py
```python
urlpatterns = [
    path('', include('accounts.urls')),
    path('', include('frontend.urls')),
    path('', include('appname.urls'))
]
```

react_django_knox/projectname/wsgi.py
```python
os.environ.setdefault(“DJANGO_SETTINGS_MODULE”, “projectname.settings”)
```

react_django_knox/projectname/appname/apps.py
```python
class AppnameConfig(AppConfig):
    name = 'appname'
```

react_django_knox/projectname/frontend/src/components/App.Js
```javascript
import Dashboard from "./appname/Dashboard";
```


**Install dependencies with the the following commands:**

```bash
pipenv shell
pipenv install
npm install
```
(Note: I use django-pyodb-azure to connect to a local SQL Server database. This can be removed from the Pipfile otherwise)

**Start the server and build the project:**

```bash
python projectname/manage.py runserver
npm run dev
```

Your web app will now be running on localhost:8000.

## Credits
This template uses code from Brad Traversy's "Full Stack React & Django" video series on YouTube.

**Video series:** https://www.youtube.com/playlist?list=PLillGF-RfqbbRA-CIUxlxkUpbq0IFkX60

**Code:** https://github.com/bradtraversy/lead_manager_react_django








