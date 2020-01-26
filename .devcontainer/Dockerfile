FROM node:slim

# update all
RUN apt-get update && apt-get install -y --no-install-recommends

# Copy default endpoint specific user settings overrides into container to specify Python path
COPY .devcontainer/settings.vscode.json /root/.vscode-remote/data/Machine/settings.json

# make work directory
RUN mkdir /workspace
WORKDIR /workspace

# install global npm modules
RUN npm install katacoda-cli --global

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y