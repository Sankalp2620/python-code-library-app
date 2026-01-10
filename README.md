Basically i have created docker images from the docker files for different services ( login, books, borrow, frontend, Database) by using the **docker stack**

Docker Stack : Combination of **Docker swarm** and **Docker compose**. Docker Stack manages the multiple service in the muliple host in real time./

   **Docker swarm**: Manging the single service on mulitple servers./
   **Docker compose**:- Managing the multiple services in a single host



<img width="933" height="640" alt="image" src="https://github.com/user-attachments/assets/19f4a6ce-0c17-486b-81c2-baf8190ddd36" />


**below are the commands which i used **
To intialize the docker swarm, /
 **docker swarm init** -> after using the comand in the server, the server will become the Manger node, 
Docker will give the command to join the node, the command need to use in the other nodes/hosts/server to join the manager node /
**docker swarm join --token <tockenid@ipaddress>**

docker node ls -> to get the list of nodes manger

----------
Docker Swarm 
We wont use the local images for docker swam and docker stack.. we will pull the images from the registry

To build the images for docker swarm
docker build -t dbimage database
docker build -t authimage auth/ <br />
docker build -t bookimage book/ <br />
docker build -t borrowimage borrow/ <br />
docker build -t appimage . <br /> <br /> <br /> <br />

To create the network 
docker network create mynetwork name /
docker network create -d overlay app-network /
docker network create -d overlay db-network /
docker network create -d overlay frontend-network /


To run multiple serice for docker swarm /
docker service create --name db_service --replicas=3 --publish 3306:3306 --network all-network sankalp2620/docker:db /
docker service create --name auth_service --replicas=3  --network all-network --publish 5001:5001 sankalp2620/docker:auth /
docker service create --name book_service --replicas=3 --network all-network --publish 5002:5002 sankalp2620/docker:book /
docker service create --name borrow_service --replicas=3 --network all-network --publish 5003:5003 sankalp2620/docker:borrow /
docker service create --name frontend --replicas 3 --publish 5000:5000 --network all-network sankalp2620/docker:frontend /

------------------
Docker stack, 

Till the network the Everything will similar like swarm but here we will use the compose file to up the service /

**docker stack stackname -c compose.yml** /
then all the service will be running. /
In the copose we will mention the networks, ports, services.. /

------------
<img width="1280" height="853" alt="image" src="https://github.com/user-attachments/assets/0e2b0290-db38-4b60-a99f-cad5a8e03f4e" />
----------------------
<img width="1903" height="972" alt="signup page" src="https://github.com/user-attachments/assets/cfce7fa1-60c8-4d22-868f-919d16e40e50" />
**<img width="1903" height="971" alt="books " src="https://github.com/user-attachments/assets/66719ecc-8cf9-499c-bc2c-69b88465c901" />
**




