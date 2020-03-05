FROM crazyzebra684/ubuntu16.04-docker:51

COPY scripts /scripts

ENV AGENT_TOOLSDIRECTORY=/_work/_tool
RUN chmod +x /scripts/installers/nodejs.sh
RUN /scripts/installers/nodejs.sh
