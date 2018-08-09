---
description: >-
  Docker Compose automates the configuration, provisioning and execution of
  Cortex CMS on a single machine. Follow this guide to quickly get started with
  Cortex CMS.
---

# Docker Compose

## Environment Preparation

Install `docker` and `docker-compose` using the [installer](https://docs.docker.com/compose/install/#install-compose) or via your Operating System's package manager \(`pacman`, for example\), then launch the service.

## `cortex-starter` Preparation {#cortex-starter-prep}

As `cortex` itself is only a Rails Engine, it needs to be mounted within a parent Rails applicaton. [cortex-starter](https://github.com/cortex-cms/cortex-starter) serves as a starting point for new users, with `cortex` and `cortex-plugins-core` already mounted and configured with several example `ContentTypes`/`Decorators`. Start by cloning the repository:

```bash
$ git clone git@github.com:cortex-cms/cortex-starter.git && cd cortex-starter
```

## Provision & Launch Application

Provision and launch Cortex Starter, PostgreSQL, Redis, ElasticSearch, Sidekiq and live Webpack rebuild via Docker Compose:

```bash
$ docker-compose up
```

Once complete, the admin interface will be accessible locally at `http://localhost:3000`. To access Cortex CMS as superadmin, login as `admin@cortexcms.org` with password `welcome1`.

