1. Create a project folder, move into the project folder, and install Django
```
mkdir <project_name>
cd <project_name>
pipenv install django
```

2. Activate the Pipenv shell
```
pipenv shell
```

3. Start a new Django project ¡DON'T FORGET THE PERIOD!
```
django-admin startproject <project_name> .
```

4. Create an application
```
python manage.py startapp <app_name>
```

5. Tell Django to use the app you created by adding it to the list of INSTALLED APPS in the `<project_name>/settings.py` file:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    '<app_name>', // newly create app name goes here
]
```

6. Django created migrations when you setup your project. It's a good idea at this point to go ahead apply those migrations. Run the following command in the terminal:
```
python manage.py migrate
```

7. Do you need a model? If yes, define your model in the `<app_name>/models.py` file. Sample code of what this may look like follows:
```
from django.db import models

class Image(models.Model):
    title = models.CharField(max_length=255)
    picture = models.URLField()
    description = models.TextField()
```

8. Did you create a model? If yes, you'll need to create models for your tables in your database.
```
// Let Django know you made some changes
python manage.py makemigrations <appname>
```

```
// Apply migrations to your database
python manage.py migrate
```
9. Do you want to setup Django admin so you can add, edit and delete model instances? If yes, you'll need to update the `<app_name>/admin.py` file. Sample code of what this may look like follows:
```
from django.contrib import admin
from .models import Image

admin.site.register(Image)
```

You also need to create a superuser. Run the following command in the termial, and follow the prompts.
```
python manage.py createsuperuser
```

9. Let's make sure everything works. Run the following command in the terminal:
```
python manage.py runserver
```

Navigate to localhost:8000.
Do you see a rocketship?

If you created a superuser, navigate to localhost:8000/admin.
Do you see a login screen?

If you answered yes to both questions, all is good.

If you answered no to either question, check your terminal and attempt to resolve your error message.
