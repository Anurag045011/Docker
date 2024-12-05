# PostgreSQL Docker Installation and Database Management

## Introduction

PostgreSQL is an open-source, object-relational database system that uses and extends the SQL language. It is known for its reliability, robustness, and scalability, making it one of the most popular database systems for a wide range of applications. PostgreSQL supports both SQL (relational) and JSON (non-relational) querying.

The objective of this project was to **install an open-source database system (PostgreSQL)** using Docker, create a new database, and interact with it by creating tables and inserting data. The final goal was to verify the database using **pgAdmin4**, a web-based tool for managing PostgreSQL databases.

## Learning Objectives

- **Docker**: I learned how to use Docker to run PostgreSQL as a containerized service.
- **PostgreSQL**: I learned how to interact with PostgreSQL using the command line (psql) and **pgAdmin4**.
- **pgAdmin4**: I explored how to verify database creation and manage it via the pgAdmin4 web interface.
- **SQL Commands**: I applied various SQL commands such as `CREATE DATABASE`, `CREATE TABLE`, `INSERT INTO`, and `SELECT`.

## Prerequisites

- **Docker**: Make sure Docker is installed on your system. [Docker Installation Guide](https://docs.docker.com/get-docker/)
- **pgAdmin4**: Optional, for verifying and managing PostgreSQL databases in a GUI. [pgAdmin4 Installation Guide](https://www.pgadmin.org/download/)

## Steps

### 1. Pull the PostgreSQL Docker Image

First, pull the official PostgreSQL Docker image from Docker Hub:

```bash
docker pull postgres
```

This will download the latest version of the PostgreSQL image.

### 2. Run PostgreSQL Container

Start a PostgreSQL container with the following command. The `-d` flag runs the container in detached mode, and the `-p` flag maps port `5432` (default PostgreSQL port) from the container to your host system.

```bash
docker run -d --name postgres-db -p 5432:5432 -e POSTGRES_PASSWORD=anurag postgres
```

- `--name postgres-db`: Names the container `postgres-db`.
- `-p 5432:5432`: Maps the PostgreSQL port from the container to the host machine.
- `-e POSTGRES_PASSWORD=anurag`: Sets the password for the `postgres` user.

### 3. Verify Running Containers

Use the following command to check if the PostgreSQL container is running:

```bash
docker ps
```

This command lists all active Docker containers, where you should see `postgres-db` listed.

### 4. Access PostgreSQL Command Line Interface (psql)

To interact with the PostgreSQL database, execute the following command:

```bash
docker exec -it postgres-db psql -U postgres
```

This command connects you to the `postgres` user within the `postgres-db` container and opens the PostgreSQL command-line interface (`psql`).

### 5. Create Database and Switch to It

Inside the `psql` interface, create a new database called `class`:

```sql
CREATE DATABASE class;
\c class
```

The `\c class` command switches to the `class` database for further operations.

### 6. Create a Table

Create a `students` table with the following columns: `id`, `name`, and `age`:

```sql
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### 7. Insert Data into the Table

Insert some records into the `students` table:

```sql
INSERT INTO students (name, age) VALUES ('Anurag', 24);
INSERT INTO students (name, age) VALUES ('Anjali', 25);
```

### 8. Verify Data in the Table

Verify that the data was inserted correctly by running:

```sql
SELECT * FROM students;
```

This should display the records that were inserted into the `students` table.

### 9. Stop the PostgreSQL Container

Once you're done, you can stop the PostgreSQL container using the following command:

```bash
docker stop postgres-db
```

This will gracefully stop the running PostgreSQL container.

### 10. Remove the PostgreSQL Container

To remove the container, use the following command:

```bash
docker rm postgres-db
```

This will remove the stopped container from Docker.

### 11. Verifying the Database in pgAdmin4

To verify that the `class` database and the `students` table were created, open **pgAdmin4** and connect to your PostgreSQL instance.

- In **pgAdmin4**, create a new connection to the PostgreSQL server.
- Once connected, you will see the `class` database in the left panel.
- Expand the `class` database to see the `students` table.
- You can also run a SQL query in **pgAdmin4** to verify the data:

```sql
SELECT * FROM students;
```
## Video


https://github.com/user-attachments/assets/e58143d1-c422-4f17-ae81-3fe5a8b9062c


## Conclusion

Through this project, I successfully installed PostgreSQL on Docker, created a database, and managed it through both the command line and **pgAdmin4**. This exercise helped me understand how to use Docker for database containerization and how PostgreSQL can be used in both development and production environments. Additionally, I gained experience using pgAdmin4 as a tool for visual database management.

## Future Improvements

- **Backup & Restore**: Learn how to backup and restore PostgreSQL databases in Docker.
- **Advanced Configuration**: Explore advanced PostgreSQL configurations, such as replication and clustering.
- **Docker Compose**: Use Docker Compose to manage multi-container applications and PostgreSQL services.
- 
---

Feel free to customize this further based on your needs, or add any additional sections you feel might be helpful!
