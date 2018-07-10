# Se utiliza la imagen de apache generada previamente
FROM jorgevbo/tarea-apache2

# Se instala PHP y el mod_php para Apache
RUN apt-get install -y php \
    libapache2-mod-php

# Instalamos Git para descargar la Aplicación Grav desde su repositorio
RUN apt-get install -y git

# Instalando extensiones PHP necesarias para Grav
RUN apt-get install -y php-gd \
    php-mbstring \
    php-curl \
    php-zip \
    php-xml

# Clonamos el repositorio de la aplicación Grav
RUN cd /var/www/html/ && \
    git clone https://github.com/getgrav/grav.git grav

# Ejecutamos el instalador de las dependencias de Grav y el plugin del Administración
RUN cd /var/www/html/grav && \
    bin/grav install && \
    bin/gpm install admin -y

# RUN chown -R www-data:www-data /var/www/html

# Agregamos un archivo de configuración de Sitio para la aplicación
ADD grav-site.conf /etc/apache2/sites-available/grav-site.conf

# Deshabilitamos el sitio por defecto de Apache y habilitamos el de Grav
RUN a2dissite 000-default && \
    a2ensite grav-site

# CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]
