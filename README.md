# Dockerized MySQL - CSE 412 Group 5

A project to create a dockerized MYSQL instance to be used for testing by Group 5 of CSE 412.

## How to stand up a MySQL instance

1. Install Docker Desktop. You can get it [here](https://www.docker.com/products/docker-desktop/).
   Make sure you restart your system to ensure it gets fully installed.

2. From this project's main directory, run the following in your terminal of choice:

   ```bash
   docker pull mysql:latest

   docker-compose up -d
   ```

Congrats! You now have a fully functioning MySQL instance running on `127.0.0.1:3306`. You can login 
to it as the root user, with password 'password'.

A quick note: `docker-compose.yaml` already creates a database inside the container, entitled `db`. 
You can use it (by inclucing `USE db;` in the top of all your SQL queries and workspaces), or you can
create a new one if you want.

When you're done, you can stop the container through Docker Desktop, or you can run:

```bash
docker-compose down
```

## How to import the sample data

MySQL's implementation of CSV imports is really, _really_ bad. Plus, with dates involved,
some data would have gotten lost anyway.

To import the data, grab the sheets Excel sheets contained in the `data_sheets` directory. 
Then, head over to [sqlizer.io](https://sqlizer.io/) and drop each sheet in.

*IGNORE THE SCHEMA IT GIVES YOU*, since we're writing our own. Instead, just grab the second 
block of SQL code it gives you, which adds data to the existing schemas. You can execute this
schema from MySQL Workbench, or directly inside the container.