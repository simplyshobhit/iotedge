ARG base_tag=3.1.7-bionic-arm32v7
FROM mcr.microsoft.com/dotnet/core/aspnet:${base_tag}

RUN apt-get update && apt-get install -y libcap2-bin libsnappy1v5 && \
    ln -s /lib/arm-linux-gnueabihf/libdl.so.2 /usr/lib/arm-linux-gnueabihf/libdl.so && \
    ln -s /lib/arm-linux-gnueabihf/libc.so.6 /usr/lib/arm-linux-gnueabihf/libc.so && \
    rm -rf /var/lib/apt/lists/*

COPY librocksdb.so /usr/lib/

RUN apt-get update && apt-get install -y --no-install-recommends iproute2 net-tools

# Add an unprivileged user account for running the module
RUN useradd -ms /bin/bash moduleuser
USER moduleuser
