FROM node:24

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y  \
      pip  \
      jq && \
    pip install --no-cache-dir --break-system-packages sarif-tools

# Download and set up CodeQL CLI
RUN mkdir /opt/codeql && \
    cd /opt/codeql && \
    curl -sL -o codeql-bundle.tar.gz \
        https://github.com/github/codeql-action/releases/latest/download/codeql-bundle-linux64.tar.gz && \
    tar -xzf codeql-bundle.tar.gz -C . --strip-components=1 && \
    rm codeql-bundle.tar.gz

COPY sarif_alert_counts /usr/local/bin/sarif_alert_counts

ENV PATH="/opt/codeql:$PATH"

ARG KTVERSION_FILE="/sbin/ktversion"

RUN echo "#!/usr/bin/env bash" > ${KTVERSION_FILE} && \
    echo -n "echo " >> ${KTVERSION_FILE} && \
    echo -n "codeql-$(codeql version --format=terse)" >> ${KTVERSION_FILE} && \
    echo -n "-node-$(node -v | sed 's/^v//')" >> ${KTVERSION_FILE} && \
    echo -n "-sarif-tools-$(sarif --version | awk '{print $3}' | sed 's/^v//')" >> ${KTVERSION_FILE} && \
    chmod +x ${KTVERSION_FILE}
