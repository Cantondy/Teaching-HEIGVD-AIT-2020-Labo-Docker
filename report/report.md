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

deliverables : 

![](/img/img2.PNG)

In this task we installed "s6" which is a process supervisor that will help us run multiple services on one container. We spent the task updating the dockfile and run scripts of the containers.

chapter 2

Our solution is still not dynamic since it isn't yet possible to manage new nodes, this would require a script whose job would be to add the nodes to the cluster

GOSSIP is a peer-to-peer protocol to send information over all the network's nodes in a broadcast fashion. This is used to maintain HAProxy's catalog of nodes. As a different solution, we could use Consul who also uses GOSSIP and works in a similar way than Serf but posses additional features like service discovery.

chapter 3

chapter 4

By doing only 1 command at each line, we save time in the case of having to re-execute only the last one since an image is created at each command. By doing all the commands in 1 line allows us to not have any temporary images and save some storage space, this is better if we want to simply save up space.

Articles : http://jasonwilder.com/blog/2014/08/19/squashing-docker-images/ and https://betterprogramming.pub/how-to-improve-docker-image-size-with-layers-3ad62be0da9b

By using image inheritance with the FROM keyword in the dockerfile. We could have a basic image with all common things between NodeJS and HAProxy and then 2 small images with the specificity of each.

Instead of adding a new line in the file each time a node joins the cluster, we overwrite it, which poses an issue since every time we add a new node we have to check the file manually in order to get the correct entry.

chapter 5

We can use Consul for service discovery and manage the list of backend nodes. It keeps the list of alive nodes up to date and it is also used for load balancing between the backend nodes

chapter 6

![](/img/img3.PNG)

HAProxy seems to be a rather good solution as long as we don't have the need for too many nodes, since they are manually added in the docker-compose configuration file, we could use "replicas" in order to start many containers that have the same configuration at the same time.

difficulties

The 2 main difficulties for us in this lab were the constant caching of docker that wouldn't take into account some minor changes as well as the fact that some errors we encountered were due to CRLF end of lines instead of LF.

conclusion

This laboratory teached us how to use HAProxy with protocols such as GOSSIP or tools like Serf.