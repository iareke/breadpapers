[//]: # "Title: django"
[//]: # "Author: Fabio Iareke"
[//]: # "Date: 2023-07-26"
[//]: # "File: django.txt"
[//]: # "Summary: django guidelines, best practices"

# django

## directory structure

```
project_name
├── apps
│   ├── app_name
│   │   ├── fixtures
│   │   └── templates
│   │        └── app_name
│   └── default
│       └── fixtures
├── media
├── setup
│   └── static
│       ├── css
│       ├── fonts
│       ├── img
│       └── js
├── static
└── templates
    └── partials
```

## best practices

- PEPs
- Use `requirements.txt` for the Configuration Management of the components
- Use `.env` (**python-dotenv**) or environment variables for secret information, credentials
- Use a `urls.py` for each app to define paths
- Use `setup` as the name of the project

## tips

`tst/settings.py`

```
ALLOWED_HOSTS = ['*']

TIMEZONE = 'America/Sao_Paulo'

STATIC_URL = 'static/'

STATIC_ROOT = BASE_DIR / STATIC_URL

MEDIA_URL = 'media/'

STATIC_ROOT = BASE_DIR / MEDIA_URL

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates/'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

## env

- Python: 3.9.2
- Django: 4.3.2
- OS: Debian GNU/Linux 11 (bullseye)
- OS_info: Linux rpi4 6.1.21-v8+ #1642 aarch64 GNU/Linux


Note: basic requirements, **Django** + dependencies

`requirements.txt`

```
asgiref==3.7.2
Django==4.2.3
sqlparse==0.4.4
typing_extensions==4.7.1
```

## work instructions

```
PROJECT_NAME = 'tst'
APP_NAME = 'appx'
```

### Show **python** version

```
pi@rpi4:~/tst $ python3 -V

Python 3.9.2
```

### Create **venv**

```
pi@rpi4:~/tst $ python3 -m venv venv
```

### Activate **venv**

```
pi@rpi4:~/tst $ source venv/bin/activate

(venv) pi@rpi4:~/tst $
```

### Deactivate **venv**

```
(venv) pi@rpi4:~/tst $ deactivate

pi@rpi4:~/tst $
```

### Show **venv**'s python version

```
(venv) pi@rpi4:~/tst $ python -V

Python 3.9.2
```

### Show **pip** version

```
(venv) pi@rpi4:~/tst $ pip --version

pip 20.3.4 from /home/pi/tst/venv/lib/python3.9/site-packages/pip (python 3.9)
```

### Upgrade **pip**

```
(venv) pi@rpi4:~/tst $ pip install --upgrade pip

Looking in indexes: https://pypi.org/simple, https://www.piwheels.org/simple
Requirement already satisfied: pip in ./venv/lib/python3.9/site-packages (20.3.4)
Collecting pip
  Downloading https://www.piwheels.org/simple/pip/pip-23.2.1-py3-none-any.whl (2.1 MB)
     |████████████████████████████████| 2.1 MB 206 kB/s 
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 20.3.4
    Uninstalling pip-20.3.4:
      Successfully uninstalled pip-20.3.4
Successfully installed pip-23.2.1
```

### List packages (**pip**)

```
(venv) pi@rpi4:~/tst $ pip list
Package       Version
------------- -------
pip           23.2.1
pkg_resources 0.0.0
setuptools    44.1.1
```

### Uninstall package (**pip**)

```
(venv) pi@rpi4:~/tst $ pip uninstall pkg_resources

Found existing installation: pkg_resources 0.0.0
Uninstalling pkg_resources-0.0.0:
  Would remove:
    /home/pi/tst/venv/lib/python3.9/site-packages/pkg_resources-0.0.0.dist-info/*
    /home/pi/tst/venv/lib/python3.9/site-packages/pkg_resources/*
Proceed (Y/n)? Y
  Successfully uninstalled pkg_resources-0.0.0
```

### Install Django

```
(venv) pi@rpi4:~/tst $ pip install django
Looking in indexes: https://pypi.org/simple, https://www.piwheels.org/simple
Collecting django
  Downloading https://www.piwheels.org/simple/django/Django-4.2.3-py3-none-any.whl (8.0 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 8.0/8.0 MB 2.8 MB/s eta 0:00:00
Collecting asgiref<4,>=3.6.0 (from django)
  Downloading https://www.piwheels.org/simple/asgiref/asgiref-3.7.2-py3-none-any.whl (24 kB)
Collecting sqlparse>=0.3.1 (from django)
  Downloading https://www.piwheels.org/simple/sqlparse/sqlparse-0.4.4-py3-none-any.whl (41 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 41.2/41.2 kB 1.5 MB/s eta 0:00:00
Collecting typing-extensions>=4 (from asgiref<4,>=3.6.0->django)
  Downloading https://www.piwheels.org/simple/typing-extensions/typing_extensions-4.7.1-py3-none-any.whl (33 kB)
Installing collected packages: typing-extensions, sqlparse, asgiref, django
Successfully installed asgiref-3.7.2 django-4.2.3 sqlparse-0.4.4 typing-extensions-4.7.1
```

### Start the server

```
(venv) pi@rpi4:~/tst $ python manage.py runserver 0.0.0.0:8000
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

July 26, 2023 - 19:51:26
Django version 4.2.3, using settings 'setup.settings'
Starting development server at http://0.0.0.0:8000/
Quit the server with CONTROL-C.
```

Note: default starts on 127.0.0.1:8000

Hint: first modify `tst/settings.py` and add the value **'*'** to the **ALLOWED_HOSTS = []** option to allow external connections.

`tst/settings.py`

```
ALLOWED_HOSTS = ['*']
```

### Declaring the templates directory

`tst/settings.py`

```
from pathlib import Path, os

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates/')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

### Declaring [static, media] directories

```
STATIC_URL = 'static/'

STATIC_ROOT = BASE_DIR / STATIC_URL

MEDIA_URL = 'media/'

MEDIA_ROOT = BASE_DIR / MEDIA_URL
```

### Init the project (startproject)

```
(venv) pi@rpi4:~/tst $ django-admin startproject tst .
```

### Init app (startapp)

```
(venv) pi@rpi4:~/tst/apps $ django-admin startapp appx
```

Hint: templates

#### Declaring the app to the project

Include the app config (**AppxConfig**) in the **INSTALLED_APPS**:

`tst/settings.py`

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'apps.appx',
]
```

Change the name of app config from **appx** to **apps.appx**:

`apps/appx/apps.py`

```
from django.apps import AppConfig


class AppxConfig(AppConfig):
    default_auto_field = 'django.db.models.BigAutoField'
    name = 'apps.appx'
```

#### Declaring app routes (urls)

Include the app urls on **urlpatterns**

`tst/urls.py`

```
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('apps.appx.urls')),
]
```

Create the app `urls.py` file and declare the app's **urlpatterns**:

`apps/appx/urls.py`

```
from django.urls import path
from apps.appx.views import index

urlpatterns = [
    path('', index, name='index'),
]
```

Hint: path pattern { 'web': singular, 'rest': plural }

#### view index (simple)

Declare the view (**index**) and point to the respective template:

`apps/appx/views.py`

```
from django.shortcuts import render

def index(request):
    return render(request, 'appx/index.html')
```

#### template index (simple)

Create the template file `templates/appx/index.html`:

`templates/appx/index.html`

```
<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AppX</title>
</head>

<body>
    <h1>AppX</h1>
</body>

</html>
```

#### view index (passing data to template)

```
from django.shortcuts import render

def index(request):
    content = "Variable content"
    return render(request, 'appx/index.html', {'content': content})
```

#### template index (passing data to template)

```
<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AppX</title>
</head>

<body>
    <h1>{{ content }}</h1>
</body>

</html>
```

### Models

Declare models on `models.py` of app

`apps/appx/models.py`

```
from django.db import models

class ObjX(models.Model):
    name = models.CharField(max_length=255, null=False, blank=False)

    def __str__(self):
        return self.name
```

Hint: from .models (inside a app, refers respective modules)

### PostgreSQL

Note: credentials from variables

```
from pathlib import Path, os
from dotenv import load_dotenv

load_dotenv()
```

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': str(os.getenv('PG_DB_NAME')),
        'USER': str(os.getenv('PG_DB_USER')),
        'PASSWORD': str(os.getenv('PG_DB_PASSWORD')),
        'HOST': str(os.getenv('PG_DB_HOST')),
        'PORT': str(os.getenv('PG_DB_PORT')),
    }
}
```

### Create a new project

  1. create the project base directory and change path to it
  2. create venv
  3. activate venv
  4. upgrade pip (if necessary)
  5. install django
  6. create the project via django-admin
  7. create the directories
  8. basic configs

### Create a new app

  1. create the app via django-admin on the **apps** directory
  2. change the app's name in the `apps.py` to add the **apps** path
  3. create the app's `urls.py`
  4. change the app's `views.py` to declare a view
  5. create the app's templates directory
  6. create the app's template respective to de declared view
  7. change the project `settings.py to add the app
  8. change the project `urls.py` to add the app's `urls.py`



# misc

**venv**

```
pi@rpi4:~/tst $ tree
.
└── venv
    ├── bin
    │   ├── activate
    │   ├── activate.csh
    │   ├── activate.fish
    │   ├── Activate.ps1
    │   ├── easy_install
    │   ├── easy_install-3.9
    │   ├── pip
    │   ├── pip3
    │   ├── pip3.9
    │   ├── python -> python3
    │   ├── python3 -> /usr/bin/python3
    │   └── python3.9 -> python3
    ├── include
    ├── lib
    │   └── python3.9
    ├── lib64 -> lib
    ├── pyvenv.cfg
    └── share
        └── python-wheels
```

**startproject**

```
pi@rpi4:~/tst $ tree 
.
├── manage.py
├── tst
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
```

**startapp**

```
(venv) pi@rpi4:~/tst $ tree
.
├── apps
│   └── appx
│       ├── admin.py
│       ├── apps.py
│       ├── __init__.py
│       ├── migrations
│       │   └── __init__.py
│       ├── models.py
│       ├── tests.py
│       └── views.py
```

