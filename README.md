# WordPress Self-Hosted with Docker

![wordpress-self-hosted](https://repository-images.githubusercontent.com/1070471675/fa9106df-8efd-4e28-82c3-a363e5164e0d)

This repository provides a `docker compose` setup to run a self-hosted [WordPress](https://wordpress.org/) instance, complete with a [MySQL](https://www.mysql.com/) database, [phpMyAdmin](https://www.phpmyadmin.net/), and [WP-CLI](https://wp-cli.org/).

It is pre-configured to join a shared Docker network, allowing easy integration with other services like [n8n](https://github.com/AiratTop/n8n-self-hosted).

## Features

-   Uses official Docker images for **WordPress**, **MySQL**, **phpMyAdmin**, and **WP-CLI**.
-   Includes a full-featured environment for development and management.
-   Persists WordPress files and MySQL data in local volumes (`./data/wp` and `./data/wp-db`).
-   Pre-configured for a shared network for easy inter-service communication.
-   Includes helper scripts for easy management (`restart-docker.sh`, `update-docker.sh`).
-   Includes a `backup.sh` script for creating compressed database backups.
-   Includes a sample `Caddyfile` for use with a reverse proxy.

## Getting Started

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/AiratTop/wordpress-self-hosted.git
    cd wordpress-self-hosted
    ```

2.  **Create the shared network:**
    If it doesn't exist yet, create the shared Docker network:
    ```bash
    docker network create shared_network
    ```

3.  **Configure environment variables:**
    Create a `.env` file and specify your database credentials.

4.  **Start the services:**
    ```bash
    docker compose up -d
    ```

## Accessing Services

-   **WordPress:** [http://localhost:8888](http://localhost:8888)
-   **phpMyAdmin:** [http://localhost:8081](http://localhost:8081)

## Usage

-   **Start:** `docker compose up -d`
-   **Stop:** `docker compose down`
-   **Restart:** `./restart-docker.sh`
-   **Update:** `./update-docker.sh` (Pulls the latest Docker images and restarts)
-   **Backup:** `./backup.sh` (Creates a compressed backup in the `backups` directory)
-   **WP-CLI:** Use `docker compose exec wp-cli wp <command>`. For example:
    ```bash
    # List installed plugins
    docker compose exec wp-cli wp plugin list
    ```

## Connecting with n8n

This setup is designed to work with the [n8n-self-hosted](https://github.com/AiratTop/n8n-self-hosted) configuration. Since both services are on the `shared_network`, you can connect to MySQL from n8n using the following credentials:

-   **Host:** `wp-db`
-   **Port:** `3306`
-   **Database, User, Password:** (As specified in your `.env` file)

## See Also

Check out other self-hosted solutions:

-   [**postgresql-self-hosted**](https://github.com/AiratTop/postgresql-self-hosted): A simple and robust PostgreSQL setup.
-   [**mysql-self-hosted**](https://github.com/AiratTop/mysql-self-hosted): A self-hosted MySQL instance.
-   [**clickhouse-self-hosted**](https://github.com/AiratTop/clickhouse-self-hosted): High-performance columnar database for analytics.
-   [**metabase-self-hosted**](https://github.com/AiratTop/metabase-self-hosted): Self-hosted Metabase on Docker for business intelligence and analytics.
-   [**qdrant-self-hosted**](https://github.com/AiratTop/qdrant-self-hosted): A vector database for AI applications.
-   [**redis-self-hosted**](https://github.com/AiratTop/redis-self-hosted): A fast in-memory data store, often used as a cache or message broker.
-   [**caddy-self-hosted**](https://github.com/AiratTop/caddy-self-hosted): A modern, easy-to-use web server with automatic HTTPS.
-   [**wordpress-self-hosted**](https://github.com/AiratTop/wordpress-self-hosted): Production-ready WordPress stack with MySQL, phpMyAdmin, and WP-CLI.
-   [**n8n-self-hosted**](https://github.com/AiratTop/n8n-self-hosted): Scalable n8n with workers, Caddy for auto-HTTPS, and backup scripts.
-   [**monitoring-self-hosted**](https://github.com/AiratTop/monitoring-self-hosted): Self-hosted monitoring stack with Prometheus and Grafana.
-   [**ollama-self-hosted**](https://github.com/AiratTop/ollama-self-hosted): Ready-to-use solution for running Ollama with the Open WebUI on Docker.
-   [**authentik-self-hosted**](https://github.com/AiratTop/authentik-self-hosted): Authentik is a flexible, open-source Identity & Access Management (IAM) solution.
-   [**gatus-self-hosted**](https://github.com/AiratTop/gatus-self-hosted): Automated service health dashboard with a PostgreSQL backend and backup scripts.
-   [**beszel-self-hosted**](https://github.com/AiratTop/beszel-self-hosted): Ready-to-run Beszel hub + agent stack for monitoring your infrastructure.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Author

**AiratTop**

- Website: [airat.top](https://airat.top)
- GitHub: [@AiratTop](https://github.com/AiratTop)
- Email: [mail@airat.top](mailto:mail@airat.top)
- Repository: [wordpress-self-hosted](https://github.com/AiratTop/wordpress-self-hosted)