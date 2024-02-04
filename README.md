# Devcontainer For ConcreteCms

## Motivation

I honestly do not like composer and everything php 😅, so to avoid having any php on my machine I decided to create a devcontainer that automatically installs all of its dependencies like composer, nginx etc for concretecms and sets it up. To even have a better and faster expirience I even left in the build script that clones, setups concretecms, creates a linux user etc. This script should only run once inside the container so to prevent a second build I have created a lockfile mechanisme. Simpely delete the `.devcontainer/prevent-install-concretecms.lock` and the buildscript will be executed when entering the devcontainer.

## WSL

I really recommend using WSL for this application otherwise concretecms will be really slow. I have tested it on WSL2 and it works like a charm.

## How to use

1. Clone this repository
1. Open the repository in VSCode
1. Navigate to the `.devcontainer` folder and delete the file `prevent-install-concretecms.lock` (if you want to install concretecms and setup the devcontainer)
1. Open the command palette and run `Devcontainer: Build container without cache`
1. Wait for the container to build and install concretecms
1. Run `ccm-service start` to start: MariaDB, Nginx, PHP-FPM, mail server.
1. Open your browser and navigate to `http://localhost` and you should see the concretecms homepage.


## Notes

### NGINX

Nginx is instructed to serve /app/cms. So install concretecms in the /app/cms folder. The reason for this is so that we can have other applications like bedrock theme in the /app folder and not having it inside live in concretecms.

If you want to change this folder name, locate to the nginx config at `.devcontainer/assets/nginx.conf`.

### ccm-service

You can use the `ccm-service` command to start, stop and restart the services. The services are: MariaDB, Nginx, PHP-FPM, mail server.

For more information run `ccm-help`.

### Credentials

```
Concrete user name: admin
Concrete user password: 12345
Name of the Concrete database: c5
Database user name: c5
Database user password: 12345
Port for the website: 80
Port for the database: 3306
Port for the webmail: 8025
```

## Credits

The docker image was originally created by [The Concrete5-community](https://github.com/concrete5-community/docker5). But I have made some changes to it to make it work. I would highly recommend checking out their repository to know more about this devcontainer.