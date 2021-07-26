# Django REST Framework & Docker
Docker :  way to isolate and run entire applications. The entire development environment is isolated: programming language, software packages, databases, and more. production environment locally;can be shared among team members so everyone is working on the same setup.

## Linux Containers
How could multiple programmers use the same single machine? The answer was virtualization and specifically virtual machines which are complete copies of a computer system from the operating system on up.
Docker:  A way to implement Linux containers!

## Containers vs Virtual Environments
Virtual environments are used to isolate Python software packages locally. virtual environments can only isolate Python packages, They still rely on a global, system-level installation of Python albeit they can refer to the proper version.

## Install Docker
## Hello, World
```
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```
## Images and Containers
Images and containers are the two fundamental concepts to grasp when you start with Docker. An image is a snapshot in time of what a project contains. A container is a running instance of the image.

There are a large number of official images available on Docker Hub for common software like different flavors of Linux, programming languages, and so on. For example, the Hello World image is there.

## Images
create our own image for something more “real.”
1. create a local directory on your computer for our code
```
$ cd ~/Desktop
$ mkdir code && cd code
$ mkdir python3.7 && cd python3.7
```
2. `$ touch Dockerfile`
3. With your text editor add the following single line of code to the Dockerfile.
`FROM python:3.7-alpine`
> Dockerfiles are read from top-to-bottom. 
## Image Builds
> Don’t forget that period . at the end of the command!
```
$ docker image build .
Sending build context to Docker daemon  2.048kB
Step 1/1 : FROM python:3.7-alpine
3.7-alpine: Pulling from library/python
c9b1b535fdd9: Pull complete
2cc5ad85d9ab: Pull complete
53a2fca3c2ea: Pull complete
30fce49de8b1: Pull complete
49bcb9571cc7: Pull complete
Digest: sha256:7655eea15dfd981eeb7d243af21e8561e967709caba938d50b136cdb992f3546
Status: Downloaded newer image for python:3.7-alpine
 ---> b2c276538711
Successfully built b2c276538711
```
  
# Django for APIs - Library Website
## Library Website and API

In this chapter we will review the similarities and differences between traditional Django and Django REST Framework. The most important takeaway is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

### Traditional Django
steps : 
```
$ mkdir library && cd library
$ pipenv install django~=3.1.0
$ pipenv shell
(library) $
```
> Don’t forget to include the period . at the end which installs the code in our current directory. If you do not include the period, Django will create an additional directory by default.
`(library) $ django-admin startproject config .`
> __init__.py is a Python way to treat a directory as a package; it is empty
> asgi.py stands for Asynchronous Server Gateway Interface and is a new option in Django 3.0+
> settings.py contains all the configuration for our project
> urls.py controls the top-level URL routes
> wsgi.py stands for Web Server Gateway Interface and helps Django serve the eventual web pages
> manage.py executes various Django commands such as running the local web server or creating a new app.

```
(library) $ python manage.py migrate
(library) $ python manage.py runserver
```
`python manage.py startapp books`

> admin.py is a configuration file for the built-in Django Admin app
> apps.py is a configuration file for the app itself
> the migrations/ directory stores migrations files for database changes
> models.py is where we define our database models
> tests.py is for our app-specific tests
> views.py is where we handle the request/response logic for our web app
> Typically developers will also create an urls.py file within each app too for routing.

'''
library_project/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # Local
    'books', # new
]
'''
`(library) $ python manage.py migrate`
## Models
```
# books/models.py
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=250)
    subtitle = models.CharField(max_length=250)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)

    def __str__(self):
        return self.title
```
Since we created a new database model we need to create a migration file to go along with it, then update our database.

```
(library) $ python manage.py makemigrations books
(library) $ python manage.py migrate
```
## Admin
```
(library) $ python manage.py createsuperuser
```
```
# books/admin.py
from django.contrib import admin
from .models import Book

admin.site.register(Book)
```
```
# books/views.py
from django.views.generic import ListView
from .models import Book


class BookListView(ListView):
    model = Book
    template_name = 'book_list.html'
```
### URLs
We need to set up both the project-level urls.py file and then one within the books app. When a user visits our site they will first interact with the config/urls.py file so let’s configure that first. Add the include import on the second line and then a new path for our books app.

```
# config/urls.py
from django.contrib import admin
from django.urls import path, include # new

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('books.urls')), # new
]
```
`(library) $ touch books/urls.py`
```
# books/urls.py
from django.urls import path

from .views import BookListView

urlpatterns = [
    path('', BookListView.as_view()),
]
```
```
(library) $ mkdir books/templates
(library) $ mkdir books/templates/books
(library) $ touch books/templates/books/book_list.html
```
```
<!-- books/templates/books/book_list.html -->
<h1>All books</h1>
{% for book in object_list %}
  <ul>
    <li>Title: {{ book.title }}</li>
    <li>Subtitle: {{ book.subtitle }}</li>
    <li>Author: {{ book.author }}</li>
    <li>ISBN: {{ book.isbn }}</li>
  </ul>
{% endfor %}
```
### Webpage
`(library) $ python manage.py runserver`
## Django REST Framework
Django REST Framework is added just like any other third-party app.
1. 
`(library) $ pipenv install djangorestframework~=3.11.0`
1. Add it to the INSTALLED_APPS config in our settings.py file.
```
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework', # new

    # Local
    'books',
]
```
There are multiple ways we can organize these files however my preferred approach is to create a dedicated api app. That way even if we add more apps in the future, each app can contain the models, views, templates, and urls needed for dedicated webpages, but all API-specific files for the entire project will live in a dedicated api app.

1. Let’s first create a new api app.

`(library) $ python manage.py startapp api`
1. add it to INSTALLED_APPS.
```
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework',

    # Local
    'books',
    'api', # new
]
```
#### URLs
5.
```
# config/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('api.urls')), # new
    path('', include('books.urls')),
]
```
`(library) $ touch api/urls.py`
update  : 
```
# api/urls.py
from django.urls import path
from .views import BookAPIView

urlpatterns = [
    path('', BookAPIView.as_view()),
]
```
#### Views
```
# api/views.py
from rest_framework import generics

from books.models import Book
from .serializers import BookSerializer


class BookAPIView(generics.ListAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializ
```
#### Serializers
A serializer translates data into a format that is easy to consume over the internet, typically JSON, and is displayed at an API endpoint
Make a serializers.py file within our api app.

`(library) $ touch api/serializers.py`

Then update it as follows in a text editor.

```
# api/serializers.py
from rest_framework import serializers

from books.models import Book


class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = ('title', 'subtitle', 'author', 'isbn')
```
#### cURL

`(library) $ python manage.py runserver`
We can use the popular cURL program to execute HTTP requests via the command line. All we need for a basic GET request it to specify curl and the URL we want to call.
run in terminal 
```
$ curl http://127.0.0.1:8000/api/
[  
   {  
      "title":"Django for Beginners",
      "subtitle":"Build websites with Python and Django",
      "author":"William S. Vincent",
      "isbn":"978-198317266"
   }
]
```

#### Browsable API

http://127.0.0.1:8000/api/  

Resources : 
* [Beginner’s Guide to Docker](https://wsvincent.com/beginners-guide-to-docker/)
* [Django for APIs - Library Website](https://djangoforapis.com/library-website-and-api/)