VERSION 0.8
FROM docker.io/library/nginx:1.27-alpine-slim
WORKDIR /usr/share/nginx/html

ENV tag="0.0.4"

image:
    USER root
    RUN apk update && apk upgrade
    RUN rm -rf /var/cache/apk/* /tmp/*
    RUN mkdir -p /var/cache/nginx \
        && mkdir -p /var/run/nginx \
        && mkdir -p /var/log/nginx
    RUN chown -R nginx:nginx /var/cache/nginx \
        && chown -R nginx:nginx /var/run/nginx \
        && chown -R nginx:nginx /var/log/nginx
    COPY nginx.conf /etc/nginx/nginx.conf

release:
    FROM +image

    COPY src/ .
    RUN chown -R nginx:nginx /usr/share/nginx/html
    RUN chmod -R 0755 /usr/share/nginx/html

    USER nginx
    EXPOSE 8080
    CMD ["nginx", "-g", "daemon off;"]

    LABEL org.opencontainers.image.source=https://github.com/andybzn/testpage
    LABEL org.opencontainers.image.authors="Andy Baizon <dev@baizon.uk>"
    LABEL org.opencontainers.image.description="Your basic test page"
    SAVE IMAGE andybzn/testpage:latest andybzn/testpage:${tag}
