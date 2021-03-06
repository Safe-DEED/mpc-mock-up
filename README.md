 # mpc-mock-up
This repository contains resources part of master thesis research conducted by M. Petronia at Delft University of Technology. The thesis can be viewed [HERE](https://repository.tudelft.nl/islandora/object/uuid%3Ab0de4a4b-f5a3-44b8-baa4-a6416cebe26f?collection=education).

## Features

- Django 3.6+
- Uses [Pipenv](https://github.com/kennethreitz/pipenv) - the officially recommended Python packaging tool from Python.org.
- Development, Staging and Production settings with [django-configurations](https://django-configurations.readthedocs.org).
- Get value insight and debug information while on Development with [django-debug-toolbar](https://django-debug-toolbar.readthedocs.org).
- Collection of custom extensions with [django-extensions](http://django-extensions.readthedocs.org).
- HTTPS and other security related settings on Staging and Production.
- Procfile for running gunicorn with New Relic's Python agent.
- PostgreSQL database support with psycopg2 (provision).

## How to install

- Clone repository
- Create and activate virtual environement 
- Install prerequisites:

```bash
$ pip install -r requirements/local.txt
```

- Include own stylesheets or include Klorofil stylesheets (CSS, JS, etc) (recommended). The klorofil files can be found [HERE](https://www.themeineed.com/downloads/klorofil-free-bootstrap-admin-template/). See overview of static files to be included in sitWolf/mpc-mock-up/smpc_demo_platform/templates/base_main.html. For more information, please send an email to masud.petronia@gmail.com
- Run the application:

```bash
$ python manage.py runserver
```

## Deployment

It is possible to deploy to Heroku or to your own server.

## Deployment Environment variables

The variables are common between environments. The `ENVIRONMENT` variable loads the correct settings, possible values are: `DEVELOPMENT`, `STAGING`, `PRODUCTION`.

```
ENVIRONMENT='DEVELOPMENT'
DJANGO_SECRET_KEY='dont-tell-eve'
DJANGO_DEBUG='yes'
```

These settings (and their default values) are only used on staging and production environments.

```
DJANGO_SESSION_COOKIE_SECURE='yes'
DJANGO_SECURE_BROWSER_XSS_FILTER='yes'
DJANGO_SECURE_CONTENT_TYPE_NOSNIFF='yes'
DJANGO_SECURE_HSTS_INCLUDE_SUBDOMAINS='yes'
DJANGO_SECURE_HSTS_SECONDS=31536000
DJANGO_SECURE_REDIRECT_EXEMPT=''
DJANGO_SECURE_SSL_HOST=''
DJANGO_SECURE_SSL_REDIRECT='yes'
DJANGO_SECURE_PROXY_SSL_HEADER='HTTP_X_FORWARDED_PROTO,https'
```

Production variables. Also include in Heroku.

```
DJANGO_ADMIN_URL 'enter URL'
DJANGO_ALLOWED_HOSTS = 'heroku app name'
DJANGO_AWS_ACCESS_KEY_ID = 'Amazon AWS S3 bucket access ID'
DJANGO_AWS_SECRET_ACCESS_KEY = 'Amazon AWS S3 bucket access key'
DJANGO_AWS_STORAGE_BUCKET_NAME = 'Amazon AWS S3 bucket name'
DJANGO_DEBUG = 'False'
DJANGO_SECRET_KEY = 'Django secret key'
DJANGO_SETTINGS_MODULE config.settings.production
HEROKU_POSTGRESQL_GRAY_URL = 'Heroku PostgresSQL url'
PYTHONHASHSEED = 'random'
REDIS_URL = 'redis://redis:6379/0'
WEB_CONCURRENCY = '4'
```

### Heroku

```bash
$ heroku create
$ heroku addons:add heroku-postgresql:hobby-dev
$ heroku pg:promote DATABASE_URL
$ heroku config:set ENVIRONMENT=PRODUCTION
$ heroku config:set DJANGO_SECRET_KEY=`./manage.py generate_secret_key`
```
## Preview

![Screenshot](MPC-mock-up.png)

## License

The BSD 3-Clause License

Copyright (c) 2020 Masud Petronia

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## Funding

The development of this mockup has received funding from the European Union’s Horizon 2020 Research and Innovation Programme, under Grant Agreement no 825225 – Safe Data Enabled Economic Development [(SAFE-DEED)](https://safe-deed.eu/), from the H2020-ICT-2018-2 Call.

![Screenshot](Safe-DEED.png)
