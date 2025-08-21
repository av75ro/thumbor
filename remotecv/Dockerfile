ARG THUMBOR_TAG=latest
FROM ghcr.io/minimalcompact/thumbor:$THUMBOR_TAG

LABEL maintainer="MinimalCompact"

VOLUME /data

ENV HOME /app
ENV SHELL bash
ENV WORKON_HOME /app
WORKDIR /app

COPY requirements.txt /app/requirements.txt
RUN pip install --trusted-host None --no-cache-dir \
   -r /app/requirements.txt

COPY docker-entrypoint.sh /
# Ensure LF endings and executable bit to avoid exec issues
RUN sed -i 's/\r$//' /docker-entrypoint.sh && chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["remotecv"]
