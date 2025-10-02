FROM php:8.2-apache

# Instala ferramentas e extensões necessárias
RUN apt-get update && apt-get install -y \
    libicu-dev \
    libpq-dev \
    libzip-dev \
    zip \
    unzip \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    && docker-php-ext-install \
        intl \
        pdo \
        pdo_pgsql \
        pdo_mysql \
        zip \
    && docker-php-ext-enable \
        intl \
        pdo_pgsql \
        pdo_mysql

RUN a2enmod rewrite

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# copy config do Apache
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Install Xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Copy Xdebug configuration
COPY xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN mkdir -p /var/log/xdebug-profiler \
    && chmod 755 /var/log/xdebug-profiler

WORKDIR /var/www/html

# Install Lighthouse GraphQL
RUN composer require nuwave/lighthouse mll-lab/laravel-graphql-playground

RUN pecl install redis && docker-php-ext-enable redis