FROM debian
RUN apt-get update && apt-get install -y \
    steghide  \
    && rm -rf /var/lib/apt/lists/*
WORKDIR '/data'
