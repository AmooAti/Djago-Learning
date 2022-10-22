# Django Setup
## Installation
### Instal Django
1. Install Django with pip `pip install django`
2. To inssure django installed completely, run this command `django-admin --version`, you must see django version after running this command
3. To create your Django project run this command `django-admin startproject amooati_project`
4. To run your project, go to your newly created directory for you project and enter this command `python manage.py runserver`, it will run your server and give you an address like `http://127.0.0.1:8000`

## DB
By default Django is using sqlite

To run database migrations and create your schemas, use this command `python manage.py migrate`

