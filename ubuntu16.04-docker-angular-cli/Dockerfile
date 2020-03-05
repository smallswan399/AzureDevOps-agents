FROM crazyzebra684/ubuntu16.04-docker-nodejs:56

COPY scripts /scripts

RUN /scripts/installers/docker-moby.sh && \
    /scripts/installers/docker-compose.sh && \
    /scripts/installers/kubernetes-tools.sh

