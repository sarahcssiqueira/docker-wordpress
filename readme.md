# Docker WordPress Environment

This is a basic **Docker WordPress Environment** focused on the development of **plugins and themes**, supports [WP-CLI](https://wp-cli.org/) and [phpMyAdmin](https://www.phpmyadmin.net/).


Clone this repository or download it through PHP Composer. To add through composer, add this repository to your folder composer.json file:

```
"repositories": [
    { "type": "vcs",
        "url": "git@github.com:sarahcssiqueira/docker-wordpress-with-wp-cli.git"
    }
]
```

Then run `composer require docker-env-template/wordpress-with-wp-cli`. This repository will be downloaded inside the vendor folder. 

Run `docker-compose up -d` to start your project.

## Services

- db 

The MYSQL official image

- phpMyAdmin

- WordPress

Uses the official WordPress docker image

- WP-CLI

The **wpcli container** was added in order to only run one-off commands. Don’t need it to run as a service, only as a cli tool, for that run:

`docker-compose run --rm wpcli command`