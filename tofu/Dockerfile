# File: Dockerfile-tofu

# Stage 1: Extract the OpenTofu binary from the official minimal image
FROM ghcr.io/opentofu/opentofu:minimal AS tofu

# Stage 2: Build the final, lightweight builder image
FROM alpine:3.20

# Copy the OpenTofu binary from the first stage
COPY --from=tofu /usr/local/bin/tofu /usr/local/bin/tofu

# Install only essential tools
# bash: For more robust scripting capabilities
RUN apk add --no-cache bash

# Tell the container that 'tofu' is the command to run
ENTRYPOINT ["/usr/local/bin/tofu"]

# Set the default working directory
WORKDIR /workspace