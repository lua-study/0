docker run -p 5050:80 -e "PGADMIN_DEFAULT_EMAIL=598855214@qq.com" -e "PGADMIN_DEFAULT_PASSWORD=123456" -d dpage/pgadmin4

docker run --name some-postgres -e POSTGRES_PASSWORD=123456 -d postgres


docker exec -i -t 容器ID或名字 /bin/bash


docker run --name pg -d -e POSTGRES_USER=cc -e POSTGRES_PASSWORD=123456 postgres:9.6
sudo docker run --name pg - d -e POSTGRES_USER=rn0z -e POSTGRES_PASSWORD=1zx2 posgres
sudo docker run --name pgadmin -d -p 5050:5050 fenglc/pgadmin4
sudo docker ps //* check images you can use option -a for all history
then...
sudo docker exec -it  pg bash // for execute -it(stand for interactive terminal)
sudo docker inspect pg // find ipaddress
in root....
psql -U rn0z(your user) -h 172.17.0.2(your ipaddress) -p 5432

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)