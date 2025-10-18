# Filebrowser Docker Compose Installation Guide

### Assumptions:
You already have Docker intalled on your Linux server.

- Docker install [guide](https://docs.docker.com/engine/install/).
- Follow the post install [guide](https://docs.docker.com/engine/install/linux-postinstall/) and add your user to the docker group.

### Installation:
In your home directory create an App Data folder for all of your Docker config files. "appdata", "docker" are common folder names you can use.
```
mkdir appdata
cd appdata
mkdir filebrowser
```
Create a new docker compose yml file or update your existing one with the contents of the attached 'docker-compose-filebrowser.yml' file.
Change the volume details to match the home folder name for your system. Run "id $user" to check your user id. Filebrowser uses port 8080, which is a very common port for other docker containers. Change the left hand side of the ports to suit. In my case I'm using port 8081.
```
---
services:
  filebrowser:
    image: filebrowser/filebrowser
    container_name: filebrowser
    environment:
      - PUID=1000 #"id $user" to find your uid & gid values
      - PGID=1000
    volumes:
      - /home/user:/srv #change 'user' to the name of your account
      - /home/user/appdata/filebrowser:/database #this will create the filebrowser.db file
      - /home/user/appdata/filebrowser:/config #this will create the settings.json file
    ports:
      - 8081:80 #default port is 8080, change as needed. Don't change the right hand side port (port 80)
    restart: unless-stopped
```
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

Filebrowser has a really nice dark theme. If that's 'your thing', select "Settings -> Global Settings tab at the top" Under 'Theme' click on the drop down and change it to 'Dark'. Update your changes at the bottom of that page.

Happy File Browsing :)
