FROM php:8.1-fpm

WORKDIR /var/www

# Instalar las dependencias necesarias
RUN apt-get update && apt-get install -y \
    curl \
    zip \
    unzip \
    git \
    libpq-dev \
    libonig-dev

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instalar las extensiones de PHP necesarias
RUN docker-php-ext-install pdo pdo_mysql mbstring

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY . /var/www

#RUN chown -R www-data:www-data /var/www
RUN chmod 755 /var/www

#RUN composer install

#RUN php artisan migrate --seed

CMD ["php-fpm"]

EXPOSE 3000
