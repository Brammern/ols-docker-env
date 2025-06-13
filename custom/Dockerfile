FROM litespeedtech/openlitespeed:1.8.3-lsphp83

# Variables
ENV PHP_VERSION=8.3 \
    PHP_API=20230831 \
    LSPHP_VERSION=lsphp83

# Install required packages
RUN curl -sSL https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
    | tar -xz -C /tmp && \
    cp /tmp/ioncube/ioncube_loader_lin_${PHP_VERSION}.so \
       /usr/local/lsws/${LSPHP_VERSION}/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so && \
    rm -rf /tmp/ioncube*

# IonCube Loader Install
RUN echo "zend_extension=/usr/local/lsws/${LSPHP_VERSION}/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so" \
    >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini && \
    echo "opcache.enable=0" >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini && \
    echo "opcache.enable_cli=0" >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini && \
    echo "max_input_vars=10000" >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini
