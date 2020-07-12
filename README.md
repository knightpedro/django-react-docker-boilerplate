# Django-React Docker Boilerplate

Boilerplate for creating a containerised Django/React app with Postgres database.

Based on https://docs.docker.com/compose/django/.

## Setup

```
docker-compose run backend python manage.py migrate
docker-compose up
```

## Steps to create

### Django Backend

1. Create backend folder
2. Add _requirements.txt_ with Django & Postgres adapter dependencies.
3. Add Dockerfile

### React Frontend

1. In project root, run Create React App

```
npx create-react-app frontend [--template typescript]
```

2. Add Dockerfile

### Docker Compose

Create docker-compose file with separate services for the database, backend and frontend.

Note for the development server to run tty: true needs to be set on the frontend service. See https://github.com/facebook/create-react-app/issues/8688.

Create Django project

```
docker-compose run backend django-admin startproject mysite .
```

Setup connection to Postgres database in Django project settings

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

Run Django migrations

```
docker-compose run backend python manage.py migrate
```
