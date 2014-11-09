# Build from latest version of ubuntu14.04
FROM ubuntu:14.04
MAINTAINER Kyle Harrison <kylejharrison@gmail.com>

# Install ansible
RUN apt-get update && \
    apt-get install --no-install-recommends -y software-properties-common && \
    apt-add-repository ppa:ansible/ansible && \
    apt-get update && \
    apt-get install -y ansible=1.7.2-1ppa~trusty

RUN echo '[local]\nlocalhost\n' > /etc/ansible/hosts

# Install ansible-tower
ENV ANSIBLE_TOWER_SETUP_DIR /etc/ansible/ansible-tower-setup/
RUN mkdir -p $ANSIBLE_TOWER_SETUP_DIR
ADD sources/ansible-tower-setup-2.0.2 $ANSIBLE_TOWER_SETUP_DIR
WORKDIR $ANSIBLE_TOWER_SETUP_DIR/ansible-tower-setup-2.0.2/
RUN ./setup.sh