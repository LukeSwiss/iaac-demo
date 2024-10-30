FROM ubuntu:18.04
ARG START_DIR=/opt/automation

COPY ${GITHUB_WORKSPACE} ${START_DIR}

# Update package lists
RUN apt-get update

# Install essential packages
RUN apt-get install -y software-properties-common python3-pip curl nodejs
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

# Add the Ansible repository
RUN apt-add-repository -y --update ppa:ansible/ansible

# Install Ansible
RUN apt-get install -y ansible

# Upgrade pip to the latest version
RUN pip3 install --upgrade pip

# Install Ansible Azure collection with pip
RUN pip3 install ansible[azure]

# Install Docker SDK for Python
RUN pip3 install docker


LABEL "com.azure.dev.pipelines.agent.handler.node.path"="/usr/bin/node"

WORKDIR ${START_DIR}

CMD [ "/bin/bash" ]