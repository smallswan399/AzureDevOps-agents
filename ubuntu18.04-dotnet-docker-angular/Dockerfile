FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive \
    METADATA_FILE=/image/metadata.txt \
    HELPER_SCRIPTS=/scripts/helpers

RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes && \
    mkdir /image && \ 
    mkdir agent && \
    touch /image/metadata.txt

COPY scripts /scripts

RUN apt-get update && \
    apt-get install \
    apt-utils \
    lsb-release \ 
    lsb-core \
    software-properties-common \
    apt-transport-https \
    ca-certificates \
    gnupg \
    sqlite \
    sqlite3

RUN /scripts/base/preparemetadata.sh && \
    /scripts/installers/basic.sh && \
    /scripts/base/repos.sh && \
    /scripts/helpers/apt.sh && \
    /scripts/installers/7-zip.sh && \
    /scripts/installers/azcopy.sh && \
    /scripts/installers/gcc.sh && \
    /scripts/installers/clang.sh && \
    /scripts/installers/cmake.sh && \
    /scripts/installers/build-essential.sh && \
    /scripts/installers/azure-cli.sh && \
    /scripts/installers/azure-devops-cli.sh

# Dotnet core sdk
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN sudo dpkg -i packages-microsoft-prod.deb
RUN sudo add-apt-repository universe
RUN sudo apt-get update
RUN sudo apt-get install apt-transport-https
RUN sudo apt-get update
RUN sudo apt-get install dotnet-sdk-3.1

# Docker CLI
RUN sudo apt-get update
RUN sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common -y
RUN sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
RUN sudo apt-key fingerprint 0EBFCD88
RUN sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
RUN sudo apt-get update
RUN sudo apt-get install docker-ce-cli -y

# Nodejs
RUN curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN sudo apt-get install -y nodejs

# Angular
RUN sudo npm install -g @angular/cli

WORKDIR /azp

COPY ./start.sh .

CMD ["./start.sh"]
