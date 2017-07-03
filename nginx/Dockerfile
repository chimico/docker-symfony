FROM nginx:alpine

RUN apk update

ADD nginx.conf /etc/nginx/
ADD symfony.conf /etc/nginx/sites-available/

RUN mkdir /etc/nginx/sites-enabled
RUN ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN set -x ; \
    addgroup -g 1000 -S www-data ; \
    adduser -u 1000 -D -D -G www-data www-data && exit 0 ; exit 1

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
