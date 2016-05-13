FROM elasticsearch:2.3.2
MAINTAINER Observable Networks <engineering@obsrvbl.com>

WORKDIR /usr/share/elasticsearch
RUN bin/plugin install -b cloud-aws
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh
