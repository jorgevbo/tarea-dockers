FROM ubuntu:16.04

# Actualización de cache
RUN apt-get update -y

# Instalación de Apache
RUN apt-get install -y apache2

# Habilitar mod_rewrite por defecto
RUN a2enmod rewrite

# RUN chown -R www-data:www-data /var/www

# ENV APACHE_RUN_USER  www-data
# ENV APACHE_RUN_GROUP www-data

# Configurar las rutas a los archivos y carpetas generados por Apache
ENV APACHE_LOG_DIR   /var/log/apache2
ENV APACHE_PID_FILE  /var/run/apache2/apache2.pid
ENV APACHE_RUN_DIR   /var/run/apache2
ENV APACHE_LOCK_DIR  /var/lock/apache2
ENV APACHE_LOG_DIR   /var/log/apache2

# Creación de las carpetas
RUN mkdir -p $APACHE_RUN_DIR
RUN mkdir -p $APACHE_LOCK_DIR
RUN mkdir -p $APACHE_LOG_DIR

# Exponer el puerto 80 HTTP
EXPOSE 80

# Ejecutar Apache
CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]