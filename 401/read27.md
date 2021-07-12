# Using models
Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc
### Designing the LocalLibrary models

Once we've decided on our models and field, we need to think about the relationships. Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).

### Model primer
how a model is defined and some of the more important fields and field arguments.
##### Model definition

Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata. The code fragment below shows a "typical" model, named MyModelName:

```
from django.db import models

class MyModelName(models.Model):
    """A typical class defining a model, derived from the Model class."""

    # Fields
    my_field_name = models.CharField(max_length=20, help_text='Enter field documentation')
    ...

    # Metadata
    class Meta:
        ordering = ['-my_field_name']

    # Methods
    def get_absolute_url(self):
        """Returns the url to access a particular instance of MyModelName."""
        return reverse('model-detail-view', args=[str(self.id)])

    def __str__(self):
        """String for representing the MyModelName object (in Admin site etc.)."""
        return self.my_field_name
```
explore code : 
1. Fields
    A model can have an arbitrary number of fields, of any type — each one represents a column of data that we want to store in one of our database tables. Each database record (row) will consist of one of each field value.
    * max_length=20 — States that the maximum length of a value in this field is 20 characters.
    * help_text='Enter field documentation' — provides a text label to display to help users know what value to provide when this value is to be entered by a user via an HTML form.
2. Metadata 
    declare model-level metadata for your Model by declaring class Meta, as shown.
    ```
    class Meta:
    ordering = ['-my_field_name']
    ```
     to control the default ordering of records returned when you query the model type. 
3. Methods
    Minimally, in every model you should define the standard Python class method __str__() to return a human-readable string for each object
> get_absolute_url()  returns a URL for displaying individual model records on the website (if you define this method then Django will automatically add a "View on Site" button to the model's record editing screens in the Admin site).

### Model management
create, update, or delete records, and to run queries to get all records or particular subsets of records.
##### Creating and modifying records
```
# Create a new record using the model's constructor.
record = MyModelName(my_field_name="Instance #1")

# Save the object into the database.
record.save()
```
##### Searching for records
We can get all records for a model as a QuerySet, using objects.all(). The QuerySet is an iterable object, meaning that it contains a number of objects that we can iterate/loop through.

```
all_books = Book.objects.all()
```

Django's filter() method allows us to filter the returned QuerySet to match a specified text or numeric field against particular criteria. For example, to filter for books that contain "wild" in the title and then count them, we could do the following.

``` wild_books = Book.objects.filter(title__contains='wild')
number_wild_books = wild_books.count()
```

Resources: 

* [Using Models](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)
* [Django Admin](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)
  * Advanced configuration section is optional
  * The tutorial is really good but some of the tools are dated so when reading try to understand the concepts more than the code.

* [Beginner’s Guide to Django - Part 1](https://simpleisbetterthancomplex.com/series/2017/09/04/a-complete-beginners-guide-to-django-part-1.html)
* [Beginner’s Guide to Django - Part 2](https://simpleisbetterthancomplex.com/series/2017/09/11/a-complete-beginners-guide-to-django-part-2.html)