# Docker WordPress Environment

Services

- db 
image: mysql:5.7

- phpmyadmin
image: phpmyadmin/phpmyadmin:latest

- wordpress
image: wordpress oficial

- wpcli
image: wordpress:cli

The **wpcli container** was added in order to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`