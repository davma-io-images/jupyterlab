# Jupyter-Ultimate

</br>

[![Build jupyter-ultimate](https://github.com/davma-io-images/jupyterlab/actions/workflows/jupyter-ultimate.yml/badge.svg)](https://github.com/davma-io-images/jupyterlab/actions/workflows/jupyter-ultimate.yml)
[![Docker Pulls](https://img.shields.io/docker/pulls/davma/jupyter-ultimate?logo=docker&logoColor=white)](https://hub.docker.com/r/davma/jupyter-ultimate)

## 1. Features

This image is a modification of the official [Jupyter Notebook Deep Learning Stack](https://hub.docker.com/r/jupyter/tensorflow-notebook) image. 

The following components have been added:

| CLI Components | Infrastructure Components | Python Components |
|---| ---| ---|
| Azure CLI | Terraform | Vault API client |
| AWS CLI | Ansible | Pyodbc |
| Napptive CLI | kubectl |  |

## 2. Requirements

1. [Docker](https://docs.docker.com/get-docker/)

## 3. Docker pull

You can download image from [Docker Hub](https://hub.docker.com/r/davma/jupyter-ultimate) with the following command.

````
docker pull davma/jupyter-ultimate:latest
````

## 4. Supported tags

Tags have been assigned based on the version of python installed.

- latest, 3.10 
- 3.9 
- 3.8

Can find the dockerfile in the following [link](https://github.com/davma-io-images/jupyterlab/blob/main/jupyter-ultimate/Dockerfile)

## 5. Deploy with Docker Compose

Use docker compose for persistent data in your local directory. You will have access from Jupyter to the directory from which you deploy this docker compose.

````
services:
  jupyter-ultimate:
    container_name: jupyter-ultimate
    image: davma/jupyter-ultimate:latest
    pull_policy: always
    volumes:
      - "./:/home/jovyan/projects"
    ports:
     - "8888:8888"
    restart: always
````

## 6. Access to Jupyter-Ultimate

Visiting ``http://<hostname>:8888/?token=<token>`` in a browser loads JupyterLab, where:

- Hostname is the name of the computer running Docker.
- Token is the secret token printed in the console.

## 7. Image build

You can run the image build with the following commands

````
git clone https://github.com/davma-io-images/jupyterlab.git
cd jupyterlab/jupyter-ultimate/
docker build -t jupyter-ultimate .
````

## 8.Documentation and guides

[Jupyter Notebook](https://jupyter.org/)

[Jupiter Ansible](https://github.com/ansible/ansible-jupyter-kernel)

[Ansible](https://docs.ansible.com/)

[Terraform](https://www.terraform.io/intro)

[TensorFlow](https://www.tensorflow.org/)

[Docker TensorFlow](https://www.tensorflow.org/install/docker)

[Microsoft ODBC 17](https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017)



