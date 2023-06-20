# Docker WordPress Environment

This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/) and [phpMyAdmin](https://www.phpmyadmin.net/).

> **Disclaimer:** This project is meant to be used for development purposes only. It's **not** meant to be used in production.

> It's work in progress. Feel free to contribute if you have anything useful to add.

---

## Usage

Clone this repository, then run run `docker-compose up -d` to start your project.

## Services

- **db**

The MYSQL official image

- **phpMyAdmin**

Intended to handle the administration of MySQL, in this case through [localhost:8080/](localhost:8080/).

- **WordPress**

Uses the official WordPress docker image

- **WP-CLI**

The **wpcli container** was added in order to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`
