# Django

## Contents

1. [Django framework](#django-framework)

    - [What is Django?](#what-is-django)
    - [Django Architecture (MTV: Model, Template, View)](#django-architecture-mtv-model-template-view)
    - [Key Features of Django](#key-features-of-django)

2. [Installation and setup](#installation-and-setup)

    - [System Requirements](#system-requirements)
    - [Installing Django](#installing-django)
    - [Understanding the Directory Structure](#understanding-the-directory-structure)

3. [Database Operations](#database-operations)

    - [Setting up a database](#setting-up-a-database)
    - [Migrations](#migrations)
    - [Querysets an ORM](#querysets-and-orm)
    - [Managing relationships](#managing-relationships)

4. [Forms and Validation](#forms-and-validation)

    - [Creating Forms](#creating-forms)
    - [Handling Form Data](#handling-form-data)
    - [Built-in Validation](#built-in-validation)
    - [Custom Validation](#custom-validation)

5. [Authentication and Authorization](#authentication-and-authorization)

    - [Django's Authentication System](#djangos-authentication-system)
    - [User Management](#user-management)
    - [Permission and Authorization](#permission-and-authorization)

6. [Admin Interface](#admin-interface)

    - [Setting up the Django Admin](#setting-up-the-django-admin)
    - [Customizing Admin Interface](#customizing-admin-interfaceP)
    - [Managing Models via Admin](#managing-media-files)

7. [Static Files and Media Handling](#static-files-and-media-handling)

    - [Serving Static Files](#serving-static-files)
    - [Managing Media Files](#managing-media-files)
    - [Best Practices for File Handling](#best-practices-for-file-handling)

8. [Security in Django](#security-in-django)

    - [CSRF Protection](#csrf-protection-cross-site-request-forgery)
    - [SQL Injection Prevention](#sql-injection-prevention)
    - [XSS Protection](#xss-protection-cross-site-scripting)
    - [Best Practices for Securing Django Apps](#best-practices-for-securing-django-apps)

9. [Deployment](#deployment)

    - [Preparing for Deployment](#preparing-for-deployment)
    - [Using WSGI/ASGI](#using-wsgiasgi)
    - [Deployment Platforms (Heroku, AWS, etc.)](#deployment-platforms-heroku-aws-etc)
    - [Continuous Integration and Deployment (CI/CD)](#continuous-integration-and-deployment-cicd)

## Django framework

### What is Django?

Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design.

### Django Architecture (MTV: Model, Template, View)

![django architecture](https://github.com/user-attachments/assets/a918a161-7a37-4ea9-a037-d0b775d07dd2)


-   **Model**: Model contains the logical file structure of the project and is the middleware & data handler between database and view.
    -   Model provides a definition the data formats.
    -   It stores and retrives information from database.
-   **View**: The View in this MTV architecture is formatting the data via the model.
    -   Handles user requests and returns responses.
    -   Views are functions or classes that receive HTTP requests, process them (possibly interacting with the models), and return HTTP responses.
    -   They are responsible for deciding what data to send to the template and how to format it.
-   **Template**: Manages the presentation layer.
    -   Templates are responsible for rendering the data into HTML that is sent to the client.
    -   They use Django’s template language to insert dynamic content into HTML pages.

### Key Features of Django

1. **Automatic Admin Interface:**
    - Django automatically generates an admin interface for managing application data.
    - The interface is highly customizable and provides a powerful way to manage the content of the application without needing to write additional code.
2. **ORM (Object-Relational Mapping):**
    - Django's ORM allows developer to interact with database using Python code rather than SQL.
3. **URL Routing:**
    - This system allows for clean, readable URL patterns and makes it easy to manage the routing of requests within the application.
4. **Built-in Authentication System:**
    - Django includes a comprehensive authentication system that handles user registration, login, logout, password management, and permissions.
5. **Template Engine:**
    - Django comes with its own templating engine, which allows to create dynamic HTML pages by embedding Python-like expressions into HTML templates.
6. **Form Handling:**
    - Django provides a powerful forms framework that simplifies the process of creating and validating forms.
    - It includes features for rendering forms, handling user input, and performing validation.
7. **Security Features:**
    - Django includes a range of built-in security features to protect your application from common vulnerabilities, such as SQL injection, cross-site scripting (XSS), cross-site request forgery (CSRF), and clickjacking.
    - It also provides tools for password hashing and secure cookie handling.
8. **Scalability:**
    - Django is designed to scale, supporting large and complex applications.
    - It includes features like caching and support for multiple database backends, which help improve performance and scalability.
9. **Development Tools:**
    - Django offers a variety of development tools, including a built-in development server, a command-line interface for administrative tasks, and tools for database migrations and testing.
10. **Rich Ecosystem:**
    - Django has a rich ecosystem of third-party packages and extensions available through the Django Packages website and PyPI (Python Package Index).
    - This ecosystem allows you to extend Django’s functionality and integrate with other tools and services.
11. **Community and Documentation:**
    - Django has a strong and active community, along with extensive documentation. This support helps developers find solutions to problems, share best practices, and stay updated with the latest developments.

## Installation and Setup

### System Requirements

-   **Python:** Ensure Python (3.x) is installed on your system.
-   **Pip:** Python package manager (pip) should be installed.
-   **Virtual Environment:** Recommended for isolating project dependencies.

### Installing Django

1. **Installing Python:**
2. **Creating virtual environment and activating:**

    ```bash
    python -m venv env
    ```

    To activate

    ```bash
    source env/bin/activate
    ```

3. **Installing Django via pip:**

    ```bash
    pip install django
    ```

    To verify installation

    ```bash
    django-admin --version
    ```

4. **Creating Django project:**
    ```bash
    django-admin startproject project_name
    ```

### Understanding the Directory Structure

When Django project is created, it usually creates a top-level directory with the name specified.

Contents of directory

1. **manage.py:**
    - `manage.py` file provides a a command-line utility that helps to interact with Django project.
    - It is used run the development server, make migrations, and perform various administrative tasks.
    - Common commands include `runserver`, `makemigrations`, `migrate`, `createsuperuser`, etc.
2. **Project directory**
    1. **init**.py:
        - An empty file that tells Python to treat this directory as a package.
    2. settings.py:
        - Contains settings and configuration for the Django project.
        - This is where developer must configure database settings, static files, middleware, and more.
    3. urls.py:
        - Contains URL patterns for the project. This file routes requests to the appropriate view functions or other URLconfs.
    4. wsgi.py:
        - Provides the WSGI interface for deploying Django application to a web server.
    5. asgi.py:
        - Provides the ASGI interface for asynchronous support and deploying application to an ASGI server.

## Database Operations

### Setting up a Database

**1. Choose database:**
Django supports several database backends, including: - SQLite (default) - PostgreSQL - MySQL - Oracle 2. **Installing databse:**
For Postgres
`bash
    pip install psycopg2-binary
    ` 3. **Configure Database Settings:**
Update the DATABASES setting in the settings.py file. This configuration tells Django how to connect to database.

-   SQLite (default):

    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }
    ```

-   Postgres:
    ```py
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'mydatabase',
            'USER': 'mydatabaseuser',
            'PASSWORD': 'mypassword',
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }
    ```

4. **Migrations:**

Migrations are Django’s way of propagating changes made to your models (database schema) into the database. 1. **Creating migrations:** Generate migration files for any changes in your models:
`py
        python manage.py makemigrations
        ` 2. **Apply Migration:** Apply the migrations to create or update database tables.
`py
        python manage.py migrate
        ` 5. **Additional Configuration:** - **Database Indexes:** Add indexes to the models to improve query performance. - **Database Caching:** Configure caching to enhance performance. - **Database Backups:** Set up regular backups to protect the data.

### Migrations

-   Migrations are a way of propagating changes made in the models (such as adding a field, deleting a model, or changing a field type) into your database schema.
-   Django handles these changes with migration files that are created automatically when changes are detected.

1. **Understanding Migrations:**
    - Migrations are Python files that represent the database schema changes.
    - Each migration is a snapshot of the model's state at a certain point in time.
    - Migrations ensure that database changes are version-controlled and applied in order.
2. **Creating Migrations:** - After making changes to models, migration file can be created using:
   `bash
python manage.py makemigrations
`
   Django detects changes in models and creates migration files under the `migrations/` directory of the app.
3. **Applying Migrations**
   To apply the migrations to the database and reflect the changes, run:
   `bash
python manage.py migrate
`
   This command applies any unapplied migrations to the database.
4. **Migration Workflow**
    - Modify the Models: Add, delete, or modify model fields.
    - Create Migrations: Use makemigrations to generate migration files.
    - Apply Migrations: Use migrate to apply changes to the database.
5. **Viewing Migration SQL**

    - To see the SQL queries generated by a migration, use:

        ```bash
        python manage.py sqlmigrate app_name migration_number
        ```

        Example:

        ```bash
        python manage.py sqlmigrate myapp 0001
        ```

    - This will display the SQL commands that will be executed for that migration.

6. **Checking Migration Status**
    - To check which migrations have been applied and which are pending, use:
        ```bash
        python manage.py showmigrations
        ```
7. **Rolling Back Migrations**

    - To revert to a previous state, migrations can be reverted by specifying a migration number:

        ```bash
        python manage.py migrate app_name migration_number
        ```

        Example: To roll back to the initial migration (before any changes):

        ```bash
        python manage.py migrate myapp 0001
        ```

8. **Merging Migrations**

    - If there are multiple migrations that need to be combined (e.g., two developers made different changes), migrations can be merged.
        ```bash
        python manage.py makemigrations --merge
        ```
    - Django will attempt to resolve conflicts between migrations.

9. **Auto Field Changes**
    - Django automatically creates an id field as the primary key for models. If different primary key is specified, migrations will handle the adjustment.
    - **Common Migration Scenarios:**
        - **Add a new field:** Modify the model, then run makemigrations and migrate.
        - **Remove a field:** Delete the field from the model, then create and apply migrations.
        - **Rename a model or field:** Use makemigrations, which tracks renaming automatically.
        - **Changing field types:** When modifying field attributes, Django will detect and generate the necessary migrations.

### Querysets and ORM

-   Django's ORM (Object-Relational Mapping) provides a powerful way to interact with the database using Python objects.
-   QuerySets are a fundamental component of Django's ORM that allow us to retrieve, filter, and manipulate data in a database.

1.  **What are querysets:**

    -   A QuerySet is a collection of database queries that Django constructs to retrieve data from the database.
    -   It represents a set of objects and provides methods to filter, sort, and manipulate the data.

    **Explaining with example**

    1.  **Defining Models**

        ```py
        from django.db import models

        class Author(models.Model):
            name = models.CharField(max_length=100)
            birthdate = models.DateField()

            def __str__(self):
                return self.name

        class Book(models.Model):
            title = models.CharField(max_length=100)
            author = models.ForeignKey(Author, on_delete=models.CASCADE)
            published_date = models.DateField()

            def __str__(self):
                return self.title
        ```

    2.  **Creating and Retrieving QuerySets:**

        -   **Retrieving All Objects**
            To retrieve all objects from a model:

            ```py
            from myapp.models import Book
            all_books = Book.objects.all()
            ```

        -   **Filtering**
            To filter QuerySets using the .filter() method:

            ```py
            # Get all books published after a certain date
            recent_books = Book.objects.filter(published_date__gte='2023-01-01')

            # Get books with a specific title
            specific_books = Book.objects.filter(title='Django for Beginners')
            ```

        -   **Excluding**
            Exclude certain objects using .exclude():

            ```py
            # Get all books except those with a specific title
            books_not_named = Book.objects.exclude(title='Django for Beginners')
            ```

        -   **Getting a Single Object**
            Use .get() to retrieve a single object. It raises an exception if no match is found or if multiple matches are found.

            ```py
            try:
                specific_book = Book.objects.get(id=1)
            except Book.DoesNotExist:
                specific_book = None
            ```

        -   **Ordering**
            Order QuerySets using .order_by():

            ```py

            # Order books by published date
            ordered_books = Book.objects.order_by('published_date')

            # Order by descending published date
            ordered_books_desc = Book.objects.order_by('-published_date')
            ```

        -   **Limiting Results**
            Use .limit() or .[:n] to limit the number of results:

            ```py
            # Get the first 5 books
            top_books = Book.objects.all()[:5]
            ```

    3.  **Aggregation and Annotation:**

        -   **Aggregation**
            Django’s ORM supports aggregate functions to perform calculations on QuerySets:

                ```py
                from django.db.models import Count, Avg

                # Get the average publication year of books
                average_year = Book.objects.aggregate(Avg('published_date'))

                # Count the number of books
                book_count = Book.objects.aggregate(Count('id'))
                ```

        -   **Annotation**
            Use .annotate() to add calculated fields to each object in the QuerySet:

                ```py
                from django.db.models import Count

                # Annotate authors with the number of books they've written
                authors_with_books = Author.objects.annotate(num_books=Count('book'))
                ```

    4.  **Chaining QuerySets:**
        QuerySets are chainable, so you can combine multiple methods:

            ```py
            # Get books by a specific author, published after 2020, and order them by title
            books = Book.objects.filter(author__name='John Doe').filter(published_date__year__gt=2020).order_by('title')
            ```

    5.  **Updating and Deleting:**

        -   **Updating**
            Use the .update() method to update fields in a QuerySet:

                ```py
                # Update the title of all books with a specific author
                Book.objects.filter(author__name='John Doe').update(title='Updated Title')
                ```

        -   **Deleting**
            Use the .delete() method to remove objects from the database:

                ```py
                # Delete all books published before 2000
                Book.objects.filter(published_date__lt='2000-01-01').delete()
                ```

    6.  **Raw SQL Queries:**

        ```py
        from django.db import connection

        def raw_query_example():
            with connection.cursor() as cursor:
                cursor.execute("SELECT * FROM myapp_book WHERE published_date > %s", ['2023-01-01'])
                rows = cursor.fetchall()
            return rows
        ```

### Managing Relationships

-   Django provides several tools to manage relationships between models (database tables).
-   The relationships define how one model is related to another, allowing easy navigation and query related data.

1. **One-to-One Relationship:**
   A one-to-one relationship links a model to another model in a one-to-one mapping.

    ```py
    class Profile(models.Model):
        user = models.OneToOneField(User, on_delete=models.CASCADE)
        bio = models.TextField()
    ```

    `on_delete:` Defines what happens when the related object is deleted (`CASCADE`, `SET_NULL`, etc.).

2. **Many-to-One (Foreign Key) Relationship:**
   A many-to-one relationship means that multiple instances of one model can be related to one instance of another model.

    ```py
    class Author(models.Model):
        name = models.CharField(max_length=100)

    class Book(models.Model):
        title = models.CharField(max_length=200)
        author = models.ForeignKey(Author, on_delete=models.CASCADE)
    ```

    `ForeignKey` is used to define the many-to-one relationship.
    **Reverse Query:** Allows to access all related objects via the related model. For example, author.book_set.all() will return all books by the author.

3. **Many-to-Many Relationship:**
   A `many-to-many` relationship allows one model to be related to multiple instances of another model, and vice versa.

    ```py
    class Student(models.Model):
    name = models.CharField(max_length=100)

    class Course(models.Model):
    name = models.CharField(max_length=100)
    students = models.ManyToManyField(Student)
    ```

    Django creates an intermediary table (join table) to store the relationships automatically.

    **Reverse Query:** Related objects from either side of the relationship can be accessed.

    For example, `course.students.all()` will return all students enrolled in the course, and student.

    `course_set.all()` will return all courses for a student.

4. **Customizing Relationship Behavior:**

-   on_delete Options:
    `CASCADE:` Deletes related objects when the referenced object is deleted.

    `SET_NULL:` Sets the foreign key to NULL if the related object is deleted.

    `PROTECT:` Prevents deletion of the referenced object if there are related objects.

    `SET_DEFAULT:` Sets a default value when the referenced object is deleted.

    `DO_NOTHING:` Takes no action, leaving responsibility for handling the situation to the developer.

5.  **Intermediate (Through) Tables:**
    Storing additional information in a many-to-many relationship.

    ```py
    class Enrollment(models.Model):
        student = models.ForeignKey(Student, on_delete=models.CASCADE)
        course = models.ForeignKey(Course, on_delete=models.CASCADE)
        enrollment_date = models.DateField()

    class Course(models.Model):
        name = models.CharField(max_length=100)
        students = models.ManyToManyField(Student, through='Enrollment')
    ```

6.  **Accessing Related Data:**

-   **Forward Query:** Access related objects from the model where the relationship is defined.

    ```py
    author = Author.objects.get(id=1)
    books = author.book_set.all() # Accessing related books
    ```

-   **Reverse Query:** Access the related object from the model it refers to using the related_name.
    ```py
    book = Book.objects.get(id=1)
    author = book.author # Accessing related author
    ```

## Forms and Validation

-   Forms in Django are a way to handle user input on your web applications.
-   They allow developer to collect and process data from users, validate that data, and provide feedback if necessary.
-   Django provides a built-in framework for working with forms, which simplifies the process of handling form submissions and data validation.

### Creating Forms

1. **Define a Form Class:**

    - Create a new form class by subclassing `django.forms.Form` or `django.forms.ModelForm`. `ModelForm` is used to create a form based on a Django model.

    - Using `forms.Form`:

        ```py
        # forms.py
        from django import forms

        class ContactForm(forms.Form):
            name = forms.CharField(max_length=100, label='Your Name')
            email = forms.EmailField(label='Your Email')
            message = forms.CharField(widget=forms.Textarea, label='Your Message')
        ```

    - Using `forms.ModelForm`:

        ```py
        # models.py
        from django.db import models

        class Feedback(models.Model):
            name = models.CharField(max_length=100)
            email = models.EmailField()
            message = models.TextField()

        # forms.py
        from django import forms
        from .models import Feedback

        class FeedbackForm(forms.ModelForm):
            class Meta:
                model = Feedback
                fields = ['name', 'email', 'message']
        ```

### Handling Form data

1. **Add Form to a View:**

    - In the view, instantiate the form and handle form submissions.

        ```py
        Copy code
        # views.py
        from django.shortcuts import render, redirect
        from .forms import ContactForm, FeedbackForm

        def contact_view(request):
            if request.method == 'POST':
                form = ContactForm(request.POST)
                if form.is_valid():
                    # Process form data
                    name = form.cleaned_data['name']
                    email = form.cleaned_data['email']
                    message = form.cleaned_data['message']
                    # Do something with the data (e.g., send an email)
                    return redirect('success')
            else:
                form = ContactForm()

            return render(request, 'contact.html', {'form': form})

        def feedback_view(request):
            if request.method == 'POST':
                form = FeedbackForm(request.POST)
                if form.is_valid():
                    form.save()  # Save form data to the database
                    return redirect('feedback_success')
            else:
                form = FeedbackForm()

            return render(request, 'feedback.html', {'form': form})
        ```

2. **Create Templates:**
    - Render the form in HTML templates. Use Django's template language to display the form and handle any validation errors.
        ```html
        <!-- contact.html -->
        <!DOCTYPE html>
        <html>
            <head>
                <title>Contact Us</title>
            </head>
            <body>
                <h1>Contact Us</h1>
                <form method="post">
                    {% csrf_token %} {{ form.as_p }}
                    <!-- Render form fields as paragraphs -->
                    <button type="submit">Send</button>
                </form>
            </body>
        </html>
        ```
        ```html
        <!-- feedback.html: -->
        <!DOCTYPE html>
        <html>
            <head>
                <title>Feedback</title>
            </head>
            <body>
                <h1>Feedback</h1>
                <form method="post">
                    {% csrf_token %} {{ form.as_p }}
                    <!-- Render form fields as paragraphs -->
                    <button type="submit">Submit</button>
                </form>
            </body>
        </html>
        ```

### Built-in Validation

-   Django forms automatically handle validation. If a form is not valid, it will include errors that can be displayed to the user.

    ```html
    {% if form.errors %}
    <div class="errors">
        <ul>
            {% for field, errors in form.errors.items %}
            <li>{{ field }}: {{ errors }}</li>
            {% endfor %}
        </ul>
    </div>
    {% endif %}
    ```

### Custom Validation

-   Add custom validation logic by defining methods in your form class:
    ```py
    def clean_email(self):
        email = self.cleaned_data.get('email')
        if not email.endswith('@example.com'):
            raise forms.ValidationError('Email must be from example.com domain')
        return email
    ```

### Additional features

1. **Formsets:** Use formsets to handle multiple forms on a single page, which is useful for managing multiple instances of a form.

2. **ModelForm Features:** Use ModelForm to automatically generate forms based on Django models, and customize the form fields and widgets as needed.

## Authentication and Authorization

**Authentication vs. Authorization**

-   **Authentication:** Verifying the identity of a user (e.g., login, password validation).
-   **Authorization:** Managing permissions for what authenticated users are allowed to do (e.g., access control, permissions).

### Django's Authentication

1.  **User Model** - Django comes with a built-in User model that handles essential user fields like username, email, and password. The default user model can be found in `django.contrib.auth.models.User`.

    -   **Fields of the default User model:**
        `username`

        `email`

        `password`

        `first_name`, `last_name`

        `is_staff`, `is_active`, `is_superuser`

        `last_login`, `date_joined`

    -   **Creating a User:**

        ```py
        from django.contrib.auth.models import User

        # Create a new user

        user = User.objects.create_user('john', 'john@example.com', 'password123')
        ```

2.  **User Registration**

    -   Django doesn't provide a registration form by default, but can be created one using the `UserCreationForm` or a custom form.

    -   **Using `UserCreationForm:`**

        ```py
        from django.contrib.auth.forms import UserCreationForm
        from django.shortcuts import render, redirect

        def register(request):
        if request.method == 'POST':
        form = UserCreationForm(request.POST)
        if form.is_valid():
        form.save()
        return redirect('login')
        else:
        form = UserCreationForm()
        return render(request, 'register.html', {'form': form})
        ```

3.  **Login and Logout**

    -   Django provides built-in views and forms for logging users in and out:

    -   **Login:** Use `LoginView` to handle login functionality.

        ```py
        from django.contrib.auth.views import LoginView


        class CustomLoginView(LoginView):
        template_name = 'login.html'
        ```

    -   **Logout:** Use `LogoutView` to handle logout functionality.
        ```py
        from django.contrib.auth.views import LogoutView
        class CustomLogoutView(LogoutView):
        template_name = 'logout.html'
        ```

### Permission and Authorization

1. **Groups**

    - Django allows to create groups to assign permissions to multiple users at once.
    - A group can be considered a collection of users sharing the same set of permissions.

    - **Creating a Group:**

        ```py
        from django.contrib.auth.models import Group
        # Create a new group
        group, created = Group.objects.get_or_create(name='Editors')
        ```

    - **Adding Users to a Group:**
        ```py
        user = User.objects.get(username='john')
        group = Group.objects.get(name='Editors')
        group.user_set.add(user)
        ```

2. **Permissions**

    - Django provides a built-in permission system.
    - Permissions are tied to models and can be used to grant or restrict access to different actions like add, change, delete, or view.

    - **Assigning Permissions:**

        ```py
        from django.contrib.auth.models import Permission

        # Get a permission
        permission = Permission.objects.get(codename='can_publish')

        # Assign it to a user
        user.user_permissions.add(permission)

        # Assign it to a group
        group.permissions.add(permission)
        ```

    - **Checking Permissions:**

        ```py
        if request.user.has_perm('app_name.can_publish'):
            # Do something
        ```

3. **Custom Permissions**

    - Custom permissions can be defined for models by adding them in the model’s Meta class.

        ````py
        class Article(models.Model):
            title = models.CharField(max_length=100)

            class Meta:
                permissions = [
                    ('can_publish', 'Can Publish Articles'),
                ]

        ```
        ````

4. **Password Management**

    - Django handles password hashing automatically, using secure hashing algorithms.

    1. **Password Reset**

        - Django provides views and forms to handle password reset functionality.

        - **URLs for Password Reset:**

            - `PasswordResetView`: Starts the reset process by sending an email.
            - `PasswordResetConfirmView`: Confirms the reset via a link sent to the user's email.
            - `PasswordResetCompleteView`: Finalizes the reset process.

            ```py
            from django.contrib.auth import views as auth_views

            urlpatterns = [
            path('password_reset/', auth_views.PasswordResetView.as_view(), name='password_reset'),
            path('password_reset/done/', auth_views.PasswordResetDoneView.as_view(), name='password_reset_done'),
            path('reset/<uidb64>/<token>/', auth_views.PasswordResetConfirmView.as_view(), name='password_reset_confirm'),
            path('reset/done/', auth_views.PasswordResetCompleteView.as_view(), name='password_reset_complete'),
            ]
            ```

    2. **Changing Password**

        - Django provides the `PasswordChangeView` for users to change their password.

        - **Password Change URL:**

            ```py
            path('password_change/', auth_views.PasswordChangeView.as_view(), name='password_change'),
            ```

5. **Middleware for Authentication**

    - Django has middleware to manage authentication, including session management. The default `AuthenticationMiddleware` automatically associates requests with the current logged-in user.

    - **Middleware:**
        - Middleware in Django is a framework of hooks that processes requests and responses as they pass through the application.
        - It acts as a layer between the server and the view, handling tasks like authentication, session management, logging, and modifying requests or responses.
        ```py
        MIDDLEWARE = [
        'django.contrib.sessions.middleware.SessionMiddleware',
        'django.contrib.auth.middleware.AuthenticationMiddleware', # Required for authentication
        ]
        ```

## Admin Interface

### Django Admin Interface

-   The Django Admin Interface is a powerful feature that allows to manage application data through a web-based interface.
-   It is automatically generated based on Django models and provides a user-friendly way to perform CRUD operations.

### Setting Up the Django Admin

1. **Enable Admin in Installed Apps**

    Ensure that `django.contrib.admin` is included in `INSTALLED_APPS` in `settings.py`. It is included by default in a new Django project.

    ```python
    # settings.py
    INSTALLED_APPS = [
        # other apps
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        # your apps
    ]
    ```

2. **Run Migrations**

    ```bash
    python manage.py migrate
    ```

3. **Create a Superuser**

    A superuser is required to access the admin interface.

    ```bash
    python manage.py createsuperuser
    ```

4. **Register Models**

    To make the models accessible through the admin interface, it needs to be registered. This is done in the `admin.py` file of Django app.

    Example:

    ```python
    # myapp/admin.py
    from django.contrib import admin
    from .models import Author, Book

    admin.site.register(Author)
    admin.site.register(Book)
    ```

### Customizing the Admin Interface

1. **Customizing ModelAdmin**

    To customize how the models are displayed and edited in the admin interface, create a `ModelAdmin` class and register it with model.

    Example:

    ```python
    # myapp/admin.py
    from django.contrib import admin
    from .models import Author, Book

    class BookAdmin(admin.ModelAdmin):
        list_display = ('title', 'author', 'published_date')  # Columns to display in list view
        search_fields = ('title', 'author__name')  # Fields to search
        list_filter = ('published_date', 'author')  # Filters in the sidebar
        ordering = ('-published_date',)  # Default ordering

    class AuthorAdmin(admin.ModelAdmin):
        list_display = ('name', 'birthdate')

    admin.site.register(Book, BookAdmin)
    admin.site.register(Author, AuthorAdmin)
    ```

2. **Adding Custom Actions**

    Example:

    ```python
    # myapp/admin.py
    from django.contrib import admin
    from .models import Book
    import datetime

    def mark_as_published(modeladmin, request, queryset):
        queryset.update(published_date=datetime.date.today())

    mark_as_published.short_description = "Mark selected books as published"

    class BookAdmin(admin.ModelAdmin):
        list_display = ('title', 'author', 'published_date')
        actions = [mark_as_published]

    admin.site.register(Book, BookAdmin)
    ```

3. **Customizing Admin Forms**

    To customize the forms used in the admin interface, define a custom form and use it in `ModelAdmin`.

    **Example:**

    ```python
    # myapp/forms.py
    from django import forms
    from .models import Book

    class BookAdminForm(forms.ModelForm):
        class Meta:
            model = Book
            fields = ['title', 'author', 'published_date']

    # myapp/admin.py
    from django.contrib import admin
    from .models import Book
    from .forms import BookAdminForm

    class BookAdmin(admin.ModelAdmin):
        form = BookAdminForm

    admin.site.register(Book, BookAdmin)
    ```

## Static Files and Media Handling

-   Static files include assets like CSS, JavaScript, and images that are not tied to any particular user interaction.
-   Media files are user-uploaded files such as profile pictures or document uploads.

### Serving Static Files

-   Static files are assets that are served to all users and are not changed dynamically. They include stylesheets, JavaScript files, images, and other files that do not change.

-   **Configuration**

    ```py
    # settings.py

    # Directory where static files will be collected during deployment
    STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

    # URL prefix for static files
    STATIC_URL = '/static/'

    # Directories where Django will look for static files
    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, 'static'),
    ]
    ```

-   **Collecting Static Files**

    -   During development, Django serves static files directly from their source directories.
    -   For production, these files are collected into single directory using the `collectstatic` command.

        ```bash
        python manage.py collectstatic
        ```

-   **Serving Static Files**

    -   **Development**: Django automatically serves static files when `DEBUG` is `True`. By default `django.contrib.staticfiles` is included in `INSTALLED_APPS`.

    -   **Production**: For production, use a web server like Nginx or Apache to serve static files. Configure the web server to serve files from the `STATIC_ROOT` directory.

    Example:

    ```nginx
    server {
        listen 80;
        server_name example.com;

        location /static/ {
            alias /path/to/staticfiles/;
        }
    }
    ```

### Managing Media Files

-   Media files are user-uploaded files that are stored separately from static files. They include things like profile pictures, documents, and other user-generated content.

-   **Configuration**

    ```python
    # settings.py

    # URL prefix for media files
    MEDIA_URL = '/media/'

    # Directory where media files are stored
    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
    ```

**Handling File Uploads**

-   Use Django’s `FileField` or `ImageField` in models to handle file uploads.

    Example:

    ```py
    # models.py
    from django.db import models

    class UserProfile(models.Model):
        user = models.OneToOneField(User, on_delete=models.CASCADE)
        profile_picture = models.ImageField(upload_to='profile_pics/')
        resume = models.FileField(upload_to='resumes/')
    ```

-   **Serving Media Files**

    -   **Development**: When `DEBUG` is `True`, Django can serve media files by adding the following to your `urls.py`:

        ```python
        # urls.py
        from django.conf import settings
        from django.conf.urls.static import static

        urlpatterns = [
            # your url patterns
        ] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
        ```

    -   **Production**: Serve media files using a web server or cloud storage. Configure your web server to serve files from the `MEDIA_ROOT` directory.

    Example:

    ```nginx
    server {
        listen 80;
        server_name example.com;

        location /media/ {
            alias /path/to/media/;
        }
    }
    ```

### Best Practices for File Handling

1. **Security**

-   **User Uploads**: Always validate user-uploaded files to prevent security issues. Use Django’s built-in validators or custom validation logic to ensure that files meet your requirements.
-   **Media File Paths**: Use secure paths and avoid exposing sensitive directories.

2. **Performance**

-   **Static Files**: Use a Content Delivery Network (CDN) to serve static files and improve load times. Configure your web server to cache static files.
-   **Media Files**: Optimize media files for performance. For images, use appropriate formats and sizes. Compress files to reduce load times.

3. **Backup and Storage**

-   **Regular Backups**: Implement regular backups for your media files, especially if they are critical to your application.
-   **Storage Management**: Implement policies for managing storage, such as archiving old files or limiting file sizes and types.

4. **Access Control**

-   **Permissions**: Control access to media files based on user permissions. Ensure that only authorized users can upload, view, or delete files.
-   **URL Protection**: Use signed URLs or other mechanisms to protect media files from unauthorized access.

5. **Cleanup**

-   **Orphan Files**: Periodically clean up orphaned files that are no longer associated with any records in your database.
-   **File Expiry**: Implement file expiry policies if applicable, to automatically handle old or outdated files.

## Security in Django

-   Django comes with several built-in security features to protect against common vulnerabilities like CSRF attacks, SQL injection, and XSS attacks.

### CSRF Protection (Cross-Site Request Forgery)

-   **CSRF** is an attack where a malicious website tricks a user's browser into making an unwanted request to another site where the user is authenticated.
-   Django provides automatic protection against CSRF attacks by including a **CSRF token** in forms. This token ensures that POST requests are coming from the original, legitimate site.
-   **ToImplement:**
    -   **CSRF Middleware**: The `CsrfViewMiddleware` is enabled by default in Django's middleware stack.
    -   **Usage in Forms**: Add `{% csrf_token %}` in form templates when rendering a form.
        ```html
        <form method="POST">
            {% csrf_token %}
            <!-- form fields -->
        </form>
        ```

### SQL Injection Prevention

- **SQL Injection** happens when attackers manipulate SQL queries by injecting malicious SQL code through user input.

- **ORM Protection**: Django's Object-Relational Mapper (ORM) automatically escapes input to prevent SQL injection when building queries. Django queries use parameterized SQL, which avoids direct string concatenation in queries.

    Example:

    ```python
    # Secure query via ORM
    User.objects.filter(username=request.POST['username'])
    ```

-   **Avoid Raw SQL Queries**: If raw SQL queries are required, always use parameterized queries to escape user input:
    ```python
    from django.db import connection
    cursor = connection.cursor()
    cursor.execute("SELECT * FROM users WHERE username = %s", [username])
    ```

### XSS Protection (Cross-Site Scripting)

-   **XSS** attacks occur when an attacker injects malicious scripts into a website, which then get executed in other users' browsers.
-   **Automatic Escaping**: By default, Django escapes user input in templates. This means that when user data is displayed on a web page, special characters like `<`, `>`, and `&` are replaced with HTML-safe sequences, preventing script execution.

    **Example**:

    ```html
    <!-- If `user_input` contains `<script>alert(1)</script>`, it will be escaped -->
    <p>{{ user_input }}</p>
    ```

-   **Manually Marking Safe Content**: Using `mark_safe` function to display trusted content manually.

    ```python
    from django.utils.safestring import mark_safe
    safe_content = mark_safe("<strong>This is safe</strong>")
    ```

-   **Best Practices:**
    -   **Sanitize user input**: Use libraries like `bleach` to sanitize HTML input if necessary.
    -   **Avoid `mark_safe` unless absolutely necessary** to avoid accidentally introducing XSS vulnerabilities.

### Best Practices for Securing Django Apps

1. **Keep Django and Dependencies Updated**

    - Always keep Django and third-party libraries up to date to get the latest security patches.

2. **Use Secure Passwords and Hashing**

    - **Password Hashing**: Django uses strong password hashing mechanisms like `PBKDF2`, `bcrypt`, and `Argon2` to store passwords securely. Never store passwords in plain text.
    - **Password Validation**: Django provides built-in password validators (`AUTH_PASSWORD_VALIDATORS`) to enforce strong password policies.

3. **Use HTTPS**

    - Enable **HTTPS** to encrypt data transmitted between the client and server, protecting sensitive data like login credentials.
    - Set `SECURE_SSL_REDIRECT = True` to force users to access the site over HTTPS.

4. **Set `SECURE_HSTS_SECONDS`**

    - **HTTP Strict Transport Security (HSTS)** instructs browsers to only use HTTPS. Set `SECURE_HSTS_SECONDS` to enable HSTS and define how long browsers should enforce it.

5. **CSRF and Clickjacking Protection**

    - **Clickjacking:** Clickjacking is an attack that tricks a user into clicking a webpage element which is invisible or disguised as another element.
    - **Clickjacking Protection**: Add the `X-Frame-Options` header to prevent your site from being embedded in an iframe by malicious sites.
        ```python
        X_FRAME_OPTIONS = 'DENY'
        ```
    - Use **CSRF protection** (enabled by default).

6. **Use `SECURE_BROWSER_XSS_FILTER`**

    - This setting enables the browser's built-in XSS filtering.

7. **Avoid Hardcoding Secrets**

    - Never hardcode sensitive information like API keys, database credentials, or secret keys in the codebase. Instead, store them securely in environment variables or external secret management tools.

    ```python
    import os
    SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', 'fallback-secret-key')
    ```

8. **Limit Error Information in Production**

    - Set `DEBUG = False` in production to avoid exposing sensitive error details. Use a proper error-handling service (e.g., Sentry) to log errors.

9. **Secure Admin Interface**

    - Change the default admin URL from `/admin/` to something less predictable.

    ```python
    # Change /admin/ URL
    urlpatterns = [
        path('secure-admin/', admin.site.urls),
    ]
    ```

    - Use multi-factor authentication (MFA) for admin accounts.

10. **Session Management**

    - Set **session timeouts** for inactive users to reduce the risk of session hijacking.

    ```python
    SESSION_COOKIE_AGE = 1800  # 30 minutes
    SESSION_EXPIRE_AT_BROWSER_CLOSE = True
    ```

11. **Use Django Security Middleware**
    - Ensure `django.middleware.security.SecurityMiddleware` is included in your middleware stack, as it provides many security features like HSTS, X-Content-Type-Options, and more.

## Deployment



### Using WSGI/ASGI

### Deployment Platforms (Heroku, AWS, etc.)

### Continuous Integration and Deployment (CI/CD)

### Preparing for Deployment

1. **Configure Settings**

    - **Debug Mode**: Set `DEBUG` to `False` in `settings.py` for production to avoid exposing sensitive information.
    ```python
    # settings.py
    DEBUG = False
    ```

-   **Allowed Hosts**: Specify the domains your site will run on in the `ALLOWED_HOSTS` setting.
    ```python
    # settings.py
    ALLOWED_HOSTS = ['yourdomain.com', 'www.yourdomain.com']
    ```

-   **Static and Media Files**: Configure `STATIC_ROOT` and `MEDIA_ROOT` for static and media files.
    ```python
    # settings.py
    STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
    ```

-   **Database Configuration**: Ensure that your database settings are configured for production. For example, use PostgreSQL or another production-grade database.

-   **Secret Key**: Ensure the `SECRET_KEY` is kept secure and not hard-coded in your `settings.py`. Use environment variables or a secrets management service.

2. **Set Up Logging**

-   **Logging Configuration**: Configure logging to capture errors and other important information.

    ```python
    # settings.py
    LOGGING = {
        'version': 1,
        'disable_existing_loggers': False,
        'handlers': {
            'file': {
                'level': 'ERROR',
                'class': 'logging.FileHandler',
                'filename': '/path/to/django/error.log',
            },
        },
        'loggers': {
            'django': {
                'handlers': ['file'],
                'level': 'ERROR',
                'propagate': True,
            },
        },
    }
    ```

Deploying a Django application involves several key considerations and tools. Here’s an expanded guide that includes using WSGI/ASGI, popular deployment platforms like Heroku and AWS, and Continuous Integration and Deployment (CI/CD) practices.

### Prepare for Deployment**

#### 1 Configure Settings

Ensure your `settings.py` is properly configured for production:

- **Debug Mode**: Turn off debugging.
  ```python
  DEBUG = False
  ```

- **Allowed Hosts**: Specify allowed domains.
  ```python
  ALLOWED_HOSTS = ['yourdomain.com', 'www.yourdomain.com']
  ```

- **Static and Media Files**: Set paths for static and media files.
  ```python
  STATIC_URL = '/static/'
  STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
  
  MEDIA_URL = '/media/'
  MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
  ```

- **Database Configuration**: Configure your database for production.
  ```python
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.postgresql',
          'NAME': 'mydatabase',
          'USER': 'mydatabaseuser',
          'PASSWORD': 'mypassword',
          'HOST': 'localhost',
          'PORT': '5432',
      }
  }
  ```

- **Secret Key**: Use a secure secret key.
  ```python
  SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', 'your-secret-key')
  ```

- **Logging**: Configure logging for errors and important events.
  ```python
  LOGGING = {
      'version': 1,
      'disable_existing_loggers': False,
      'handlers': {
          'file': {
              'level': 'ERROR',
              'class': 'logging.FileHandler',
              'filename': '/path/to/django/error.log',
          },
      },
      'loggers': {
          'django': {
              'handlers': ['file'],
              'level': 'ERROR',
              'propagate': True,
          },
      },
  }
  ```

### Using WSGI/ASGI

- **WSGI (Web Server Gateway Interface)** and **ASGI (Asynchronous Server Gateway Interface)** are interfaces between web servers and Python applications.

1. **WSGI**

    - **WSGI** is used for synchronous applications and is the most common for Django.
    - The default WSGI configuration in Django is located in `myproject/wsgi.py`.

        ```python
        # myproject/wsgi.py
        import os
        from django.core.wsgi import get_wsgi_application

        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'myproject.settings')
        application = get_wsgi_application()
        ```

2. **ASGI**

    - **ASGI** is used for asynchronous applications, allowing for real-time communication and WebSockets.
    - The ASGI configuration in Django is located in `myproject/asgi.py`.

        ```python
        # myproject/asgi.py
        import os
        from django.core.asgi import get_asgi_application

        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'myproject.settings')
        application = get_asgi_application()
        ```

### Deployment Platforms

1. Heroku

- **Setup**: Heroku is a PaaS (Platform as a Service) that simplifies deployment.

    1. **Install Heroku CLI**: Download and install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli).
    2. **Create a Heroku App**:

        ```bash
        heroku create my-django-app
        ```
    3. **Configure the `Procfile`**: Define how Heroku should run your application.

        ```
        web: gunicorn myproject.wsgi
        ```
    4. **Add `runtime.txt`**: Specify the Python version.

        ```
        python-3.9.7
        ```
    5. **Add Dependencies**: Ensure `requirements.txt` includes all dependencies.

    6. **Deploy**:

        ```bash
        git add .
        git commit -m "Deploy to Heroku"
        git push heroku master
        ```
    7. **Migrate Database**:

        ```bash
        heroku run python manage.py migrate
        ```

### AWS (Amazon Web Services)

- **Setup**: AWS offers various services like EC2, Elastic Beanstalk, and Lightsail.

    1. **Amazon EC2**:
        - Launch an EC2 instance.
        - Set up a web server and application server.
        - Deploy Django manually or use deployment tools.
    
    2. **Elastic Beanstalk**:
        - Create a new Elastic Beanstalk environment for Django.
        - Upload your application using the Elastic Beanstalk CLI.
        - Configure environment variables and settings.
    
    3. **Amazon Lightsail**:
        - Launch a Lightsail instance with a pre-configured Django environment.
        - Deploy your project similarly to how you would with a standard VPS.

### Continuous Integration and Deployment (CI/CD)

1. **CI/CD Overview****

CI/CD involves automating the process of testing, building, and deploying the application. It helps ensure code quality and streamline deployments.

2. CI/CD Pipeline

- **Automated Testing**: Run tests automatically before deployment.
- **Build**: Ensure the application builds correctly.
- **Deployment**: Deploy the application to your staging or production environment.
- **Monitoring**: Implement monitoring to ensure deployments are successful and the application performs well.

