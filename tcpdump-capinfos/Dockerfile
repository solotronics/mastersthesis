# docker build -t gaddy/tcpdump-capinfos .
# docker run --rm \
#   --name host-tcpdump \
#   --privileged \
#   --network host \
#   -v /tmp:/tmp \
#   gaddy/tcpdump-capinfos \
#   <CAPTURE_DURATION_SEC> \
#   <INTERFACE> \
#   udp

FROM ubuntu:xenial
LABEL maintainer "Sai Man Wong <smwong@kth.se>"

WORKDIR /

COPY us.sources.list /etc/apt/sources.list
COPY docker-entrypoint.sh /

RUN apt-get update && apt-get install -y \
    tcpdump \
    wireshark-common \
    --no-install-recommends && \
    mv /usr/sbin/tcpdump /usr/bin/tcpdump && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["./docker-entrypoint.sh"]
