# Use the official image as a parent image.
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-focal-arm64v8

# Set the working directory.
# WORKDIR /usr/src/app

# Copy the file from your host to your current location.
# COPY package.json .

# Run the command inside your image filesystem.
RUN dotnet tool install --global dotnet-sonarscanner
ENV PATH="$PATH:/root/.dotnet/tools"
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get -y install dialog apt-utils
RUN apt-get -y install nano htop net-tools
RUN apt-get -y install default-jre

# Inform Docker that the container is listening on the specified port at runtime.
EXPOSE 5000

# Run the specified command within the container.
# CMD [ "export PATH="$PATH:/root/.dotnet/tools"", "start" ]

# Copy the rest of your app's source code from your host to your image filesystem.
# COPY . .