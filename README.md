# SpringXD Docker Image
Spring XD docker file for SpringXD image - 1.2.0.RELEASE

###Get started on MacOS
The fastest way on MACOS to get up and running with docker is [Kitematics](https://kitematic.com/download). However there are few more options to play with [latticecf](http://lattice.cf) by [Pivotal](www.pivotal.io) or [RancherOS](http://rancher.com/rancher-os/). Both are good and are one level up from Kitematic. Rancher is particularly impressive. Kitematic and perhaps [Docker Compose](https://www.docker.com/docker-compose) is good enough if you want to work with local multi container apps and don't want to get bogged down with building cloud/microservices sh** just yet. 

###How to get this thing up and running 
*(assuming you have docker installed)*

####Pull the image
To pull the image just type the following on your docker host.
    
    >docker pull mohdaliiqbal/springxdbase

####Spring XD single node container
To run SpringXD in single node run the following command (daemon mode)
    
    >docker run -d mohdaliiqbal/springxdbase xd/bin/xd-singlenode

This should return a container id - keep track of it for connecting later with shell.

You will need to grap IP address of the running container using the following command 

    >docker inspect -f "{{.NetworkSettings.IPAddress}}" $containerid 
    
*container id = the id of the single node container*

####Spring XD Shell container
To run SpringXD shell container run the following command (interactive mode)
    
    docker run -i mohdaliiqbal/springxdbase shell/bin/xd-shell
    
One the shell prompts comes up you can issue the following command to connect the shell with the single node admin container.

    xd:>admin config server http://<single-node-container-ip>:9393

*single-node-container-ip = the ip obtained by docker inspect command*
######Note: 
*This is/was originally managed by Eric Bottard of Pivotal. Since the automatic build on the original docker file was failing so I had to make my own. I recommend that you use his repository but if that did not work, you can always use this repository.*
