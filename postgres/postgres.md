# Postgres
Link to [Postgres 12 Documentation](https://www.postgresql.org/docs/12/index.html)  
## Installation: 
### Debian: 
Debian includes postgres in their apt repository, however, pgadmin4 was not in there for me
- add postgres respository: 
```bash
# Create the file repository configuration:
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

# Import the repository signing key:
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# Update the package lists:
sudo apt-get update
```
- Then install postgres: 
```bash
# Client files: 
sudo apt-get install postgresql-client-12

# Server files: 
sudo apt-get install postgresql-12

# Pgadmin4
sudo apt-get install pgadmin4
```
### Create a user: 
Activate postgres shell, type `sudo -u postgres psql`  
This will bring up a shell running as the default postgres user. From there we can add more users:  
```bash
$ createuser --interactive joe
```
Where Joe is our new users name. `--interactive` will guide you through the process of creating a user, defining roles, priveledges and setting a password in a step by step manner.   
Reference: [here](https://www.postgresql.org/docs/12/app-createuser.html)

## Drop and recreate public
I have the habit, during my development with django, of changing the models in ways that prevents updating the database or does so in an un-clean way. That looks like me not being able to run migrations or not applying migrations. Rather than drop one table at a time this script will drop the public schema and recreate it: 
```postgres
DROP SCHEMA public CASCADE;
CREATE SCHEMA public;
GRANT ALL ON SCHEMA public TO postgres;
GRANT ALL ON SCHEMA public TO wchesley;
GRANT ALL ON SCHEMA public TO public;
```