# Django FileSystem

```
root
├── diamooati_project
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
```

1. **manage.py**: This file use for command line tool where it's a brige for developer and his/her project.
2. **amooati_project (Directory)**: Your main python package where most of infrastructure files are located here, eq. settings
3. **settings.py**: Your project settings like email, authentication, installed apps, ... are located here.
4. **urls.py**: Accessable routes are here
5. **asgi.py** and **wsgi.py**: these two files are using for webservers and we won't edit this files
6. **\_\_init\_\_.py**: It's an empty file, use for converting it's container folder to a package so that we can use all information in that package and import them, it's python capability not Django!


# Settings File
[Offical Documation for Django Settings](https://docs.djangoproject.com/en/4.1/topics/settings/)

