# MasteringDjango

## Setting up Django with Docker Compose

Create a new file file called `Dockerfile`.

The Dockerfile defines an application's image content via one or more build commands that configure that image.
Once built, you can run the image in a container.

[Dockerfile](Dockerfile)

This `Dockerfile` starts with a Python 3 base image.
The base image is modified by adding a new `code` directory.

The base image is further modified by installing the Python requirements defined in the `requirements.txt` file.

[requirements.txt](requirements.txt)

Create a `docker-compose.yml` file to describe the services that make your app.

[docker-compose.yml](docker-compose.yml)

Run to generate a new Django project:
```
$ docker-compose run web django-admin.py startproject composeexample .
```

Only Django would be:
```
$ django-admin startproject mysite
```

To run django:

```
$ docker-compose up
```

Generated files:

* manage.py - A command-line utility that lets you interact with your Django project.
* mysite/__init__.py - an empty file that tells Python that this directory should be considered a Python package.
* mysite/settings.py - settings configurations for this projects.
* mysite/urls.py - the URL declarations for this project.
* mysite/wsgi.py - an entry-point for WSGI-compatible web servers to serve your project.

### Django settings

By default settings.py comes with some installed apps.

Some of these applications uses at least one database table.

```
$ docker-compose up
$ docker ps
# find the container's id of your Django app
$ docker exec -t -i 66175bfd6ae6 bash
$ python manage.py migrate
```
