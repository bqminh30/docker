pull images

docker pull mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04

tag == versions
create container from images
1 Image => multiple containers

-d : Detach(background) mode
-e : enviroment variables
--name : container's name
-p : map port
96c2d12d15cd2b3f8569432bdafa0c39e3f05034f7e19d9cc7192c1cb8ef2d46
=> container's id

docker run \
-e "ACCEPT_EULA=Y" \
-e "SA_PASSWORD=Abc@123456789" \
--name sql-server-2019-container \
-p 1435:1433 \
-v /Users/mbq15/Desktop/Docker:/var/opt/mssql \
-d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04 \

Docker container with default volume
docker run \
-e "ACCEPT_EULA=Y" \
-e "SA_PASSWORD=Abc@123456789" \
--name sql-server-2019-container \
-p 1435:1433 \
-v my-volume-1:/var/opt/mssql \
-d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04 \

Volume's path in Host(your PC, laptop)
ls -la ~/Library/Containers/com.docker.docker/Data/vms
docker volume inspect "your volume's name"
 
remove container
docker rm 
-f : force
-v "host' volume":"container's volume"
(container's volume la duong dan  chua db sql server o tren server)
(host volume la duong dan tren pc cua minh)


MacOS:
docker run \
-e MYSQL_ROOT_PASSWORD=Abc@12356789 \
--name mysql8-container \
-p 3308:3306 \
-v mysql8-volume:/var/lib/mysql \
-d mysql

Go inside the container :
-it = interactive mode
docker exec -it mysql8-container bash
Then:
mysql -u root -p

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password
BY '' FLUSH PRIVILEGES;