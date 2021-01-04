## read_27
## Overview
Django web applications access and manage data through Python objects referred to as models. Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc. The definition of the model is independent of the underlying database — you can choose one of several as part of your project settings. Once you've chosen what database you want to use, you don't need to talk to it directly at all — you just write your model structure and other code, and Django handles all the dirty work of communicating with the database for you.

## Designing the LocalLibrary models
*Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).

* With that in mind, the UML association diagram below shows the models we'll define in this case (as boxes).
![image](https://mdn.mozillademos.org/files/17406/local_library_model_uml.png)

*The diagram also shows the relationships between the models, including their multiplicities. The multiplicities are the numbers on the diagram showing the numbers (maximum and minimum) of each model that may be present in the relationship. For example, the connecting line between the boxes shows that Book and a Genre are related. The numbers close to the Genre model show that a book must have one or more Genres (as many as you like), while the numbers on the other end of the line next to the Book model show that a Genre can have zero or many associated books.*

## Model definition
Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata.

## Fields
A model can have an arbitrary number of fields, of any type — each one represents a column of data that we want to store in one of our database tables. Each database record (row) will consist of one of each field value. 
## Common field arguments
The following common arguments can be used when declaring many/most of the different field types:

* help_text: Provides a text label for HTML forms (e.g. in the admin site), as described above.
* verbose_name: A human-readable name for the field used in field labels. If not specified, Django will infer the default verbose name from the field name.
* default: The default value for the field. This can be a value or a callable object, in which case the object will be called every time a new record is created.
* null: If True, Django will store blank values as NULL in the database for fields where this is appropriate (a CharField will instead store an empty string). The default is False.
* blank: If True, the field is allowed to be blank in your forms. The default is False, which means that Django's form validation will force you to enter a value. This is often used with null=True , because if you're going to allow blank values, you also want the database to be able to represent them appropriately.
* choices: A group of choices for this field. If this is provided, the default corresponding form widget will be a select box with these choices instead of the standard text field.
* primary_key: If True, sets the current field as the primary key for the model (A primary key is a special database column designated to uniquely identify all the different table records). If no field is specified as the primary key then Django will automatically add a field for this purpose.

## Metadata
You can declare model-level metadata for your Model by declaring class Meta, as shown.
```
class Meta:
    ordering = ['-my_field_name']
```
## Registering models 
First, open admin.py in the catalog application (/locallibrary/catalog/admin.py). It currently looks like this — note that it already imports django.contrib.admin:
```
from django.contrib import admin

# Register your models here.
```
## Creating a superuser
In order to log into the admin site, we need a user account with Staff status enabled. In order to view and create records we also need this user to have permissions to manage all our objects.  You can create a "superuser" account that has full access to the site and all needed permissions using manage.py.
## Logging in and using the site
To login to the site, open the /admin URL (e.g. http://127.0.0.1:8000/admin) and enter your new superuser userid and password credentials (you'll be redirected to the login page, and then back to the /admin URL after you've entered your details).
This part of the site displays all our models, grouped by installed application. You can click on a model name to go to a screen that lists all its associated records, and you can further click on those records to edit them. You can also directly click the Add link next to each model to start creating a record of that type.
The refernces:
[1. developer.mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

[2. developer.mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)