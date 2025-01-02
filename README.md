# ELT Project

Repository contains a custom ELT (Extract, Load, Transform) project that applies PostgreSQL and Docker.

## Structure

1. **elt_script/Dockerfile**: Dockerfile sets up a Python environment and installs the PostgreSQL client. It copies the ELT script into the container and defines it as the default command.

2. **elt_script/elt_script.py**: Python script performs the ELT process. It waits for the source PostgreSQL database to become available, then dumps its data to a SQL file and loads the data into the destination PostgreSQL database.

3. **docker-compose.yaml**: File contains the configuration for Docker Compose, which is used to orchestrate multiple Docker containers. It specifies three services:
   - `source_postgres`: Source PostgreSQL database.
   - `destination_postgres`: Destination PostgreSQL database.
   - `elt_script`: Service running the ELT script.

4. **source_db_init/init.sql**: SQL script initializes the source database with sample data. Script creates tables for users, films, film categories, actors, and film actors, and inserts sample data into the tables.

## How It Works

1. **Docker Compose**: The `docker-compose.yaml` file is used to create three Docker containers:
   - A source PostgreSQL database with sample data.
   - A destination PostgreSQL database.
   - A Python environment that runs the ELT script.

2. **ELT Process**: The `elt_script.py` waits for the source PostgreSQL database to become available. When available, the script uses `pg_dump` to dump the source database to a SQL file. After that the script uses `psql` to load this SQL file into the destination PostgreSQL database.

3. **Database Initialization**: The `init.sql` script initializes the source database with sample data. It creates several tables and populates them with sample data.

## Getting Started

1. Docker and Docker Compose have to be installed on your machine locally.
2. Clone the repository.
3. Navigate to the repository directory (on CLI, terminal) and run `docker-compose up`.
4. First, all containers are built up and then running. After that, the ELT process starts automatically.
5. When the ELT process is completed, the source and destination PostgreSQL databases can be accessed on ports 5433 and 5434, respectively.
