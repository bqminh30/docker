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
-d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04