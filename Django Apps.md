# Django Apps

Django apps are like modules where add a sub app to project like User, Product, ...

To create a Django App use this command `python manage.py startapp first_app`

After create an app you need to add this app to app list in `settings.py`:

Recommended way:
```python
INSTALLED_APPS = [
    ...,
    'first_app.apps.FirstAppConfig',
]
```
Another way:
```python
INSTALLED_APPS = [
    ...,
    'first_app',
]
```


### Models.py
This file is use for Django models and data structure that most be store in database

```python
from django.db import models

class Person(models.Model):
    name = models.CharField(max_length=70)
    age = models.IntegerField()
    country = models.CharField(max_length=50)
```

### Views.py
This file is a collection of classes and function that it's responsible for connecting users, models and store data, Also every function or class as view that wrote in this file must be link to an address in urls.py file, so that users can acces them

In `urls.py`, import you view and make a path for that view:
```python
from django.contrib import admin
from django.urls import path

from first_app.views import signup_view

urlpatterns = [
    path('admin/', admin.site.urls),
    path('signup/', signup_view),
]
```

In `views.py`:
```python
from django.shortcuts import HttpResponse

def signup_view(request):
    return HttpResponse('Signup Completed!')
```

### Migrations Directory
This folder contains migration files and to make a migration we use this command `python manage.py makemigrations {app_name}`
Note: if we leave `app_name` empty, this command will run for every apps in project!

To run migration we use this command `python manage.py migrate {app_name}` Also as before command if you run if without `app_name` it will run for all apps!


### apps.py
This file contains informain and settings for the app.

### admin.py
This file is use for Django admin features

### tests.py
This file use for unittest and testing app functionallities
