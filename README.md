# postgres

    docker run -d -p 5432:5432 --name postgres -h postgres postgres
    docker exec -ti postgres /bin/bash

# mongo

    docker run -d -p 27017:27017 --name mongo -h mongo mongo
    docker exec -ti mongo /bin/bash

# php-apache

    docker run -d -p 80:80 --name php-apache -h php-apache -e TZ=America/Sao_Paulo -v $PWD:/var/www/html -w /var/www/html eduardolagolima/php-apache:apache
    docker exec -ti --user=nonroot php-apache /bin/bash
    docker exec -ti php-apache /bin/bash
