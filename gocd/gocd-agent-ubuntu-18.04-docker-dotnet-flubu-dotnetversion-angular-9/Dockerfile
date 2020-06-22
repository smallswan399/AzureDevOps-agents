FROM gocd/gocd-agent-ubuntu-18.04:v20.4.0

USER root

# Install tools
RUN apt-get update
RUN apt-get install wget
RUN apt-get install software-properties-common -y

# Dotnet core sdk
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN add-apt-repository universe
RUN apt-get update
RUN apt-get install apt-transport-https
RUN apt-get update
RUN apt-get install dotnet-sdk-3.1

# Docker CLI
RUN apt-get update
RUN apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
RUN apt-get update
RUN apt-get install docker-ce-cli -y

# Nodejs
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs

# Angular
RUN npm install -g @angular/cli

# Flubu + dotnet-version-cli
RUN dotnet tool install FlubuCore.GlobalTool --tool-path /usr/local/bin
RUN dotnet tool install dotnet-version-cli --tool-path /usr/local/bin

USER go