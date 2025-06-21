# Filebrowser Docker Compose Installation Guide

### Assumptions:
You already have Docker intalled on your Linux server.

- Docker install [guide](https://docs.docker.com/engine/install/).
- Follow the post install [guide](https://docs.docker.com/engine/install/linux-postinstall/) and add your user to the docker group.

### Installation:
In your home directory create the App Data folder for your Docker config files
```
mkdir appdata
cd appdata
mkdir filebrowser
```
Create the 'filebrowser.db' file before running your docker compose file, otherwise it will create a folder instead. This will not work.
```
cd filebrowser
touch filebrowser.db
```

Create a new docker compose yml file or copy the contents of the docker-compose-filebrowser.yml file into your exising one.
Change the volume details to match the home folder for your system. Filebrowser uses port 8080, which is a very common port for other docker containers. Change the left hand side of the ports to suit. In my case I'm using port 8081
Update your docker compose file in detatched mode.
```
docker compose up -d
```

Check the logs to see if the container deployed successfully.
```
docker logs filebrowser
```

Note down the admin password in the logs.
e.g. - `Generated random admin password for quick setup: xOGWRHB0t8fq`

Open a browser to the ip address of your server with port the number you set e.g. 192.168.1.100:8081

Login with username: admin & password: generated from the logs e.g. `xOGWRHB0t8fq`.
Once you've successfully logged in change the admin user's name and password to one that you want.

Happy File Browsing on your Linux Server :)
