## read-26
## Django 
is a Python-based web framework used by millions of developers and billions of consumers through popular apps like Instagram. It is open source, meaning the code is available for free on Github and can be downloaded onto any developer’s computer and used alongside the official documentation.
* Ridiculously fast.
Django was designed to help developers take applications from concept to completion as quickly as possible.
* Fully loaded.
Django includes dozens of extras you can use to handle common Web development tasks. Django takes care of user authentication, content administration, site maps, RSS feeds, and many more tasks — right out of the box.
* Reassuringly secure.
Django takes security seriously and helps developers avoid many common security mistakes, such as SQL injection, cross-site scripting, cross-site request forgery and clickjacking. Its user authentication system provides a secure way to manage user accounts and passwords.
* Exceedingly scalable.
Some of the busiest sites on the planet use Django’s ability to quickly and flexibly scale to meet the heaviest traffic demands.
* Incredibly versatile.
Companies, organizations and governments have used Django to build all sorts of things — from content management systems to social networks to scientific computing platforms.
![image](https://mdn.mozillademos.org/files/13931/basic-django.png)
#### URLs:
 While it is possible to process requests from every single URL via a single function, it is much more maintainable to write a separate view function to handle each resource. A URL mapper is used to redirect HTTP requests to the appropriate view based on the request URL. The URL mapper can also match particular patterns of strings or digits that appear in a URL and pass these to a view function as data.
#### View:
 A view is a request handler function, which receives HTTP requests and returns HTTP responses. Views access the data needed to satisfy requests via models, and delegate the formatting of the response to templates.
#### Models: 
Models are Python objects that define the structure of an application's data, and provide mechanisms to manage (add, modify, delete) and query records in the database. 
Templates: A template is a text file defining the structure or layout of a file (such as an HTML page), with placeholders used to represent actual content. A view can dynamically create an HTML page using an HTML template, populating it with data from a model. A template can be used to define the structure of any type of file; it doesn't have to be HTML!
## What can you do?
* Sending the request to the right view (urls.py).
* Handling the request (views.py).
* Defining data models (models.py).
* Querying data (views.py).
* Rendering data (HTML templates).

* Also The preceding sections show the main features that you'll use in almost every web 

* application: URL mapping, views, models and templates. Just a few of the other things provided by Django include:

* Forms: HTML Forms are used to collect user data for processing on the server. Django simplifies form creation, validation, and processing.
* User authentication and permissions: Django includes a robust user authentication and permission system that has been built with security in mind. 
* Caching: Creating content dynamically is much more computationally intensive (and slow) than serving static content. Django provides flexible caching so that you can store all or part of a rendered page so that it doesn't get re-rendered except when necessary.
* Administration site: The Django administration site is included by default when you create an app using the basic skeleton. It makes it trivially easy to provide an admin page for site administrators to create, edit, and view any data models in your site.
* Serialising data: Django makes it easy to serialise and serve your data as XML or JSON. This can be useful when creating a web service (a website that purely serves data to be consumed by other applications or sites, and doesn't display anything itself), or when creating a website in which the client-side code handles all the rendering of data.
### The resources 
[1.developer.mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction).

[2.wsvincent](https://wsvincent.com/how-django-works-behind-the-scenes/).

[3.djangoproject](https://docs.djangoproject.com/en/3.0/intro/tutorial01/)

