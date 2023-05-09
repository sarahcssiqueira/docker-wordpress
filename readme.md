# Docker WordPress Environment

This is a basic **Docker Wordpress Environment** focused on development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/) and [phpMyAdmin](https://www.phpmyadmin.net/).

Clone this repository, then run `docker-compose up -d`

## Services

- db 
The mysql

- phpmyadmin

- wordpress
Uses the official WordPress docker image

- wpcli
The **wpcli container** was added in order to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`