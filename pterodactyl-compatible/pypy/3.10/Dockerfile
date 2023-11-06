FROM pypy:3.10-7.3.13-slim

LABEL       author="Discord: loki_101" maintainer="loki@crazycoder.dev"

RUN adduser --disabled-password --gecos '' --home /home/container container
RUN apt-get update \
    && apt-get install -y --no-install-recommends tini build-essential libpq-dev git curl \
    && rm -rf /var/lib/apt/lists/*

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
