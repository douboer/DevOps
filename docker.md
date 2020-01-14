
# docker

apt-get update

apt-get -y install docker.io  # 安装docker
service docker start

//openvas: tcp6       0      0 172.17.0.2:443          192.168.25.133:59834    ESTABLISHED 47/gsad
//宿主机器: tcp6       0      0 :::443                  :::*                    LISTEN      25097/docker-proxy
docker run -d -p 443:443 --name openvas mikesplain/openvas:9

root@kali:~# docker stop openvas
openvas
root@kali:~# docker start openvas
openvas

docker exec -it openvas bash

docker ps -a

problem:
If you are trying to access GSA via its hostname or a proxy, make sure GSA is set up to allow it.
solve:
vi /etc/init.d/openvas-gsa
DAEMON_ARGS="$DAEMON_ARGS --allow-header-host=$PUBLIC_HOSTNAME"
==>
DAEMON_ARGS="$DAEMON_ARGS --allow-header-host=192.168.65.17"

http://blog.51cto.com/linhong/2134910


//制作放到私有仓库


docker login -u admin -p Harbor12345 harbor.51iwifi.com
docker push harbor.51iwifi.com/test/ubuntu:wr

//从仓库取出
docker pull harbor.51awifi.com/test/jenkins-demo:716a813

docker run --name wr2 -d ubuntu:wr /bin/sh -c "while true; do echo hello world; sleep 2; done"

--insecure-registry 的作用是 www.monicacca.com 使用的是http而非https。加上--insecure-registry 就可以忽略


2018-9-10
============================
yum install docker

[root@localhost ~]# docker search moodle
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

service docker start
//https://hub.docker.com/r/jhardison/moodle/
docker pull docker.io/jhardison/moodle
docker run -d --name DB -p 3306:3306 -e MYSQL_DATABASE=moodle -e MYSQL_ROOT_PASSWORD=moodle -e MYSQL_USER=moodle -e MYSQL_PASSWORD=moodle mysql:5
//docker run -d -P --name moodle --link DB:DB -e MOODLE_URL=http://192.168.188.19 -p 80:80 -p 443:443 jhardison/moodle
docker run -d -P --name moodle --link DB:DB -e MOODLE_URL=https://192.168.188.19 -p 443:443 jhardison/moodle


? docker rm moodle 后修改是否就不保存了

清理所有停止的容器
docker container prune 
清理所有不用数据(停止的容器,不使用的volume,不使用的networks,悬挂的镜像)
docker system prune -a


a, 获取容器ip  
docker inspect $container_name | grep IPAddress
docker inspect moodle | grep IPAddress
b. 添加转发规则 
iptables -t nat -A DOCKER -p tcp --dport $host_port -j DNAT --to-destination $docker_ip:$docker_port  
iptables -t nat -A DOCKER -p tcp --dport 8080  -j DNAT --to-destination  172.17.0.3:8080

a. 获取规则编号  
    iptables -t nat -nL --line-number
b. 根据编号删除规则  
    iptables -t nat -D DOCKER $num

ln -s ../sites-available/edusoho edusoho


2018-10-19
============================
docker harbor 仓库
docker login -u admin -p Harbor12345 https://hub.51iwifi.com

docker tag hub.51iwifi.com/jhardison/moodle:v1 hub.51iwifi.com/chen.io/jhardison/moodle
docker push hub.51iwifi.com/chen.io/jhardison/moodle

docker tag hub.51iwifi.com/mysql:v1 hub.51iwifi.com/chen.io/mysql:v1
docker push hub.51iwifi.com/chen.io/mysql:v1


2018-10-30
============================
yum install docker

/etc/docker/daemon.json
 {  "insecure-registries": ["harbor.51awifi.com","hub.51iwifi.com","harbor.51iwifi.com","192.168.193.1"] }

 docker run -d --name DB -p 3306:3306 -e MYSQL_DATABASE=moodle -e MYSQL_ROOT_PASSWORD=moodle -e MYSQL_USER=moodle -e MYSQL_PASSWORD=moodle hub.51iwifi.com/chen.io/mysql:v1
 docker run -d -P --name moodle --link DB:DB -e MOODLE_URL=https://192.168.188.20 -p 443:443 hub.51iwifi.com/chen.io/jhardison/moodle

