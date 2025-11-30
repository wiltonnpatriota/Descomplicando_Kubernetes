FROM wordpress:php8.2-apache

# Instala unzip para extrair o plugin
RUN apt-get update && apt-get install -y unzip && rm -rf /var/lib/apt/lists/*

# Baixa o plugin SQLite Integration
RUN curl -L -o /tmp/sqlite.zip https://downloads.wordpress.org/plugin/sqlite-integration.1.8.1.zip \
    && unzip /tmp/sqlite.zip -d /var/www/html/wp-content/plugins \
    && rm /tmp/sqlite.zip

# Copia o arquivo db.php necessário ao WordPress
RUN cp /var/www/html/wp-content/plugins/sqlite-integration/db.php /var/www/html/wp-content
