ARG BUILD_FROM
FROM $BUILD_FROM

WORKDIR /usr/src/node-red

USER root

RUN apt-get update && \
    apt-get install -y jq && \
    npm install -g node-red-admin

# Upgrade node to workaround issue with node-red-contrib-home-assistant 0.3.0. Remove workaround once base image (nodered/node-red-docker) has compatible version of node.
RUN npm cache clean -f && \
    npm install -g n && \
    n stable

# Expose tcp/1880
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json

COPY settings.js /
COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]
