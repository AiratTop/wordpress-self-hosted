# AGENTS.md

## Purpose
Public self-hosted deployment template for WordPress with MySQL, WP-CLI, and phpMyAdmin.

## Repository Role
- Category: `*-self-hosted` (public GitHub repository).
- Related local stack: `../wordpress-docker`.
- Main entrypoint: `docker-compose.yml`.

## Stack Summary
- Services: `wp-db`, `wp`, `wp-cli`, `pma`.
- Exposed ports: `8888` (WordPress), `8081` (phpMyAdmin).
- External network: `shared_network`.

## Data and Config
- MySQL data: `./data/wp-db`.
- WordPress files: `./data/wp`.
- PHP overrides: `./config/php.ini`.

## Operations
- Restart stack: `./restart-docker.sh`.
- Update images and restart: `./update-docker.sh`.
- Backup helper: `./backup.sh`.

## AI Working Notes
- Keep credentials in `.env` (`MYSQL_ROOT_PWD`, `MYSQL_USER`, `MYSQL_PWD`, `MYSQL_DB`).
- Preserve DB healthcheck and `depends_on` gating for `wp`, `wp-cli`, `pma`.
- Treat `./data/wp` as persistent CMS state; avoid destructive syncs.
