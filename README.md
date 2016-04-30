[![dockeri.co](http://dockeri.co/image/weldpua2008/nginx)](https://hub.docker.com/r/weldpua2008/nginx/)

[![](https://imagelayers.io/badge/weldpua2008/nginx:latest.svg)](https://imagelayers.io/?images=weldpua2008/nginx:latest 'Get your own badge on imagelayers.io')

[![Docker Pulls](https://img.shields.io/docker/pulls/weldpua2008/nginx.svg)](https://hub.docker.com/r/weldpua2008/nginx/)
[![Docker Stars](https://img.shields.io/docker/stars/weldpua2008/nginx.svg)](https://hub.docker.com/r/weldpua2008/nginx/)
[![GitHub issues](https://img.shields.io/github/issues/weldpua2008/nginx.svg)](https://github.com/weldpua2008/docker-nginx/issues) [![GitHub forks](https://img.shields.io/github/forks/weldpua2008/docker-nginx.svg)](https://github.com/weldpua2008/docker-nginx/network) [![GitHub stars](https://img.shields.io/github/stars/weldpua2008/docker-nginx.svg)](https://github.com/weldpua2008/docker-nginx/stargazers) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/weldpua2008/docker-nginx/master/LICENSE) 

Docker-nginx
==================
Docker Image to run Nginx server


Usage
-----

To create the image `weldpua2008/nginx`, execute the following command on the `weldpua2008-docker-nginx` folder:

    docker build -t weldpua2008/nginx .


Running your Nginx docker image
-------------------------------

Start your image building the external ports 80 in all interfaces to your container:

    docker run -d -p 80:80 weldpua2008/nginx

Test your deployment:

    curl http://localhost/

Hello world!

Loading your custom PHP application
-----------------------------------

In order to replace the "Hello World" application that comes bundled with this docker images, first create a new empty folder. Go to the new folder and create two subfolders: `sites-enabled` and `app`. Copy your configuration files to `sites-enabled` and you application files to `app`. Then create a new `Dockerfile` with the following contents:

    FROM weldpua2008/nginx
    ADD sites-enabled/ /etc/nginx/sites-enabled/
    ADD app/ /app/
    RUN chown -R www-data:www-data /app/
    EXPOSE 80

Remember to put your configuration files under the folder named `sites-enabled` and your website files under the folder `app`. Also, if you want to use a different port, change the `EXPOSE 80` in `Dockerfile` as well.(eg. `EXPOSE 443 80` will allow connections go through port `443` and `80`).
After that, build the new `Dockerfile`:

    docker build -t username/my-nginx

And test it:

    docker run -d -P username/my-nginx

Test your deployment:

    curl http://localhost/

That's it!