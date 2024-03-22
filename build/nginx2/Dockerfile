FROM nginx:latest

COPY ./ssl.conf /etc/nginx/conf.d/ssl.conf

RUN apt-get update -y \
    && mkdir /etc/nginx/ssl \
    && openssl genrsa -out /etc/nginx/ssl/server.key 2048 \
    # && echo -e "\n\n\n\n\n\n\n" | openssl req -new -key /etc/nginx/ssl/server.key -out /etc/nginx/ssl/server.csr \
    && openssl req -new -key /etc/nginx/ssl/server.key -out /etc/nginx/ssl/server.csr -subj "/C=JP/ST=Tokyo/L=Tokyo/O=Example Company/OU=IT Department/CN=example.co.jp" \
    && openssl x509 -days 3650 -req -signkey /etc/nginx/ssl/server.key -in /etc/nginx/ssl/server.csr -out /etc/nginx/ssl/server.crt

RUN service nginx restart
