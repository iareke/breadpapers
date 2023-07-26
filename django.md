[//]: # "Title: django"
[//]: # "Author: Fabio Iareke"
[//]: # "Date: 2023-07-26"
[//]: # "File: django.txt"
[//]: # "Summary: django guidelines, best practices"

# django

## directory structure

- project_name/
  - apps/
    - app_name/
  - setup/
    - static/
      - css
      - js
      - img
  - templates/
    - share/ (other?)
      - partials/
  - static/ (opt, collectstatic generated)
  - media/ (opt, on 1st upload generated)

todo: verify official

## best practices

- PEPs
- Use **setup** for the name of the project when creating a new project via `django-admin`
- Use `requirements.txt` for the Configuration Management of the components
- Use `.env` (**python-dotenv**) or environment variables for secret information, credentials

## tips

`setup/settings.py`

```
ALLOWED_HOSTS = ['*']
```

```
LANGUAGE_CODE = 'en-us'
```

```
TIMEZONE = 'America/Sao_Paulo'
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

- Show **python** version

```
pi@rpi4:~/Documents/django/tst $ python3 -V

Python 3.9.2
```

- Create **venv**

```
pi@rpi4:~/Documents/django/tst $ python3 -m venv venv
```

- Activate **venv**

```
pi@rpi4:~/Documents/django/tst $ source venv/bin/activate

(venv) pi@rpi4:~/Documents/django/tst $
```

- Deactivate **venv**

```
(venv) pi@rpi4:~/Documents/django/tst $ deactivate

pi@rpi4:~/Documents/django/tst $
```

- Show **venv**'s python version

```
(venv) pi@rpi4:~/Documents/django/tst $ python -V

Python 3.9.2
```

- Show **pip** version

```
(venv) pi@rpi4:~/Documents/django/tst $ pip --version

pip 20.3.4 from /home/pi/Documents/django/tst/venv/lib/python3.9/site-packages/pip (python 3.9)
```

- Upgrade **pip**

```
(venv) pi@rpi4:~/Documents/django/tst $ pip install --upgrade pip

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

- List packages (**pip**)

```
(venv) pi@rpi4:~/Documents/django/tst $ pip list
Package       Version
------------- -------
pip           23.2.1
pkg_resources 0.0.0
setuptools    44.1.1
```

- Uninstall package (**pip**)

```
(venv) pi@rpi4:~/Documents/django/tst $ pip uninstall pkg_resources

Found existing installation: pkg_resources 0.0.0
Uninstalling pkg_resources-0.0.0:
  Would remove:
    /home/pi/Documents/django/tst/venv/lib/python3.9/site-packages/pkg_resources-0.0.0.dist-info/*
    /home/pi/Documents/django/tst/venv/lib/python3.9/site-packages/pkg_resources/*
Proceed (Y/n)? Y
  Successfully uninstalled pkg_resources-0.0.0
```

- Install Django

```
(venv) pi@rpi4:~/Documents/django/tst $ pip install django
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

- Init the project (startproject)

```
(venv) pi@rpi4:~/Documents/django/tst $ django-admin startproject setup .
```

Hint: using **setup** for the name of the project

- Start the server

```
(venv) pi@rpi4:/tmp/tst $ python manage.py runserver 0.0.0.0:8000
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

July 26, 2023 - 19:51:26
Django version 4.2.3, using settings 'setup.settings'
Starting development server at http://0.0.0.0:8000/
Quit the server with CONTROL-C.
```

Note: default starts on 127.0.0.1:8000

Hint: first modify `setup/settings.py` and add the value **'*'** to the **ALLOWED_HOSTS = []** option to allow external connections.

`setup/settings.py`

```
ALLOWED_HOSTS = ['*']
```

- Init app (startapp)

```
(venv) pi@rpi4:~/Documents/django/tst $ python manage.py startapp appx
```

Hint: templates


# misc

**venv**

```
pi@rpi4:~/Documents/django/tst $ tree
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
pi@rpi4:~/Documents/django/tst $ tree 
.
├── manage.py
├── setup
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
```

**startapp**

```
(venv) pi@rpi4:~/Documents/django/tst $ tree
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

Note: after `mkdir apps ; mv appx apps/`

