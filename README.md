# Conduit-Container

This repository contains a fully containerized deployment of the Conduit Application.The goal of this setup is to provide a reproducible, secure, and production‑ready environment according to modern DevOps and containerization standards.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Quickstart](#Quickstart)
- [Usage](#Usage)

## Prerequisites

- Docker engine
- Docker compose

## Quickstart

- Clone the repository

```bash
git clone https://github.com/FlyingChris1/Conduit-Container.git
cd Conduit-Container
```


- Convert example.env into .env

Please change the .env variables before creating the .env, due to security reasons
```bash
cp example.env .env
```

- Start Docker compose 

```bash
docker compose up --build -d
```

- check if your application is up and running

```bash
http://<your_server_ip>:8282
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