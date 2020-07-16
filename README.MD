Django using MySQL


#### Project setup

- Launch VS Code adn then open terminal window

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
