# Docker WordPress Environment

This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/), [phpMyAdmin](https://www.phpmyadmin.net/) and [Xdebug](https://xdebug.org/).
This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/), [phpMyAdmin](https://www.phpmyadmin.net/) and [Xdebug](https://xdebug.org/).

## Table of Contents

- [Introduction](#docker-wordpress-environment)
  - [Services](#services)
- [Requirements](#requirements)
- [Usage](#usage)
  - [Variables](#variables)
- [Contributing and Support](#contributing-and-support)

## Table of Contents

- [Introduction](#docker-wordpress-environment)
  - [Services](#services)
- [Requirements](#requirements)
- [Usage](#usage)
  - [Variables](#variables)
- [Contributing and Support](#contributing-and-support)

---

> **Disclaimer:** This project is meant to be used for development purposes only. It's **not** meant to be used in production.

---

### Services

Docker services used on [docker-compose. yml](https://github.com/sarahcssiqueira/docker-wordpress/blob/master/docker/docker-compose.yml):

- **db**

The MYSQL official image.

- **phpMyAdmin**

Intended to handle the administration of MySQL, in this case through port 80, on browser [localhost:8080/](localhost:8080/).

- **WordPress**

Uses the official WordPress latest docker image.

- **WP-CLI**

The **wpcli container** was added to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`

## Requirements

- [Docker](https://www.docker.com/) hub installed.

## Usage

Clone this repository, then cd the **docker folder** and run `docker-compose up -d` to start your project.

## Services

- **db**

The MYSQL official image.

- **phpMyAdmin**

Intended to handle the administration of MySQL, in this case through port 80, on browser [localhost:8080/](localhost:8080/).

- **WordPress**

Uses the official WordPress latest docker image.

- **WP-CLI**

The **wpcli container** was added to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`
