+++
title = 'How to create a PostgreSQL database in Django'
date = 2024-01-21T22:14:54+05:30
draft = false
+++


## Setting up PostgreSQL Database and User

In this blog post, we'll walk through the steps to set up a PostgreSQL database and user with the following commands.

## Step 1: Create a PostgreSQL Database

```sql
CREATE DATABASE yourdbname;
```

This command creates a new PostgreSQL database named yourdbname.

## Step 2: Create a PostgreSQL User

```sql
CREATE USER yourdbuser WITH PASSWORD 'yourdbpassword';
```

This command creates a new PostgreSQL user named yourdbuser with the specified password.

## Step 3: Configure User Encoding

```sql
ALTER ROLE yourdbuser SET client_encoding TO 'utf8';
```

This command sets the character encoding for the user yourdbuser to 'utf8'.

## Step 4: Configure Transaction Isolation

```sql
ALTER ROLE yourdbuser SET default_transaction_isolation TO 'read committed';
```

This command sets the default transaction isolation level for the user yourdbuser to 'read committed'.

<!-- ## Step 5: Grant Permissions

```sql
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO yourdbuser;
``` -->

## Step 5: Configure Timezone

```sql
ALTER ROLE yourdbuser SET timezone TO 'UTC';
```

This command sets the timezone for the user yourdbuser to 'UTC'.

## Step 6: Set Database Owner

```sql
ALTER DATABASE yourdbname OWNER TO yourdbuser;
```

This command sets the owner of the database yourdbname to the user yourdbuser.

## Step 7: Connect to Django

### Add these lines to settings.py

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": config.get("DB_NAME"),
        "USER": config.get("DB_USER"),
        "PASSWORD": config.get("DB_PASSWORD"),
        "HOST": config.get("DB_HOST"),
        "PORT": config.get("DB_PORT"),
    }
}
```

### Configure environment variables

```env
DB_HOST =
DB_NAME =
DB_USER =
DB_PORT =
DB_PASSWORD =
```

## All SQL Commands in one line

```sql
CREATE DATABASE yourdbname;
CREATE USER yourdbuser WITH PASSWORD 'yourdbpassword';
ALTER ROLE yourdbuser SET client_encoding TO 'utf8';
ALTER ROLE yourdbuser SET default_transaction_isolation TO 'read committed';
ALTER ROLE yourdbuser SET timezone TO 'UTC';
ALTER DATABASE yourdbname OWNER TO yourdbuser;
```

## Conclusion

You have successfully set up a PostgreSQL database named yourdbname and created a user yourdbuser with the specified configurations. This database and user are now ready to be used for your applications.

Feel free to explore more PostgreSQL features and functionalities as you continue your journey with databases.

Happy coding!
