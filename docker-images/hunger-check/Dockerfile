FROM python:3.7-slim
LABEL MAINTAINER="UTD" INFO="Kubernetes"

RUN apt update && apt install stress-ng curl wget -y \
    && cd /tmp; wget https://github.com/yudai/gotty/releases/download/v1.0.1/gotty_linux_amd64.tar.gz \
    && tar -xvzf gotty_linux_amd64.tar.gz; mv gotty /usr/local/bin/gotty

EXPOSE 8080

CMD [ "gotty", "-w", "bash" ]
