#################################################################
# Dockerfile to build Zimbra Collaboration 8.8.15 container images
# Based on Ubuntu 18.04 LTS (bionic)
# Created by Jorge de la Cruz
#################################################################
FROM ubuntu:bionic
LABEL org.opencontainers.image.authors="Jorge de la Cruz <jorgedlcruz@gmail.com>"

RUN echo "resolvconf resolvconf/linkify-resolvconf boolean false" | debconf-set-selections

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install \
  wget \
  dialog \
  openssh-client \
  software-properties-common \
  dnsmasq \
  dnsutils \
  net-tools \
  sudo \
  rsyslog \
  unzip

VOLUME ["/opt/zimbra"]

EXPOSE 22 25 465 587 110 143 993 995 80 443 8080 8443 7071

COPY opt /opt/

COPY etc /etc/

RUN wget -O /opt/zimbra-install/zimbra-zcs-8.8.15.tar.gz https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_3869.UBUNTU18_64.20190918004220.tgz

RUN tar xzvf /opt/zimbra-install/zimbra-zcs-8.8.15.tar.gz -C /opt/zimbra-install/

CMD ["/bin/bash", "/opt/start.sh", "-d"]
