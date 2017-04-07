Custom Middleware for Django Redirect App
=========================================
-----------------------------------------

Default [django redirect app middleware](https://github.com/django/django/blob/master/django/contrib/redirects/middleware.py) is not support url parameters. It will throw 404 error when URL have parameters.

This custom-redirect-middleware introduced to handle url parameters. So, this custom middleware will handle all the below cases with/without trailing slash in URL.

- URL with no parameters.

- URL with one parameter.

- URL with more than one parameter.
 
### What this middleware actually do:
------------------------------------- 

- Simply separate URL parameters from `full_absolute_path`.

- Next get exact `redirect_path` of separated `full_absolute_path` form `django.contrib.redirects database`.

- Then append the URL parameters which separated from `full_absolute_path` is to `redirect_path`.

### Steps to use  [custom redirect middleware](https://github.com/s-steephan/django-custom-redirect-middleware/blob/master/custom_redirect_middleware.py) :
---------------------------------------------------------------------------------------------------------------------------

- Download custom redirect middleware [custom redirect middleware](https://raw.githubusercontent.com/s-steephan/django-custom-redirect-middleware/master/custom_redirect_middleware.py) 

- Place inside your Django app.

- Replace `'django.contrib.redirects.middleware.RedirectFallbackMiddleware'` or add bellow line in `MIDDLEWARE` of your `settings.py`.

 Note that the order of `MIDDLEWARE` matters. Generally, you can put `RedirectMiddleware` at the end of the list, because it’s a last resort. Refer [here](https://docs.djangoproject.com/en/1.10/ref/contrib/redirects/#how-it-works).

  ```
  'your_django_app_name.custom_redirect_middleware.CustomRedirectFallbackMiddleware'
  ```
Thats it.

Inspired by [this](http://stackoverflow.com/questions/43192484/djangos-redirects-app-doesnt-work-with-url-parameters/) stackoverflow question.


