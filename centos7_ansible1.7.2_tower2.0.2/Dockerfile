# Build from latest version of centos7
FROM centos:centos7
MAINTAINER Kyle Harrison <kylejharrison@gmail.com>
# Add ansible dependencies
RUN yum clean all && \
    yum -y install epel-release && \
    yum -y install PyYAML python-jinja2 python-httplib2 python-keyczar python-paramiko python-setuptools git python-pip

# Install ansible
RUN mkdir /etc/ansible/
RUN echo '[local]\nlocalhost\n' > /etc/ansible/hosts
RUN pip install ansible==1.7.2

# Install ansible-tower
ENV ANSIBLE_TOWER_SETUP_DIR /etc/ansible/ansible-tower-setup/
RUN mkdir -p $ANSIBLE_TOWER_SETUP_DIR
ADD sources/ansible-tower-setup-2.0.2.gz $ANSIBLE_TOWER_SETUP_DIR
WORKDIR $ANSIBLE_TOWER_SETUP_DIR/ansible-tower-setup-2.0.2/
RUN ./setup.sh