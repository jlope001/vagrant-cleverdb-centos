FROM centos:centos6

MAINTAINER Jose Lopez "jlope001@gmail.com"

# Enable EPEL Repository
RUN su -c 'rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm'
RUN yum -y update

# install dependencies
RUN yum -y update
RUN yum install -y wget mysql rsyslog which openssh-clients

# install agent
ADD ./assets/yum.repo.conf /etc/yum.repos.d/cleverdb-agent.repo
RUN  yum -y install cleverdb-agent

# setup folders
RUN mkdir -p /etc/cleverdb-agent
ADD ./assets/connect.conf /etc/cleverdb-agent/connect.conf
ADD ./assets/ports.conf /etc/cleverdb-agent/ports.conf

ADD ./scripts/startup.sh /opt/startup.sh
CMD ["/bin/bash", "/opt/startup.sh"]
