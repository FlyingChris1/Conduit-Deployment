# Conduit-Container

This repository contains a Conduit Deployment project. It includes a fully containerized frontend and backend application, configured for deployment on a cloud VM using Docker Compose. The project aims to provide a reproducible and scalable environment for running Conduit, with persistent data storage and automated deployment workflows.


## Table of Contents

- [Prerequisites](#prerequisites)
- [Quickstart](#Quickstart)
- [Usage](#Usage)

## Prerequisites

- Docker engine
- Docker compose
- Ready to use VM or Server

## Quickstart

- Clone the repository

```bash
git clone https://github.com/FlyingChris1/Conduit-Deployment.git
cd Conduit-Deployment
```

- Convert example.env into .env

Please change the .env variables before creating the .env, due to security reasons
```bash
cp example.env .env
```

- Setup the SSH Key

```bash
ssh-keygen -t ed25519
```

- Add the pub key to authorized keys

```bash
cat .ssh/id_ed25519.pub | ssh user@host 'cat >> .ssh/authorized_keys'

```

- Add your sensitive information into Github secrets

```bash
https://github.com/<your Github name>/<your project>/settings/secrets/actions

```

- Check your workflow on Github actions

```bash
git add .
git commit -m "<your message>"
git push
```
## Usage

- restart Container

```bash
docker compose restart
```

- stop Container

```bash
docker compose down -v
```

- Enter Conduit-Backend Container

```bash
docker compose exec -it backend bash
```

- Enter Conduit-Frontend Container

```bash
docker compose exec frontend sh
```

- Get Docker Compose logs

```bash
docker compose logs
```

- Create an admin Login

```bash
python manage.py createsuperuser
```

- Remove Container and boot it up again

```bash
docker compose down -v
docker compose up --build -d
```

- Check what containers are up

```bash
docker ps
```

- monitor resource usage

```bash
docker stats
```