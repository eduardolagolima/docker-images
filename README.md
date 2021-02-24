# php-apache

    docker run -d -p 80:80 --name php-apache -h php-apache -e TZ=America/Sao_Paulo -v $PWD:/var/www/html -w /var/www/html eduardolagolima/php-apache:apache
    docker exec -ti --user=nonroot php-apache /bin/bash
    docker exec -ti php-apache /bin/bash
