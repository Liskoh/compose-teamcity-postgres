
# TeamCity + PostgreSQL Skeleton

This project provides a skeleton setup for quickly configuring a TeamCity instance with a PostgreSQL database using Docker Compose.

## Requirements

Before you start, make sure you have the following installed on your system:
- Docker
- Docker Compose

You can check if Docker and Docker Compose are installed by running:

```bash
docker --version
docker-compose --version
```

If these commands return versions, you are ready to proceed. If not, please install Docker and Docker Compose following the instructions on the [official Docker website](https://docs.docker.com/get-docker/).

## Initial Setup

1. Clone the repository or download the files into a directory of your choice.

2. Rename the `.env.example` file to `.env` and update the environment variables according to your configuration.

```bash
mv .env.example .env
```

3. Open the `.env` file and change the variable values to match your needs. Here are the variables you will need to configure:

- `TEAMCITY_SERVICE_NAME`: The name of the TeamCity service.
- `TEAMCITY_PORT`: The port on which TeamCity will be accessible.
- `POSTGRES_DB`: The name of the PostgreSQL database.
- `POSTGRES_USER`: The database user.
- `POSTGRES_PASSWORD`: The password for the database user.

## Launching TeamCity and PostgreSQL

To build and start the TeamCity and PostgreSQL containers, run the following command:

```bash
docker-compose up --build
```

This command will download the necessary images, create the containers, and start the services. You can access TeamCity in your browser by visiting `http://localhost:<TEAMCITY_PORT>` where `<TEAMCITY_PORT>` is the port you configured in the `.env` file.

## Accessing TeamCity

After launching, open your browser and go to `http://localhost:<TEAMCITY_PORT>` to start the TeamCity setup. Follow the on-screen instructions to connect TeamCity to the PostgreSQL database.

## Stopping Services

To stop the containers, use the following command:

```bash
docker-compose down
```

## Important Notes

- Data is persisted using Docker volumes. You will find TeamCity's data in the named volume `teamcity_data` and PostgreSQL data in `postgres_data`.
- If you encounter database connection issues from TeamCity, ensure that the database hostname in TeamCity is set to `postgres` and not `localhost` or `127.0.0.1`.

If you have any questions or issues, please refer to the documentation of TeamCity and PostgreSQL, or open an issue in this repository.

---

Happy building and deploying with TeamCity and PostgreSQL!
