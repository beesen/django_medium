# django_medium
# Get Started with Postgres + Django => https://medium.com/@jaredblackjcb/get-started-with-postgres-django-8f79d78fc3771
create file called .env
.env
`# Database Connection Info
DJANGO_DATABASE_NAME='your_database_name'
DJANGO_DATABASE_USER='your_user'
DJANGO_DATABASE_PASSWORD='your_password'
DJANGO_DATABASE_HOST='localhost'
DJANGO_DATABASE_PORT='5432'`

settings.py
`import environ

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
}`