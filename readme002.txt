App with mul containers
docker network create todo-app-network
docker run -d \
--name mysql-container \
--network todo-app-network \
--network-alias todo-app-network-alias \
-v todo-mysql-database:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=Abc@123456789 \
-e MYSQL_DATABASE=todoDB \
-d mysql

docker exec -it mysql-container mysql -u root -p

Create another container, has the same network
docker run -it \
--network todo-appp-network \
--name netshoot-container \
nicolaka/netshoot