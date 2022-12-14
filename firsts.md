# First virtual environment

```
mkdir pro && cd pro
pipenv shell
pipenv install django~=3.1.0
```

```
django-admin startproject config .
python manage.py migrate
python mange.py runserver
```
## Know is the time we need to switch to docker by closing virtual environment
## ctrl + c

```
A Docker image is a snapshot in time of what a project contains. It is represented by a Dockerfile
and is literally a list of instructions that must be built. A Docker container is a running instance
of an image. To continue our apartment analogy from earlier, the image is the blueprint or set of
plans for the apartment; the container is the actual, fully-built building.
```

## Create dockerfile
```
touch Dockerfile
```
### Add this to the Dockerfile

```
# Pull base image
FROM python:3.8

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Install dependencies
COPY Pipfile Pipfile.lock /code/
RUN pip install pipenv && pipenv install --system

# Copy project
COPY . /code/
```

```
Dockerfile s are read from top-to-bottom when an image is created.
```

`
Then we use the ENV command to set two environment variables:
• PYTHONUNBUFFERED ensures our console output looks familiar and is not buffered by Docker,
which we don’t want
• PYTHONDONTWRITEBYTECODE means Python will not try to write .pyc files which we also do
not desire
`

`
Next we use WORKDIR to set a default work directory path within our image called code which is
where we will store our code. If we didn’t do this then each time we wanted to execute commands
within our container we’d have to type in a long p
`

`
For our dependencies we are using Pipenv so we copy over both the Pipfile and Pipfile.lock
files into a /code/ directory in Docker.
It’s worth taking a moment to explain why Pipenv creates a Pipfile.lock , too. The concept of
lock files is not unique to Python or Pipenv; in fact it is already present in package managers

for most modern programming languages: Gemfile.lock in Ruby, yarn.lock in JavaScript,
composer.lock in PHP, and so on. Pipenv was the first popular project to incorporate them into
Python packaging.
`

## build the image using the command docker build .)
```
docker build .
```
## create docker-compose file

`
Moving on we now need to create a docker-compose.yml file to control how to run the container
that will be built based upon our Dockerfile image.
`
```
touch docker-compose.yml
```
### put this in to docker-compose file
```
version: '3.8' # Docker Compose which is currently 3.8 .
services:    # containers
  web:
    build: .
    command: python /code/manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - 8000:8000
    depends_on:
      - db

  db:
    image: postgres:11
    environment:
      - "POSTGRES_HOST_AUTH_METHOD=trust"
```

`
Then we specify which services (or containers) we want to have running within our Docker host.
It’s possible to have multiple services running, but for now we just have one for web . We specify
how to build the container by saying, Look in the current directory . for the Dockerfile . Then
within the container run the command to start up the local server.

Then we specify which services (or containers) we want to have running within our Docker host.
It’s possible to have multiple services running, but for now we just have one for web . We specify
how to build the container by saying, Look in the current directory . for the Dockerfile . Then
within the container run the command to start up the local server.
`

## The final step is to run our Docker container using the command (docker-compose up)
```
docker-compose up
```

```
docker-compose down
```

# Conclusion
#   Docker
`
Docker is a self-contained environment that includes everything we need for local development:
web services, databases, and more if we want. The general pattern will always be the same when
using it with Django:
• create a virtual environment locally and install Django
• create a new project
• exit the virtual environment
• write a Dockerfile and then build the initial image
. write a docker-compose.yml file and run the container with docker-compose up
`

# Normally I don’t recommend running migrate on new projects until after a custom user model
has been configured.

# Detached mode runs containers in the background

```
docker-compose up -d
```

# docker-compose logs to see the current output and debug any issues
```
docker-compose log
```

# docker-compose exec web python manage.py createsuperuser

```
Now it’s time to switch over to PostgreSQL for our project which takes three additional steps:
• install a database adapter, psycopg2 , so Python can talk to PostgreSQL
• update the DATABASE config in our settings.py file
• install and run PostgreSQL locally
```

`
Now run docker-compose up -d which will rebuild our image and spin up two containers, one
running PostgreSQL within db and the other our Django web server.
.
`.