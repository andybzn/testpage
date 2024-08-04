VERSION 0.8
FROM docker.io/library/nginx:1.27-alpine-slim
WORKDIR /usr/share/nginx/html

ENV tag="0.0.3"

build:
    COPY src/ .
    RUN chown -R nginx:nginx .
    LABEL org.opencontainers.image.source=https://github.com/andybzn/testpage
    LABEL org.opencontainers.image.authors="Andy Baizon <dev@baizon.uk>"
    LABEL org.opencontainers.image.description="Your basic test page"
    SAVE IMAGE testpage:latest testpage:${tag}
