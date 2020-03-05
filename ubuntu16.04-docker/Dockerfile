FROM crazyzebra684/ubuntu16.04-base:50

COPY scripts /scripts

RUN /scripts/installers/docker-moby.sh && \
    /scripts/installers/docker-compose.sh && \
    /scripts/installers/kubernetes-tools.sh

