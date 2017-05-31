# voaty-mcboat-space

So This is it, the famed container.

It's currently in a bit of a .... fluid state.

I will need some assistance in cleaning up where files are, how the service starts etc, please clone this, work out where things are supposed to be, and let me know!

application < All live code should go here 
The application uses gunicorn and is listening on decentcontainer_application_1:5000

nginx < all webserver / proxy / load balancing and other fancy stuff goes here

The nginx server is purely there for proxy purposes and is listening on:
decentcontainer_nginx_1:8080 & decentcontainer_nginx_1:5000 

postgres < the database goes here

The DB server is listening on decentcontainer_db_1:5432

voat < any new code from Cights repo, please clone it to here and then copy it to application to make it live 

  (messy I know, but until we have a rolling lifescycle and we are updating the container, it's the only solution I have)
  
  
#Do not rename decent-container unless you want to have a sad day and break all of the containers ;)


The networking is fairly straight forward:

Docker will run it's own internal networking, so it will do this:
docker ps
CONTAINER ID        IMAGE                         COMMAND                  CREATED             STATUS                         PORTS                                     NAMES
0902c910e2f0        decentcontainer_nginx         "nginx -g 'daemon ..."   38 minutes ago      Up 16 minutes                  80/tcp, 443/tcp, 0.0.0.0:8880->8080/tcp   decentcontainer_nginx_1
8ca5a49b7cbc        decentcontainer_application   "/application/bin/..."   38 minutes ago      Restarting (0) 2 minutes ago                                             decentcontainer_application_1
9436be128216        postgres:9.6.1-alpine         "/docker-entrypoin..."   52 minutes ago      Up 17 minutes                  0.0.0.0:5432->5432/tcp                    decentcontainer_db_1

Each name is a hostname that resolves to an internal IP address

https://docs.docker.com/engine/userguide/networking/

This will show you the networks docker has created:

docker network ls

If you want to "login" into a running container 

docker attach {insert container name here}

or 

docker exec -it  {insert ner ID here} {input shell or a single UNIX command here}

nginx container only has sh
postgres has full bash
and 
gunicorn is currently toasted until we can get the python stuff running smooth.
