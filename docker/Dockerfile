FROM ubuntu:18.04
ARG START_DIR=/opt/automation

COPY ${GITHUB_WORKSPACE} ${START_DIR}

# Update package lists
RUN apt-get update

# Install essential packages
RUN apt-get install -y software-properties-common python-pip curl nodejs

# Add the Ansible repository
RUN apt-add-repository -y --update ppa:ansible/ansible

# Install Ansible
RUN apt-get install -y ansible

# Install Ansible Azure collection with pip
RUN pip install ansible[azure]

# Install Docker SDK for Python
RUN pip install docker


LABEL "com.azure.dev.pipelines.agent.handler.node.path"="/usr/bin/node"

WORKDIR ${START_DIR}

CMD [ "/bin/bash" ]