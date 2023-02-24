# django_medium
# How to set up environment variables in Django
Install django-environ
```cmd
$ pip install django-environ
```
Create .env file in the root directory
file: .env
```text
SECRET_KEY=django_secret_key
DATABASE_NAME=your_database_name
DATABASE_USER=your_user
DATABASE_PASSWORD=your_password
DATABASE_HOST=localhost
DATABASE_PORT=5432
```
Add your .env file to .gitignore

file: settings.py
```python
import environ

env = environ.Env()
env.read_env(os.path.join(BASE_DIR,  ".env"))

# Other settings..

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': env('DJANGO_DATABASE_NAME', default='your_app'),
        'USER': env('DJANGO_DATABASE_USER', default='postgres'),
        'PASSWORD': env('DJANGO_DATABASE_PASSWORD', default='***'),
        'HOST': env('DJANGO_DATABASE_HOST', default='localhost'),
        'PORT': env('DJANGO_DATABASE_PORT', default='5432'),
    }
}
```
In terminal:
```cmd
pip install psycopg2
install postgresql on Windows
createdb your_database_name -U postgres
```
