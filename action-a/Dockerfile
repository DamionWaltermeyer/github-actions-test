#Node 14 chosen on debian. 14 is current LTS and debian over alpine since size 
#isn't really an issue for us and compability is better for lib reasons.
FROM node:14

ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes
#install prereqs and clean during same layer
RUN apt update \
  && apt install -y --no-install-recommends \
  apt-transport-https \
  apt-utils \
  ca-certificates \
  curl \
  git \
  gpg \
  iputils-ping \
  jq \
  libcurl4-gnutls-dev \
  libunwind8 \
  netcat \
  && apt autoremove


#label examples
LABEL "com.github.actions.name"="Hello World"
LABEL "com.github.actions.description"="Write arguments to the standard output"
LABEL "com.github.actions.icon"="mic"
LABEL "com.github.actions.color"="purple"



#basic bits to get it started.
ADD entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
