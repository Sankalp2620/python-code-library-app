Basically i have created docker images from the docker files for different services ( login, books, borrow, frontend, Database) by using the **docker stack**

Docker Stack : Combination of **Docker swarm** and **Docker compose**. Docker Stack manages the multiple service in the muliple host in real time
   Docker swarm: Manging the single service on mulitple servers
   Docker compose:- Managing the multiple services in a single host



<img width="933" height="640" alt="image" src="https://github.com/user-attachments/assets/19f4a6ce-0c17-486b-81c2-baf8190ddd36" />


**below are the commands which i used **
To intialize the docker swarm, 
 **docker swarm init** -> after using the comand in the server, the server will become the Manger node, 
Docker will give the command to join the node, the command need to use in the other nodes/hosts/server to join the manager ode
**docker swarm join --token <tockenid@ipaddress>**

docker node ls -> to get the list of nodes manger

To build the images
docker build -t dbimage database
docker build -t authimage auth/ <br />
docker build -t bookimage book/ <br />
docker build -t borrowimage borrow/ <br />
docker build -t appimage . <br /> <br /> <br /> <br />


docker network create mynet <br /> <br /> <br /> <br />


docker run -d --name db -p 3306:3306 --network mynet dbimage <br />
docker run -d --name auth_service --network mynet  -p 5001:5001 authimage <br />
docker run -d --name book_service -p 5002:5002 --network mynet bookimage <br />
docker run -d --name borrow_service  -p 5003:5003 --network mynet borrowimage <br />
docker run -d --name frontend  -p 5000:5000 --network mynet  appimage <br /> 

------------

