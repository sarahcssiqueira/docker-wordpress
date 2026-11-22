# Docker WordPress Environment

[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Release Version](https://img.shields.io/github/release/sarahcssiqueira/docker-wordpress.svg)](https://github.com/sarahcssiqueira/docker-wordpress/releases/latest)
[![Support Level](https://img.shields.io/badge/support-may_take_time-yellow.svg)](#support-level)

This is a **Docker WordPress Environment** focused on the development of **WordPress plugins and themes**, supports [WP-CLI](https://wp-cli.org/), [phpMyAdmin](https://www.phpmyadmin.net/), [Xdebug](https://xdebug.org/) and [WordPress Coding Standards - WPCS](https://github.com/WordPress/WordPress-Coding-Standards).

---

> **Disclaimer:** This project is meant to be used for development purposes only. It's **not** meant to be used in production.

---

## Table of Contents

- [Introduction](#docker-wordpress-environment)
- [Requirements](#requirements)
- [Docker](#docker)
- [Folders Structure](#folders-structure)
- [Containers](#containers)
- [Basic Usage](#basic-usage)
  - [Set variables](#variables)
  - [Starting Docker](#starting-docker)
- [More Tools](#more-tools)
  - [Set debugging in WordPress](#set-debugging-in-wordPress)
  - [Xdebug for VSCode](#xdebug-for-vscode)
  - [Set WordPress Coding Standards](#set-wordpress-coding-standards)
  - [Using WordPress Coding Standards](#using-wordpress-coding-standards)
- [Contributing and Support](#contributing-and-support)

## Requirements

- [Docker](https://www.docker.com/)
- [VS Code](https://code.visualstudio.com/)
  - [PHP Debug Extension](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)
  - [phpcs](https://github.com/sarahcssiqueira/docker-wordpress/blob/master/.vscode/settings.json)
- [Composer](https://getcomposer.org/)
- [Xdebug](https://xdebug.org/docs/install)

## Docker

### Folders Structure

![docker folder](https://github.com/sarahcssiqueira/docker-wordpress/assets/82296194/eef4010b-9c13-49a8-970b-1a707666defd)

- .vscode
- db
- docker: also install Xdebug and set Xdebug.ini.
- plugins
- themes
- wp-core
- .gitignore
- composer.json
- license
- readme

### Containers

Docker containers used on [docker-compose.yml](https://github.com/sarahcssiqueira/docker-wordpress/blob/master/docker/docker-compose.yml):

- WordPress: Uses the official WordPress image, with WordPress and PHP versions configured in `.env`.
- WP-CLI: The **wpcli container** was added to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run `docker compose run --rm wpcli command`
- db: MySQL 8.0, with its data stored in the `db` folder.
- phpMyAdmin: Intended to handle database administration and is accessible at [localhost:8080](http://localhost:8080).

## Basic usage

Clone (or download) this repository `git clone https://github.com/sarahcssiqueira/docker-wordpress` or download one of the [latest releases](https://github.com/sarahcssiqueira/docker-wordpress/releases).
Go to the `/docker` folder, copy `.env.example` to `.env`, and set your chosen variables there. The `.env` file is ignored by Git; commit changes to `.env.example` if the defaults need updating.

### Set variables

Configure database credentials, WordPress/PHP versions, and debugging options in `.env`:

```
MYSQL_DATABASE_NAME=exampledatabase
MYSQL_USER=exampleuser
MYSQL_PASSWORD=examplepass
WORDPRESS_VERSION=6.8.2
PHP_VERSION=8.3
WORDPRESS_DEBUG=1
XDEBUG_MODE=off
```

### Starting Docker

Choose `WORDPRESS_VERSION` and `PHP_VERSION` in `.env` to test different supported combinations. The database uses the pinned MySQL 8.0 image; back up the `db` folder before changing database versions.
Run `docker compose up -d --build` to build the selected WordPress/PHP image and start the environment.

When Docker finishes their work (can take a few minutes at the first time, depending on your connection and machine), you will see the WordPress default installation screen in your browser.

Finish WordPress installation.

![wp-setup-start](https://github.com/sarahcssiqueira/docker-wordpress/assets/82296194/0ac267b6-b2a6-44c2-aa29-a4092d62b80d)

In your terminal, cd the root project folder again to start working on your plugins and/or themes.

For using wp-cli, use `docker compose run --rm wpcli command` as it was added to only run one-off commands.

🚀 You already can start to work on your themes and plugins, but there are more tools available for using, keep reading.

## ⚙️ More Tools

### Debugging in WordPress

WordPress debugging is configured through `WORDPRESS_DEBUG` and `WORDPRESS_CONFIG_EXTRA` in Compose. Set `WORDPRESS_DEBUG=0` in `.env` to disable it; no edits to generated files in `wp-core` are needed. Recreate the service with `docker compose up -d` after changing the value.

More info about **debugging in WordPress** you can find [here](https://wordpress.org/documentation/article/debugging-in-wordpress/).

### Xdebug for VSCode

Xdebug 3.4.2 is installed in the Docker image. It is disabled by default to avoid slowing down normal development. To enable debugging, set `XDEBUG_MODE=debug` in `.env`, then rebuild and recreate the service:

`docker compose up -d --build`

The Xdebug client is configured for VS Code on port 9003. Compose also maps `host.docker.internal` to the host gateway for Linux.

When `XDEBUG_MODE=debug`, use the PHP Debug VS Code extension to listen on port 9003 and trigger a session with `?XDEBUG_TRIGGER=1` (or a browser helper). The **launch.json** file contains the path mappings for remote debugging.

```
"pathMappings": {
"/var/www/html": "${workspaceRoot}/wp-core",
                "/var/www/html/wp-content/plugins": "${workspaceRoot}/plugins",
                "/var/www/html/wp-content/themes": "${workspaceRoot}/themes"
}
```

### Set WordPress Coding Standards

WordPress Coding Standards 3.x, PHP CodeSniffer, and the Composer installer plugin are managed in `composer.json`. Install them with:

`composer install`

The Composer installer registers WPCS automatically; `phpcs.xml.dist` selects it and scopes checks to `plugins` and `themes`. Check a file with `./vendor/bin/phpcs path/to/file.php` or fix it with `./vendor/bin/phpcbf path/to/file.php`. Without a path, PHPCS scans the configured folders and PHPCBF applies fixes to them.

### Using WPCS in VS Code

Install a PHP CodeSniffer extension in VS Code and use the project's `phpcs.xml.dist`; the Composer plugin discovers WPCS automatically.

# 🤝 Contributing and Support

This project is **a work in progress.** Feel free to contribute by reporting [issues](https://github.com/sarahcssiqueira/docker-wordpress/issues) or submitting [pull requests](https://github.com/sarahcssiqueira/docker-wordpress/pulls) with improvements.

❤️ Support [buying me a coffee](https://www.buymeacoffee.com/sarahcssiqueira).
