FROM node:24

ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies: curl, tar, gzip, git, python3-pip, jq, and Node.js
# RUN apt-get update && \
    # apt-get install -y \
        # curl \
        # tar \
        # gzip \
        # git \
        # python3-pip \
        # jq \
        # nodejs \
        # npm 

# Install pipx and sarif-tools
# RUN pip install pipx && \
    # pipx ensurepath && \
    # pipx install sarif-tools

# Download and set up CodeQL CLI
RUN mkdir /opt/codeql && \
    cd /opt/codeql && \
    curl -sL -o codeql-bundle.tar.gz \
        https://github.com/github/codeql-action/releases/latest/download/codeql-bundle-linux64.tar.gz && \
    tar -xzf codeql-bundle.tar.gz -C . --strip-components=1 && \
    rm codeql-bundle.tar.gz

ENV PATH="/opt/codeql:$PATH"

ARG KTVERSION_FILE="/sbin/ktversion"

RUN echo "#!/usr/bin/env bash" > ${KTVERSION_FILE} && \
    echo -n "echo " >> ${KTVERSION_FILE} && \
    echo -n "codeql-$(codeql version --format=terse)" >> ${KTVERSION_FILE} && \
    echo -n "-node-$(node -v | sed 's/^v//')" >> ${KTVERSION_FILE} && \
    chmod +x ${KTVERSION_FILE}
