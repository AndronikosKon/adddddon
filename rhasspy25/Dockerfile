FROM synesthesiam/rhasspy-server:latest
LABEL maintainer="Michael Hansen <hansen.mike@gmail.com>"
ENV LANG C.UTF-8

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
      git \
      alsa-utils \
      dkms \
      i2c-tools \
      libasound2-plugins \
    && git clone "https://github.com/respeaker/seeed-voicecard" \
    && cd seeed-voicecard \
    && chmod a+x ./install.sh \
    && rm -rf .git \
    && apt-get purge -y --auto-remove git

# Copy script to run
COPY docker/run.sh /run.sh
RUN chmod a+x /run.sh

ENV CONFIG_PATH /data/options.json

ENTRYPOINT ["/run.sh"]
