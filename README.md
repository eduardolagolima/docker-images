postgres
===

    docker run -d --name postgres -h postgres eduardolagolima/postgres:latest

php-apache
===

    docker run -d --link postgres --name php-apache -h php-apache -p 8080:80 -e TZ=America/Sao_Paulo -v $PWD:/var/www/html -w /var/www/html eduardolagolima/php-apache:apache
