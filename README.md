Docker swarm: Manging the single service on mulitple servers



<img width="933" height="640" alt="image" src="https://github.com/user-attachments/assets/19f4a6ce-0c17-486b-81c2-baf8190ddd36" />


Docker compose -> Managing the multiple services in a single host 
Docker stack -> Docker swarm + Docker compose
 Docker Stack => managing the muliple services in multiple host / servers
git clone



**docker swarm init**
Auto generated command for when intitialize the docker swam
**docker swarm join --token <tockenid@ipaddress>**


docker build -t dbimage database/ <br />
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

