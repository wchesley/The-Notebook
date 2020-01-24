# C3T

## TODO: 
- CRUD Layer for models
	- essentially write views with code to create, read, update, delete objects defined in the models
- docker deployment
	- needs documentation
	- test deployment
		- postgres works
	- need babbs docker file
	- example docker file for postgres: 
```yaml
	version: '3.7'

	services:

	db:
      image: postgres
      restart: always
      environment:
	    POSTGRES_USER: wchesley
        POSTGRES_PASSWORD: example

	adminer:
      image: adminer
      restart: always
      ports:
        - 8080:8080
```

To get running: 
comment out postgres connnections in settings.py
uncomment sqlite settings
```python
DATABASES = {
    'default': {
         'ENGINE': 'django.db.backends.sqlite3',
         'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        # 'ENGINE': 'django.db.backends.postgresql',
        # 'NAME': 'postgres',
        # 'USER': 'postgres',
        # 'PASSWORD': 'postgres',
        # 'HOST': 'db',
        # 'PORT': 5432
    }
}
```

Set dev secret key `SECRET_KEY = "SECRET_KEY" #os.environ.get('SECRET_KEY')`
Install cripsy forms and all auth
`pip install django-allauth`
`pip install django-cripsy-forms`

after the above is installed: run `python manage.py migrate` to set up the database
run `python manage.py runserver` to start the server. 