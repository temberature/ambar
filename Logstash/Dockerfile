FROM logstash:5.6.3

# Set a timezone
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY config/logstash.yml ./config/logstash.yml
COPY pipeline/ ./pipeline

RUN /usr/share/logstash/bin/logstash-plugin install x-pack

HEALTHCHECK --interval=5s --timeout=30s --retries=50 \
  CMD curl -f http://localhost:5000/ || exit 1