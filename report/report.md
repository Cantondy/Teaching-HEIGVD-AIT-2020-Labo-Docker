title

table of content

chapter 0

m1 : No, our solution is static and non-scalable. Which means we have to update it manually each time we want to add new nodes when a server crashes

m2 : First we create a new webapp container in the docker-compose.yml file, then we modify the HAProxy configuration file to add our new node, then we rebuild everything in order to load our changes

m3 : Implement a dynamic configuration for HAProxy so that every time we add a new node, the configuration is updated automatically

m4 : We need a service discovery tool in order to tell us which node is up and then update the HAProxy accordingly

m5 : Right now each container have only one service running, if we want to have multiple services on a container we need to have a process that would run multiple services for us.

m6 : Every time we add a new server node, we will have to modify the HAProxy configuration file, this is not dynamic. In order to make it dynamic we would require to loop through the list of nodes and update the HAProxy configuration file automatically every time we add a new node. A template engine could do that.

Deliverables : 

![](/img/img1.PNG)

Repository URL : https://github.com/Cantondy/Teaching-HEIGVD-AIT-2020-Labo-Docker

chapter 1

![](/img/img2.PNG)

chapter 2

chapter 3

chapter 4

chapter 5

chapter 6

difficulties

conclusion