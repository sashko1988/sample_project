FROM python:3.11.6-slim-bookworm

RUN apt-get update && apt-get upgrade -y \
    && apt-get install --no-install-recommends -y \
        build-essential \
        unixodbc-dev \
        libpq-dev \
        git \
    # Clean cache and delete index files
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Setup timezone
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone

# Upgrade pip for faster installs and disable version check
RUN python3 -m pip install --upgrade pip && \
    python3 -m pip config set global.disable-pip-version-check true

ENTRYPOINT ["/bin/bash"]