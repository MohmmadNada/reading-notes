# Getting started with Django
## Intro to Django
web framework for python 
### Object-relational mapper

Deﬁne your data models entirely in Python. You get a rich, dynamic database-access API for free — but you can still write SQL if needed.

### URLs and views

To design URLs for an application, you create a Python module called a URLconf. Like a table of contents for your app, it contains a simple mapping between URL patterns and your views.

### Templates
designers and front-end developers.
```
<html>
  <head>
    <title>Band Listing</title>
  </head>
  <body>
    <h1>All Bands</h1>
    <ul>
    {% for band in bands %}
      <li>
        <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
        {% if band.can_rock %}<p>This band can rock!</p>{% endif %}
      </li>
    {% endfor %}
    </ul>
  </body>
</html>
```
### Forms 

Django provides a powerful form library that handles rendering forms as HTML, validating user-submitted data, and converting that data to native Python types. Django also provides a way to generate forms from your existing models and use those forms to create and update data.

### Authentication

Django comes with a full-featured and secure authentication system. It handles user accounts, groups, permissions and cookie-based user sessions. This lets you easily build sites that allow users to create accounts and safely log in/out.

### Admin
automatic admin interface. It reads metadata in your models to provide a powerful and production-ready interface that content producers can immediately use to start managing content on your site. It’s easy to set up and provides many hooks for customization.

### Internationalization

Django offers full support for translating text into different languages, plus locale-specific formatting of dates, times, numbers, and time zones. It lets developers and template authors specify which parts of their apps should be translated or formatted for local languages and cultures, and it uses these hooks to localize Web applications for particular users according to their preferences.

### Security

Django provides multiple protections against:

Clickjacking
Cross-site scripting
Cross Site Request Forgery (CSRF)
SQL injection
Remote code execution


## How Django Works Behind the Scenes
Python-based web framework used by millions of developers and billions of consumers through popular apps like Instagram.

### Conclusion

So where does this Django behind the scenes tour leave us? Django’s code is open source and available to all. Django’s organization is managed by a non-profit, the DSF, with a miniscule budget. And Django code is lead by a core team of volunteers, two paid Django Fellows, and a larger group of contributors.

One of the best ways to become more involved in Django is to attend an annual conference and meet all the contributors in person. Currently there are DjangoCons in the US, Europe, Australia, and Africa in 2020 for the first time. I hope to see some of you there!

Resources :
1. [Getting started with Django Just Intro to Django](https://www.djangoproject.com/start/)
2. [How Django Works Behind the Scenes](https://wsvincent.com/how-django-works-behind-the-scenes/)
3. [What is Django](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction)
4. [First Django App - Part 1](https://docs.djangoproject.com/en/3.0/intro/tutorial01/)
5. [First Django App - Part 2](https://docs.djangoproject.com/en/3.0/intro/tutorial02/)