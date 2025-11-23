ARG BUILD_FROM
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Setup base
RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        chromium \
        procps \
    && curl -fsSL https://getchannels.com/dvr/setup.sh -o /tmp/setup.sh \
    && chmod +x /tmp/setup.sh \
    && cd /usr/local \
    && DOWNLOAD_ONLY=1 bash /tmp/setup.sh \
    && apt-get clean \
    && rm -fr \
        /tmp/* \
        /var/lib/apt/lists/*

# Create run script dynamically to ensure LF line endings and permissions
RUN mkdir -p /etc/services.d/channels-dvr && \
    printf "#!/command/with-contenv bashio\n\
\n\
bashio::log.info \"Starting Channels DVR Server...\"\n\
\n\
# Set data directory\n\
export CHANNELS_DVR_DATA=\"/share/channels-dvr\"\n\
mkdir -p \"\${CHANNELS_DVR_DATA}\"\n\
\n\
bashio::log.info \"Data directory: \${CHANNELS_DVR_DATA}\"\n\
\n\
# Start Channels DVR Server\n\
cd /usr/local/channels-dvr/latest\n\
exec ./channels-dvr\n\
" > /etc/services.d/channels-dvr/run && \
    chmod a+x /etc/services.d/channels-dvr/run


