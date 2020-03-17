# Env_containers
Containers for l2tp, pppoe and dhcp servers

# Setup
You must install static ip 10.80.1.7 on the selected interface.<br>
pppoe_server/Dockerfile: you must replace “ap_wan” with your interface name

# How build and run
Each folder has a Dockerfile that describes how to create and run each of the services.

# How to set static ip
    ~# ip a flush ap_wan
    ~# ip a add 10.80.1.7/24 brd 10.80.1.255 dev ap_wan

# How to manage docker
## Show list of installed images
    ~# docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    my/dhcp_server      latest              6c52d258d373        36 minutes ago      105MB
    my/pppoe_server     latest              ac7737c84298        About an hour ago   119MB
    my/l2tp_server      latest              70d2b6439e21        About an hour ago   98.6MB
## Show list of started/stopped images
    ~# docker ps -a
    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
    f032a39161b6        my/dhcp_server      "/entrypoint.sh"         36 minutes ago      Up 36 minutes                           dhcp_server
    31e34f17f00b        my/pppoe_server     "/bin/sh -c 'pppoe-s…"   About an hour ago   Up About an hour                        pppoe_server
## Stop running image
    ~# docker rm -f pppoe_server (name from docker ps -a)
## Remove installed image
    ~# docker image rm my/pppoe_server (name from docker images)
