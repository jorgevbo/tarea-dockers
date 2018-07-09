FROM jorgevbo/tarea-apache2

RUN apt-get install -y php \
    libapache2-mod-php \
    php-gd

RUN echo "<?php phpinfo(); ?>" > /var/www/html/info.php

RUN apt-get install -y git
RUN cd /var/www/html/ && git clone https://github.com/getgrav/grav.git grav && cd grav
RUN bin/grav install
RUN bin/gpm install admin -y

# CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]
