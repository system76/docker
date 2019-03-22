FROM ubuntu:latest
Maintainer system76

RUN apt update -qq && apt install -qqy \
  apt-transport-https \
  ca-certificates \
  curl \
  lxc \
  iptables \
  wget

RUN curl -sSL https://get.docker.com/ | sh && \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y docker-ce && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

RUN curl -s -L https://github.com/docker/compose/releases/latest | \
  egrep -o '/docker/compose/releases/download/[0-9.]*/docker-compose-Linux-x86_64' | \
  wget --base=http://github.com/ -i - -O /usr/local/bin/docker-compose && \
  chmod +x /usr/local/bin/docker-compose && \
  /usr/local/bin/docker-compose --version

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

VOLUME /var/lib/docker

ENV LOG=file

ENTRYPOINT ["wrapdocker"]
CMD []
