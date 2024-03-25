# Docker Compose configuration for the installation of Tonic Textual
Deploying Tonic via docker-compose is a relatively straightforward process. This repository contains an example/template docker-compose.yaml which can be used for this.
Project structure:
```
.
├── sample.env
├── docker-compose.yaml
├── docker-compose-with-gpus.yml
└── README.md
```

## Configuration

### .env

Before deploying this setup, you need to rename sample.env to .env and configure the following values, or set the environment variables directly within docker-compose.yaml. Please note that variables outside of the ones referenced below are option. Reach out to support@tonic.ai with any questions.

### Environment Name

* ENVIRONMENT_NAME: E.g. "my-company-name", or if deploying multiple Tonic instances, "my-company-name-dev" or "my-company-name-prod to differentiate instances.

### Version

* SOLAR_VERSION: A specific version tag. Tonic's tag convention is just the release number, e.g. “086. The latest version during installation will be supplied by Tonic.

### Application Database

The connection details for the Postgres metadata/application database which holds Tonic's state (user accounts, workspaces, etc.).
* SOLAR_DB_HOST
* SOLAR_DB_PORT
* SOLAR_DB_DATABASE
* SOLAR_DB_USERNAME
* SOLAR_DB_PASSWORD

By default we're deploying a Postgres DB container, so the only field that requires update is the SOLAR_DB_PASSWORD and the Postgres database will be instantiated upon installation. If you’d prefer, you can provide credentials for a standalone database (i.e. RDS Postgres) and update each of these values accordingly.

### Secret

This value is used as the secret for encryption functionality.
* SOLAR_SECRET: Any string value is valid


## Deploy

To run Tonic, execute the docker-compose up -d command from within the directory containing your docker-compose.yaml file.

` $ docker-compose up -d `


### Validate the deployment

Use docker ps to check that containers are running:

` $ docker ps `


The Tonic UI will be accessible in your browser on port 80 or 443. I.e. from the server at https://localhost:443 or http://localhost, or via the server IP/hostname or domain you are routing to the server.
Tonic may take a few minutes to fully startup. You can validate that it has fully started up and is in a healthy state by running 

` $ docker logs textual-api `
