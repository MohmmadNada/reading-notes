# Readings: Django Custom User

## Django Best Practices: Custom User Model
### Setup
create  Django project from the **command line**: 
first : 
```
$ cd ~/Desktop
$ mkdir accounts && cd accounts
$ pipenv install django~=3.1.0
$ pipenv shell
(accounts) $ django-admin.py startproject config .
(accounts) $ python manage.py startapp accounts
(accounts) $ python manage.py runserver
```

> Note that we did not run migrate to configure our database. It's important to wait until after we've created our new custom user model before doing so.

### AbstractUser vs AbstractBaseUser
create a custom user model ways : 
1. AbstractUser (easy way )


2. AbstractBaseUser

#### Custom User Model
requires four steps:
1. update config/settings.py
   1. Within INSTALLED_APPS add accounts at the bottom. 
   2. at the bottom of the entire file, add the AUTH_USER_MODEL config.
2. create a new CustomUser model
    ```
    # accounts/models.py
    from django.contrib.auth.models import AbstractUser
    from django.db import models

    class CustomUser(AbstractUser):
        pass
        # add additional fields in here

        def __str__(self):
            return self.username
    ```

3. create new UserCreation and UserChangeForm
   1. run `(accounts) $ touch accounts/forms.py`
   2. We'll update it with the following code to largely subclass the existing forms.

    ```
    # accounts/forms.py
    from django import forms
    from django.contrib.auth.forms import UserCreationForm, UserChangeForm
    from .models import CustomUser

    class CustomUserCreationForm(UserCreationForm):

        class Meta:
            model = CustomUser
            fields = ('username', 'email')

    class CustomUserChangeForm(UserChangeForm):

        class Meta:
            model = CustomUser
            fields = ('username', 'email')
    ```
4. update the admin

```
    # accounts/admin.py
    from django.contrib import admin
    from django.contrib.auth.admin import UserAdmin

    from .forms import CustomUserCreationForm, CustomUserChangeForm
    from .models import CustomUser

    class CustomUserAdmin(UserAdmin):
        add_form = CustomUserCreationForm
        form = CustomUserChangeForm
        model = CustomUser
        list_display = ['email', 'username',]

    admin.site.register(CustomUser, CustomUserAdmin)
```

now , run 
``` (accounts) $ python manage.py makemigrations accounts
(accounts) $ python manage.py migrate 
```
##### Superuser
```
(accounts) $ python manage.py createsuperuser
```
##### Templates/Views/URLs
Start by updating settings.py to use a project-level templates directory.
```
# config/settings.py
TEMPLATES = [
    {
        ...
        'DIRS': [str(BASE_DIR.joinpath('templates'))], # new
        ...
    },
]
```
set the redirect links for log in and log out, which will both go to our home templat
```
# config/settings.py
LOGIN_REDIRECT_URL = 'home'
LOGOUT_REDIRECT_URL = 'home'
```
Create a new project-level templates folder and within it a registration folder as that's where Django will look for the log in template. We will also put our signup.html template in there.
```
(accounts) $ mkdir templates
(accounts) $ mkdir templates/registration
```
Then create four templates:

```
(accounts) $ touch templates/registration/login.html
(accounts) $ touch templates/registration/signup.html
(accounts) $ touch templates/base.html
(accounts) $ touch templates/home.html
```
Update the files as follows:

```
<!-- templates/base.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>{% block title %}Django Auth Tutorial{% endblock %}</title>
</head>
<body>
  <main>
    {% block content %}
    {% endblock %}
  </main>
</body>
</html>
```
```
<!-- templates/home.html -->
{% extends 'base.html' %}

{% block title %}Home{% endblock %}

{% block content %}
{% if user.is_authenticated %}
  Hi {{ user.username }}!
  <p><a href="{% url 'logout' %}">Log Out</a></p>
{% else %}
  <p>You are not logged in</p>
  <a href="{% url 'login' %}">Log In</a> |
  <a href="{% url 'signup' %}">Sign Up</a>
{% endif %}
{% endblock %}
```
```
<!-- templates/registration/login.html -->
{% extends 'base.html' %}

{% block title %}Log In{% endblock %}

{% block content %}
<h2>Log In</h2>
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Log In</button>
</form>
{% endblock %}
```
```
<!-- templates/registration/signup.html -->
{% extends 'base.html' %}

{% block title %}Sign Up{% endblock %}

{% block content %}
<h2>Sign Up</h2>
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Sign Up</button>
</form>
{% endblock %}
```
Now for our urls.py files at the project and app level.


```
# config/urls.py
from django.contrib import admin
from django.urls import path, include
from django.views.generic.base import TemplateView

urlpatterns = [
    path('', TemplateView.as_view(template_name='home.html'), name='home'),
    path('admin/', admin.site.urls),
    path('accounts/', include('accounts.urls')),
    path('accounts/', include('django.contrib.auth.urls')),
]
```
Create a urls.py file in the accounts app.

```
(accounts) $ touch accounts/urls.py
```
```
# accounts/urls.py
from django.urls import path
from .views import SignUpView

urlpatterns = [
    path('signup/', SignUpView.as_view(), name='signup'),
]
```
Last step is our views.py file in the accounts app which will contain our signup form.

```
# accounts/views.py
from django.urls import reverse_lazy
from django.views.generic.edit import CreateView

from .forms import CustomUserCreationForm

class SignUpView(CreateView):
    form_class = CustomUserCreationForm
    success_url = reverse_lazy('login')
    template_name = 'registration/signup.html'
```
now Ruuuuuuuuuuuuuun
```
python manage.py runserver
```

Resources:
* [Django Custum User Model](https://learndjango.com/tutorials/django-custom-user-model)
* [DjangoX](https://github.com/wsvincent/djangox)
* [Creating a Custom User Moel](https://www.youtube.com/watch?v=eCeRC7E8Z7Y&t=59s)
* [Abstract User, User Profile and Signals in Django](https://www.youtube.com/watch?v=EudKs1HPUfE)
* [Substituting a custom User model](https://docs.djangoproject.com/en/3.0/topics/auth/customizing/#auth-custom-user)