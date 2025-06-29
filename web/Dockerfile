FROM ubuntu:22.04

RUN apt update && \
    apt install -y apache2 curl && \
    a2enmod proxy proxy_http rewrite && \
    rm -rf /var/lib/apt/lists/*

CMD ["apachectl", "-D", "FOREGROUND"]
