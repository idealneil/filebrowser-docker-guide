# Filebrowser Docker Installation Guide

### Assumptions:
You already have Docker and Portainer intalled on your Linux server

- Docker install [guide](https://docs.docker.com/engine/install/)
- Portainer Community Edition install [guide](https://docs.portainer.io/start/install-ce/server/docker/linux)

### Installation:
In your home directory create the App Data folder for your Docker config files
`cd ~
mkdir appdata
cd appdata
mkdir filebrowser`

Create the 'filebrowser.db' file before running the stack in Portainer. Otherwise it will create a folder instead
`cd filebrowser
touch filebrowser.db`

In Portainer create a new Stack. Give the Stack a name and copy the contents of the docker-compose-filebrowser.yml file into the Web Editor. Change the volume details to match home folder for your system. Deploy the stack.

Open a browser to the ip address of your server with port 8081 e.g. 192.168.1.100:8081
Login with username: admin, password: admin
For security change these default login details
