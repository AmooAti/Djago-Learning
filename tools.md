# Useful Tools and Packages

1. [Mockaroo Website](https://www.mockaroo.com/): You can use this website to create a lot of objects with your desired fields
2. Django Debug Toolbar: This modules adds a debug toolbar to your application and you can track views, sql queries and ex.
   
   Installation:

   1. run `pip install django-debug-toolbar`
   2. edit `settings.py`:
        ```python
        INSTALLED_APPS = [
            # ...
            'debug_toolbar',
        ]
        ```
    3. add below code to rooturls in `urls.py`:
        ```python
        import debug_toolbar
        from django.urls import include, path
        # Other Imports

        urlpatterns = [
            # ...
            path('__debug__/', include(debug_toolbar.urls)),
        ]
        ```
    4. Add below Middleware in `settings.py`:
        ```python
        MIDDLEWARE = [
            'debug_toolbar.middleware.DebugToolbarMiddleware',
            # ...
        ]
        ```
    5. Add below lines at the end of `settings.py`:
        ```python
        INTERNAL_IPS = [
           '127.0.0.1',
        ]
        ```