# Task 3: PHP + MySQL + phpMyAdmin with Docker Compose

## Structure
- `Dockerfile`: builds the PHP 8.0 Apache image with the mysqli extension
- `compose.yml`: three services (php-apache-environment, db, phpmyadmin)
- `php/src/index.php`: connects to MySQL, creates the `users` table, shows an insert form
- `php/src/insert.php`: inserts the submitted row and lists the table

## Services
- **db**: image `mysql:8.0`, restart always, port `9906:3306`, environment variables MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER, MYSQL_PASSWORD
- **phpmyadmin**: image `phpmyadmin`, restart always, port `8080:80` (different from the PHP server port 8000), depends on db, `PMA_HOST: db`
- **php-apache-environment**: built from the Dockerfile, port `8000:80`, mounts `./php/src` to `/var/www/html`

## Change made to the skeleton
The skeleton Dockerfile ended with `RUN apt-get update && apt-get upgrade -y`. This failed with 404 errors because the `php:8.0-apache` image is based on Debian 11 (bullseye), which is no longer maintained and whose security package files were removed from the Debian servers. The line is not needed for the application, so it was removed.

## Commands
- `docker compose up -d --build`
- `docker compose ps`
- `docker compose down`

## URLs
- Website: http://localhost:8000
- phpMyAdmin: http://localhost:8080 (user `root`, password `MYSQL_ROOT_PASSWORD`)

## Result
The website connects to MySQL, creates the table and inserts form data. The inserted rows are visible in phpMyAdmin under MYSQL_DATABASE > users.
