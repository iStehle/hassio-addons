# Taken from https://github.com/Homegear/Homegear-Docker/blob/master/stable/Dockerfile
FROM debian:stretch
MAINTAINER Thomas Hirsch <thi@gurkenbruehe.de>

RUN apt-get update && apt-get -y install apt-transport-https wget ca-certificates apt-utils gnupg
RUN wget https://homegear.eu/packages/Release.key && apt-key add Release.key && rm Release.key
RUN echo 'deb https://apt.homegear.eu/Debian/ stretch/' >> /etc/apt/sources.list.d/homegear.list
RUN apt-get update && apt-get -y install \
  homegear \
#  homegear-beckhoff \
#  homegear-enocean \
  homegear-homematicbidcos \
  homegear-homematicwired \
  homegear-influxdb \
  homegear-insteon \
#  homegear-intertechno \
  homegear-ipcam \
#  homegear-knx \
 # homegear-kodi \
#  homegear-max \
  homegear-nodes-core \
  homegear-nodes-extra \
 # homegear-philipshue \
 # homegear-sonos \
  htop \
  insserv \
  less \
  ntp \
  tzdata \
  vim
RUN rm -f /etc/homegear/dh1024.pem
RUN rm -f /etc/homegear/homegear.crt
RUN rm -f /etc/homegear/homegear.key
RUN cp -R /etc/homegear /etc/homegear.config
RUN cp -R /var/lib/homegear /var/lib/homegear.data

# Inspired by Dockerfile from visevision
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD /start.sh

EXPOSE 2001 2002 2003
