VERSION 0.8
FROM docker.io/andybzn/secure-nginx:latest
WORKDIR /usr/share/nginx/html

ENV tag="0.0.5"

release:
    COPY src/ .
    RUN chown -R nginx:nginx /usr/share/nginx/html
    RUN chmod -R 0755 /usr/share/nginx/html

    LABEL org.opencontainers.image.source=https://github.com/andybzn/testpage
    LABEL org.opencontainers.image.authors="Andy Baizon <dev@baizon.uk>"
    LABEL org.opencontainers.image.description="Your basic test page"
    LABEL org.opencontainers.image.version="${tag}"
    SAVE IMAGE andybzn/testpage:latest andybzn/testpage:${tag}
