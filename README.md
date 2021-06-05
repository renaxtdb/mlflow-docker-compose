# mlflow-docker-compose
Deploy mlflow with docker-compose

## 1. Create .env file
In `docker-composa.yaml`, some parameters is loaded from `.env` file.
Set following parameters in `.env`.

```
USER_NAME = <user name>
COMPOSE_PROJECT_NAME=PJ_mlflow

# Mount volume path
MOUNT_PATH = <mount path>

# jupyter port setting
JUPYTER_PORT_NO = 8819

# docker image version
PYTHON_VERSION = 3.7
DEBIAN_VERSION = slim-buster

# hasura config
PREFECT_SERVER__HASURA__ADMIN_SECRET=<PREFECT_SERVER__HASURA__ADMIN_SECRET>

# Minio config
MINIO_ACCESS_KEY=<MINIO_ACCESS_KEY>
MINIO_SECRET_KEY=<MINIO_SECRET_KEY>
MINIO_MOUNT_PATH=<MINIO_MOUNT_PATH>
MINIO_PORT=9000

#container resources
CONTAINER_LIMIT_MEMORY = 8g
CONTAINER_USE_CPU = 2

# postgresql config
POSTGRES_USER = <POSTGRES_USER>
POSTGRES_PASSWORD = <POSTGRES_PASSWORD>


##### Automatically generated environment parameters
MINIO_URL = http://minio:${MINIO_PORT}

# prefect config
PREFECT_SERVER_TAG="latest"
# Using exact version because of https://github.com/PrefectHQ/ui/issues/798
PREFECT_UI_TAG="2021-02-23"

# hasura config
PREFECT_SERVER__TELEMETRY__ENABLED="false"
PREFECT_SERVER_DB_CMD="prefect-server database upgrade -y"

#postgresql
POSTGRES_POERT=5432
POSTGRES_DB_NAME=mlflow_db
DB_URL = postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@postgresql:5432/${POSTGRES_DB_NAME}


ARTIFACT_PATH = s3://default/

```

## 2. Build and deploy
Build mlflow Dockerfilw, and then deploy applications.

```sh
$ docker-compose build
$ docker-compose up -d
```

## 3. Access Jupyter and Mlflow UI

Juptrer Lab
http://localhost:8819
Mlflow
http://localhost:5000



## Notes
Created with reference to https://github.com/flavienbwk/prefect-docker-compose
