FROM php:8.2-fpm

# Install system dependencies required to build PHP extensions
RUN apt-get update && apt-get install -y \
        libzip-dev \
        zip \
        unzip \
        libonig-dev \
        libxml2-dev \
        git \
        curl \
        && docker-php-ext-install pdo_mysql mbstring bcmath exif pcntl \
        && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions required by Laravel
RUN docker-php-ext-install pdo_mysql mbstring bcmath exif pcntl

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Install Node.js and npm
RUN apt-get update && \
    apt-get install -y nodejs npm && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/laravel-app
