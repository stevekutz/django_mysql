Django using MySQL


#### Project setup

- Launch VS Code and then open terminal window

1) Set up virtual environment

    - if not installed already, run `pip install virtualenv` in terminal

    ~~~ bash
    python3 -m venv v_env
    ~~~

2) Activate the virtual environment

    - on Mac

    ~~~ bash
    source v_env/bin/activate
    ~~~

    - Windows

    ~~~ bash
    v_env\Scripts\activate.bat
    ~~~    

3) Install `Django`

~~~ bash
pip install django
~~~

4) Create project

~~~ bash
django-admin startproject sql_site
~~~

5) Test project setup

- Change into project directory
- Run the following from the virtual environment terminal

~~~ bash
python manage.py runserver
~~~

#### App Setup
1) Create `student` app within `sqy_site folder` while in virtual environment

    ~~~ bash
    django-admin startapp student
    ~~~


2) Add app to `INSTALLED_APPS` list in project's `settings.py`

    ~~~ py
    INSTALLED_APPS = [
        'settings',
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    ]
    ~~~

3) Add `Student` model in the app's `models.py` file

   - this is a class the represents a data-structure in the database

    ~~~ py
    from django.db import models

    # Create your models here.
    class Student(models.Model):
        roll_no = models.TextField()
        name = models.TextField(max_length = 40)
        stud_class = models.TextField()
        department = models.TextField()
    ~~~

#### Setup MySQL database

1) Install mysqlclient from the command line

2) Replace the `DATABASES` dict with the following:

    ~~~ py
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'dbstudent',
            'USER': 'root',
            'PASSWORD': '',
            'HOST': '',
            'PORT': '',
            'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"
            }    
        }
    }
    ~~~
3) Add `students` to INSTALLED_APPS section of `settings.py`

    ~~~ py
    INSTALLED_APPS = [
        'student',
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    ]
    ~~~

4) Install MySQL and optionally MySQL Workbench and create the `dbstudent` database under your root user

5) Install mysqlclient vi pip let Django communicate with the MySQL server

    ~~~ bash
    pip install mysqlclient
    ~~~

6) Run the first migration
    
    ~~~ bash
    python manage.py makemigrations
    python manage.py migrate
    ~~~

7) Check MySQL to verify that the table is added  
   - Note that MySQL will fully rewrite tables for almost every schema operation and generally takes a time proportional to the number of rows in the table to add or remove columns  