ARG IMAGE
ARG NB_UID="100"

FROM ${IMAGE} as parent

USER root

#---------------------------------------------------------------------------------------------
# Install ANSIBLE
RUN pip install ansible-kernel
RUN python -m ansible_kernel.install
RUN apt-get update
RUN apt-get install -y sshpass

# HashiCorp Vault API client
RUN pip install hvac

#---------------------------------------------------------------------------------------------
# Install Terraform
RUN apt-get update && sudo apt-get install -y gnupg software-properties-common

RUN wget -O- https://apt.releases.hashicorp.com/gpg | \
    gpg --dearmor | \
    tee /usr/share/keyrings/hashicorp-archive-keyring.gpg

RUN gpg --no-default-keyring \
    --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
    --fingerprint

RUN echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
    tee /etc/apt/sources.list.d/hashicorp.list

RUN apt update
RUN apt-get install terraform