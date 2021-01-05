## read_29
## custom user model
The official Django documentation highly recommends using a custom user model. This provides far more flexibility down the line so, as a general rule, always use a custom user model for all new Django projects.
## Setup
To start, create a new Django project from the command line. We need to do several things:

1. create and navigate into a dedicated directory called accounts for our code
2. install Django
3. make a new Django project called config
4. make a new app accounts
5. start the local web server
Here are the commands to run:
```
$ cd ~/Desktop
$ mkdir accounts && cd accounts
$ pipenv install django~=3.1.0
$ pipenv shell
(accounts) $ django-admin.py startproject config .
(accounts) $ python manage.py startapp accounts
(accounts) $ python manage.py runserver
```

## AbstractUser vs AbstractBaseUser
There are two modern ways to create a custom user model in Django: AbstractUser and AbstractBaseUser.
AbstractBaseUser requires much, much more work.

So we'll use AbstractUser which actually subclasses AbstractBaseUser but provides more default configuration.

## Custom User Model
Creating our initial custom user model requires four steps:

* update config/settings.py
* create a new CustomUser model
* create new UserCreation and UserChangeForm
* update the admin
```
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'accounts', # new
]
...

AUTH_USER_MODEL = 'accounts.CustomUser' # new
```
Now update accounts/models.py with a new User model which we'll call CustomUser.

# accounts/models.py
```
from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    pass
    # add additional fields in here

    def __str__(self):
        return self.username

```

We need new versions of two form methods that receive heavy use working with users. Stop the local server with Control+c and create a new file in the accounts app called forms.py.
```
(accounts) $ touch accounts/forms.py
```
We'll update it with the following code to largely subclass the existing forms.
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

Finally we update admin.py since the Admin is highly coupled to the default User model.
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
## Then create a database and templates , urls and views


### [The resource](https://learndjango.com/tutorials/django-custom-user-model)