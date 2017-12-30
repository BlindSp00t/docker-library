FROM alpine:latest AS build
RUN apk add --no-cache build-base git autoconf automake libjpeg-turbo-dev ffmpeg-dev v4l-utils-dev linux-headers && \
    git clone  https://github.com/Motion-Project/motion.git && \
    cd motion && \
    autoreconf -fiv && \
    ./configure && \
    make && \
    mkdir -p /opt && \
    DESTDIR=/opt make install && \
    cp -rf /opt/usr/local/etc/motion/motion-dist.conf /opt/usr/local/etc/motion/motion.conf

FROM alpine:latest
COPY --from=build /opt /
RUN apk add --no-cache ffmpeg
VOLUME /var/lib/motion
ENTRYPOINT ["/usr/local/bin/motion"]
