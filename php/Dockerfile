FROM jorgevbo/tarea-apache2

RUN apt-get install -y php \
    libapache2-mod-php

RUN echo "<?php phpinfo(); ?>" > /var/www/html/info.php

RUN apt-get install -y git

# Instalando dependencias para Grav
RUN apt-get install -y php-gd \
    php-mbstring \
    php-curl \
    php-zip \
    php-xml

RUN cd /var/www/html/ && \
    git clone https://github.com/getgrav/grav.git grav && \
    cd grav && \
    bin/grav install && \
    bin/gpm install admin -y

RUN chown -R www-data:www-data /var/www/html

ADD grav-site.conf /etc/apache2/sites-available/grav-site.conf
RUN a2dissite 000-default && \
    a2ensite grav-site

# RUN service apache2 reload

# CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]
