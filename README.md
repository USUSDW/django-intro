# Introduction To Django and Web Frameworks

If you have found yourself wondering, "How would I go about building a high quality website like many I see on the modern web?" or "How do I create a product that people *want* to use?" or even, "What is a good way to test my software-development abilities?" then this presentation is for you! 

Today we will learn all about the fundamentals of web frameworks, software design patterns commonly used in industry, and the Django Web Framework. 

## Table Of Contents
*   ... I ran out of time to fill this out for now lol
*   [Sources](#Sources)

## "Required" Knowledge
Before continuing with this presentation, you may want to ensure you have some familiarity with the following topics:

*   Basics of HTML/CSS
*   Knowledge of Python
*   If you lack the above requirements, then there is an option for you...
    *   Following along to the best of your abilities to gain the drive to learn the above!


## What Is Django?
Django is a Python based web framework used for developing web applications! It is *not* an HTTP(S) server in and of itself, but it works in conjunction with an HTTP(S) server to serve the web application.


### Okay... What is a web framework?
A web framework is an application framework for creating web servers and web applications. See [What is an Application Framework?](https://gitlab.cs.usu.edu/erik.falor/fa21-cs2610-lecturenotes/-/blob/master/Module2/Django.md#what-is-an-application-framework) in Erik's Lecture Notes for more

### Now, what is an HTTP(S) server? 
Long story short, a server is a device that *serves* information when information is requested of it. Much like a waiter in a restuarant serves food when requested, an HTTP server will return requested data to the person that requested it through the HTTP web protocol.

#### Dynamic vs Static Servers
*   Static servers are ones where the data returned for any identical request is the same
    *   If I ask a server to get `hamburgers.html` I *will* get the same `hamburgers.html` file every time I make that request, and every user that makes the request will see the same `hamburgers.html` file that I got
*   Dynamic servers change the content *dynamically* based on numerous factors, such as which user is requesting what data
    *   If I ask a server to go to `accounts.html`, I may be redirected to a login page or a page of my accounts information, depending on if I previously signed into the website

## The MVC Design Pattern : Model, View, Controller
Model View Controller is a software design pattern commonly used to organize code when developing user interfaces and web applications

MVC stands for...
*   Model
    *   Models the data stored inside the database
*   View
    *   Defines the presentation for the user
*   Controller
    *   Allows the user to give input and process said input.
        *   EX: User requests `MYSITE.com/accounts`, so the controller process the input and then presents the user the accounts page

When using Django terminology, this changes just a tad. When one refers to specific segments of the Model, View, Controller design pattern, Django implemented it with slightly different naming conventions

*   Model in MVC -> Model in Django
    *   See an applications `models.py` file, as well as the data migrations (which is the result of the ORM translating the data in `models.py` to the database)
*   View in MVC -> Template in Django
    *   Configured for dynamic templates in the `templates/<APP_NAME>` directory 
    *   Configured for static files in the `static/<APP_NAME>` directory 
    *   Configured in an apps `views.py` file which defines what templates/static files to return or manipulation tasks to perform
        *   Please note that Django's `views.py` fits in both the View and Controller aspsects of the MVC design pattern 
*   Controller in MVC -> View in Django
    *   List of `django.urls.path` objects called `urlpatterns`
    *   "When X url is requested, I want you to perform the task defined in the Y view"
    *   Project level controller defined in `<PROJ_DIR>/urls.PY`
    *   App level controller defined in `<APP_DIR>/urls.py`
        *   Each app's urls must be `include`d into the project level `urls.py` file 
    *   The contents of `views.py` define the *work and controls* I want to happen, while the contents of a `urls.py` file defines how to access the given view 

Please see the ["What Is MVC and/or MTV?" section of the Fa21 CS2610 Lecture Notes](https://gitlab.cs.usu.edu/erik.falor/fa21-cs2610-lecturenotes/-/blob/master/Module2/Django.md#what-is-mvc-andor-mtv) for more information

## Models : What exactly are they?
*   Kind of like a class for data that will exist inside a database
*   You define the shape of the data and the data types contained in your model that will exist in the database
*   We will use sqllite3 for now to store our models
*   Note that the ORM allows us easy access to the models inside of sqllite3 without needing to know any SQL syntax
    *   Thanks, libraries and abstraction!

## CRUD Design Pattern
CRUD is how one creates methods to manipulate the objects in a data base. CRUD stands for:
*   Create
*   Read
*   Update
*   Destroy

In Django, we use the ORM to actively manipulate the object inside the database. But to expose this functionality to the users of our web app, we follow the crud model

*   C: Allow a user to visit a specific web link to create a new queue request
*   R: Allow select users to read the data on a queue request that exists in the database
*   U: Allow a user to update information on an existing queue request object in the database
*   D: Allow a user to delete a queue request when it is not necessary
*   Using API's with CRUD methodology is a great way to create high quality web applications with a lot of expandability! Why do I bring this up? Wait for next week... ;)

## Django Installation

Assuming you have `pip` installed on your computer (the Python package manager), one can install the newest version of Django with `$ pip install django`. If we are wanting to ensure that we are all on the *exact* same version of Django, we can modify the command to be `$ pip install Django==3.2.7`. 

See [Django Download Page](https://www.djangoproject.com/download/) for more information.

## The Polls App And The `mysite` Project
Let us build the polls app together, and learn Django together! As we build this app, we will relate what we see to what we have discussed above.

Please see the [`mysite`](./mysite) directory for the sample project we will build together.

## If we have the time...
We can start planning a future project together!

## Sources
*   [The Honorable Erik Falor And His Phenomenal Web Development Course Lecture Notes](https://gitlab.cs.usu.edu/erik.falor/fa21-cs2610-lecturenotes)
    *   [Erik Falor's CS2610 Lecture Notes For Monday, September 27th's](https://gitlab.cs.usu.edu/erik.falor/fa21-cs2610-lecturenotes/-/tree/master/Module2/Lec11-Mon_Sep_27)
    *   [CS2610 Introduction To Django](https://gitlab.cs.usu.edu/erik.falor/fa21-cs2610-lecturenotes/-/blob/master/Module2/Django.md)
    *   Real quick, I just want to add how grateful I am for Erik teaching me about Django initially, and allowing me to utilize and adapt part of his lecture notes for this presentation. Seriously, take Web Dev with him if you can. You will not regret it.
*   [Django Project](https://djangoproject.com/)
*   [Django 3.2 Documentation](https://docs.djangoproject.com/en/3.2)
*   [Django 3.2 "Writing Your First App" Tutorial](https://docs.djangoproject.com/en/3.2/intro/tutorial01/)
