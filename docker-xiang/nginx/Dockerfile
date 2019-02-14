FROM nginx:latest
COPY ./upstream.conf /etc/nginx/conf.d/
COPY ./nginx.conf /etc/nginx/
RUN adduser -D -H -u 82 -s /bin/sh nginx
WORKDIR /etc/nginx
