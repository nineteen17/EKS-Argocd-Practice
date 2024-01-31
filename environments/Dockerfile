FROM ubuntu:latest
LABEL name="nick-admin"
LABEL email="nik-r07@live.com"
ENV UBUNTU_HOME=/var/www/html/
RUN apt-get update -y
ENV DEBIAN_FRONTEND noninteractive	
RUN apt-get -y install tzdata
RUN apt-get install apache2 -y
WORKDIR UBUNTU_HOME
COPY script/index.html ${UBUNTU_HOME}
EXPOSE 80
CMD ["apachectl" , "-D","FOREGROUND"]