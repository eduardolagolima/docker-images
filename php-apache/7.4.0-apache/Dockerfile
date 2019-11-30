FROM php:7.4.0-apache

# Adiciona um usuário sem privilégios de root
RUN useradd -m nonroot --uid=1000

# Atualiza a lista de pacotes
RUN apt-get update

# Instala dependências
RUN apt-get install -y \
    vim \
    git \
    zip \
    libpq-dev

# Instala módulos oficias do PHP sem necessidade de configuração
RUN docker-php-ext-install -j$(nproc) pdo
RUN docker-php-ext-install -j$(nproc) pdo_pgsql

# Habilita o módulo do apache que trata as urls amigáveis
RUN a2enmod rewrite

# Baixa o composer e cria o executável global
RUN php -r "readfile('https://getcomposer.org/installer');" | php; \
    mv composer.phar /usr/local/bin/composer; \
    chmod +x /usr/local/bin/composer

# Limpa a lista de pacotes
RUN rm -r /var/lib/apt/lists/*

# Configura o virtualhost
COPY vhost.conf /etc/apache2/sites-available/000-default.conf

# Seta o php.ini-development como principal 
RUN cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

# Copia as configurações necessárias
COPY config.ini $PHP_INI_DIR/conf.d/