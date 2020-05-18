# Readme

This is a basic blank Setup for Django projects. My vision is a Django plugin system which is not done by clicking on download, but by inserting single code snippets. This should contribute to the dynamics as well as the understanding of code and functions.

# Table of Content
* [Setup Guide](#setupguide)
	* [Organization](#setupguide_system)
	* [Django](#setupguide_django)
		* [modify .env-file](#setupguide_django_env)
		* [settings](#setupguide_django_settings)
			* [env_file](#setupguide_django_settings_import_env)
			* [secret_key](#setupguide_django_settings_secret_key)
			* [rest_framework]('#setupguide_django_settings_restframework)
			* [cors_headers](#setupguide_django_settings_corsheaders)
			* [postgres](#setupguide_django_settings_postgres)
* [Snippets](#snippets)

<a href="#setupguide"></a>
# Setup Guide
This Guide is structured in two parts:
1. organize your data by moving them to the right place and use the correct setup
2. manipulate your existing project for using that basic setup

<a href="#setupguide_system"></a>
## Setup Guide (System Part)
(1) Clone the Repository:

    git clone https://github.com/JangasCodingplace/snippet_basic_project_setup.git
   
(2) copy the following Files to your blank project:
manage.py, env.example, .gitignore, requirements.txt

(3) open your project in your console
```
    cd {PATH TO ROOT OF PROJECT}
```
(4) create a virtual environment
Linux / Mac:
```
    python3 -m venv venv
```
Windows:
```
    python -m venv venv
```
(5) start virtual environment
Linux / Mac:
```
    source venv/bin/activate
```
Windows:
```
    venv\Scripts\activate.bat
```
(6) upgrade pip
```
    pip install --upgrade pip
```
(7) install requirements
```
    pip install -r requirements.txt
```
(8) create .env file:
```
    cp .env.example .env
```

<a href="#setupguide_django"></a>
## Setup Guide (Django Part)
<a href="#setupguide_django_env"></a>
### Edit .env-File
Modify variable `DJANGO_SETTINGS_MODULE` and change it to the path of your settings.py File.

<a href="#setupguide_django_settings"></a>
### Edit settings.py

<a href="#setupguide_django_settings_import_env"></a>
#### Import env_file
import module `env_file` at the head of your document:
```
    import env_file
```

<a href="#setupguide_django_settings_secret_key"></a>
#### secret key changes
Copy your SECRET_KEY and put it into the .env File.
Change your SECRET_KEY in your settings.py file to
```
    SECRET_KEY = ENV['SECRET_KEY']
```

<a href="#setupguide_django_settings_restframework"></a>
#### Restframework
Add `'rest_framework'` to your `INSTALLED_APPS` setting
```
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```
For additional informations please use the documentation of [Django Restframework](https://www.django-rest-framework.org)

<a href="#setupguide_django_settings_corsheaders"></a>
#### Corsheaders
Add `'corsheaders'` to your `INSTALLED_APPS` setting
```
INSTALLED_APPS = [
    ...
    'corsheaders',
]
```
You will also need to add a middleware class to listen in on responses:
```
MIDDLEWARE = [
    ...
    'corsheaders.middleware.CorsMiddleware',
]
```
Add following lines to your settings.py file:
```
    CORS_ORIGIN_ALLOW_ALL = True
    CORS_ALLOW_CREDENTIALS = True
```
Note: This is just for testing. I recommend to specify your cors_headers hosts and credentials for Production.

For additional informations I refer to [django-cors-headers](https://pypi.org/project/django-cors-headers/)

<a href="#setupguide_django_settings_postgres"></a>
#### PostgresQL
The default database in that project is sqlite3. You can simply change it by following the Introductions at the settings File.
I recommend to store the Database Settings in your .env File. The example does already force it. You simply have to change the strings.
If you want to use a Postgres Database please Delete the uncomment default sqlite3 Database and use the following for your `DATABASES`:
```
    DATABASES = {
	    'default': {
		    'ENGINE': 'django.db.backends.postgresql',
		    'NAME': ENV['DBNAME'],
		    'USER': ENV['DBUSER'],
		    'PASSWORD': ENV['DBPASSWORD'],
		    'HOST':ENV['DBHOST'],
		    'PORT':ENV['DBPORT'],
		}
	}
```

<a href="#snippets"></a>
# Snippets
Here is a Linguist by Snippets by me which are matching to this Guide and you could implement into this basic project setup.