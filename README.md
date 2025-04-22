# Basic User Data Management API with Django

## Overview

This project is a RESTful API built using the Django framework in Python to manage user data. It implements CRUD operations, providing a structured and efficient way to handle user information.

## Key Features

* **User Creation:** Allows for the creation of new user records, including fields for username and age.
* **User Retrieval:** Enables fetching details of individual users and retrieving a list of all users.
* **User Update:** Provides functionality to modify existing user information.
* **User Deletion:** Implements the ability to remove user records from the database.

## Technologies Used

* [Python](https://www.python.org/)
* [Django](https://www.djangoproject.com/)
* [Django REST Framework](https://www.django-rest-framework.org/)

## Setup Instructions

1.  Make sure you have Python installed (`python --version` or `python3 --version`).
2.  Install Pip (Python's package manager).
3.  Install Django and Django REST framework:

    ```bash
    pip install django djangorestframework
    ```

4.  Start a new Django project (you might have already done this):

    ```bash
    django-admin startproject newproject
    cd newproject
    ```

    (If you named your project something other than `newproject`, use that name.)

5.  Create a new app within your Django project (you might have already done this):

    ```bash
    python3 manage.py startapp api
    ```

    (If you named your app something other than `api`, use that name.)

6.  Register `rest_framework` and your new app in the `INSTALLED_APPS` array in your project's `settings.py` file. It should look something like this:

    ```python
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'rest_framework',
        'api',  # Or whatever you named your app
    ]
    ```
7.  Define your User model in `api/models.py` (or your app's `models.py` file) with `name` (CharField with `max_length=100`) and `age` (IntegerField).
8.  Create database tables:

    ```bash
    python3 manage.py makemigrations api
    python3 manage.py migrate
    ```

    (If you named your app differently, replace `api` in the `makemigrations` command.)
    
10.  Run the development server:

    ```bash
    python3 manage.py runserver
    ```

## API Endpoints

* `GET /api/users/`: Retrieves a list of all users.
* `POST /api/users/create/`: Creates a new user.
    * **Request body:** JSON object with `name` (string) and `age` (integer) fields.
* `GET /api/users/<id>/`: Retrieves a specific user by ID (replace `<id>` with the user's ID).
* `PUT /api/users/<id>/`: Updates an existing user (replace `<id>` with the user's ID).
    * **Request body:** JSON object with fields to update (e.g., `{"age": 47}`).
* `DELETE /api/users/<id>/`: Deletes a specific user (replace `<id>` with the user's ID).

## Usage Example

To create a new user, you would typically use a tool like `curl` or Postman to send a POST request to `http://127.0.0.1:8000/api/users/create/` with the following JSON data in the request body:

```json
{
    "name": "John Doe",
    "age": 30
}
