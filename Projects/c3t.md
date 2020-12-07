# C3T

## TODO: 
- Update README with new packages list
- Update Pipfile with new packages
- Create index in postgres for Searches (atm it's for Disposition (term_identifier and description) and Knowledge Elements)
- Create search feature for Dispositions Description and Knowledge Elements in the front end. 
- Competency Creation wizard (Babb handling this?)
- Create Formsets to save Disposition with competency. (Create disposition applied in the backend?)

## Setup: 
**RECOMMENDED** to use Anaconda to manage environment. For windows, also recommended to use WSL (any distro should work, verified working in Ubuntu 16.04+ or Debian 8+)
> For my case I had issues getting another app (otree) updated on my machine, twisted failed to build it's wheel. Worked just fine in WSL.  

- Set postgres connection strings and python env vars from they python shell:  `os.environ.set["name"] = "Value"` Value has to be a string. You can check the value set with `print(os.environ["Name"])`
    - Postgres env vars: 
        - Name
        - User
        - Password
        - Host
        - Port
- Set dev secret key `SECRET_KEY = "SECRET_KEY" #os.environ.get('SECRET_KEY')`
- Install dependencies: 
- `pip install django==3.1.2`
- `psycopg2-binary = "==2.8.6"`
- `django-crispy-forms = "==1.9.2"`
- `django-allauth = "==0.43.0"`
- `whitenoise = "==5.2.0"`
- `gunicorn = "==20.0.4"`
- `dj-database-url = "==0.5.0"`
- `django-taggit 1.3.0`
- `django-autocomplete-light 3.8.1 `


after the above is installed: run `python manage.py migrate` to set up the database  
> Ensure postgres is running

run `python manage.py runserver` to start the server. 