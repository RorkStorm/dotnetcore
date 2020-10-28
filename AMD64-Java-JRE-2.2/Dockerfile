# Use the official image as a parent image.
FROM ubuntu:bionic

# Set the working directory.
# WORKDIR /usr/src/app

# Copy the file from your host to your current location.
# COPY package.json .

# Run the command inside your image filesystem.
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get -y install dialog apt-utils wget

RUN wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb

RUN apt-get update
RUN apt-get install -y apt-transport-https 
RUN apt-get install -y dotnet-sdk-2.2

RUN dotnet tool install --global dotnet-sonarscanner
ENV PATH="$PATH:/root/.dotnet/tools"
RUN apt-get -y install nano htop net-tools mlocate
RUN apt-get -y install default-jre

# Inform Docker that the container is listening on the specified port at runtime.
EXPOSE 5000

# Run the specified command within the container.
# CMD [ "export PATH="$PATH:/root/.dotnet/tools"", "start" ]

# Copy the rest of your app's source code from your host to your image filesystem.
# COPY . .