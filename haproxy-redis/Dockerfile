FROM haproxy:1.8.2

RUN useradd haproxy \
    && mkdir /var/lib/haproxy

COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg
COPY docker-entrypoint.sh /

ENV REDIS_CLUSTER NULL

EXPOSE 6379
