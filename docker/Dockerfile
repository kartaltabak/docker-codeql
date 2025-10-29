FROM node:24

# Set environment variables for non-interactive installation
ENV DEBIAN_FRONTEND=noninteractive

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
# WORKDIR /opt/codeql
# RUN curl -sL -o codeql-bundle.tar.gz \
#         https://github.com/github/codeql-action/releases/latest/download/codeql-bundle-linux64.tar.gz && \
#     tar -xzf codeql-bundle.tar.gz -C . --strip-components=1 && \
#     rm codeql-bundle.tar.gz

# # Add CodeQL to PATH
# ENV PATH="/opt/codeql:$PATH"

# # Define the command for jq as the entrypoint
# # This will be executed when the container starts without a specific command
# CMD ["jq", "-r", "--compact-output", ".runs[0] | ( .tool.driver.rules | map({ (.id): .defaultConfiguration.level }) | add ) as $ruleLevels | [.results[] | $ruleLevels[.ruleId]] | reduce .[] as $item ({}; .[$item] += 1)", "sarif-results/javascript.sarif"]
