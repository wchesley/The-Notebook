# C3T

## TODO: 
- CRUD Layer for models
	- essentially write views with code to create, read, update, delete objects defined in the models
- docker deployment
	- needs documentation
	- need babbs docker file
	- example docker file for postgres: 
	```yaml
	version: '12'

	services:

	db:
      image: postgres
      restart: always
      environment:
	    POSTGRES_USER
        POSTGRES_PASSWORD: example

	adminer:
      image: adminer
      restart: always
      ports:
        - 8080:8080
```