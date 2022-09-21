# syntax=docker/dockerfile:1.4

# Uncomment this, and comment out below, if using a custom image
# FROM busybox as untarred
# ARG DEEPHAVEN_VERSION=0.15.0
# ARG DEEPHAVEN_HOME=/opt/deephaven
# COPY --link server-jetty-${DEEPHAVEN_VERSION}.tar server-jetty-${DEEPHAVEN_VERSION}.tar
# RUN set -eux; \
#     mkdir -p ${DEEPHAVEN_HOME}; \
#     tar -xf server-jetty-${DEEPHAVEN_VERSION}.tar -C ${DEEPHAVEN_HOME}; \
#     ln -s ${DEEPHAVEN_HOME}/server-jetty-${DEEPHAVEN_VERSION} ${DEEPHAVEN_HOME}/server-jetty

# FROM scratch as server-scratch
# ARG DEEPHAVEN_HOME=/opt/deephaven
# COPY --link --from=untarred ${DEEPHAVEN_HOME} ${DEEPHAVEN_HOME}

FROM ghcr.io/deephaven/server:0.16.1-scratch as server-scratch

FROM eclipse-temurin:17
ARG DEEPHAVEN_HOME=/opt/deephaven
COPY --link --from=server-scratch ${DEEPHAVEN_HOME} ${DEEPHAVEN_HOME}
COPY --link config/ ${DEEPHAVEN_HOME}/config
VOLUME /data
VOLUME /cache
EXPOSE 10000
ENV DEEPHAVEN_HOME=${DEEPHAVEN_HOME}
# Uncomment this to add debugging
# ENV JAVA_OPTS="-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005"
ENTRYPOINT ["/opt/deephaven/server-jetty/bin/start", "/opt/deephaven/config/image-bootstrap.properties"]
