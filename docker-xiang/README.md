```
docker build -t nginx:v1 .

docker run -d --name php-fpm --network my-net --mount type=bind,source=E:/work/workspace/docker-xiang/docker-xiang/php,target=/usr/local/etc/php-fpm.d --mount type=bind,source=E:/work/workspace/project/php,target=/var/www/test alipeng/php7-fpm-alpine 

docker run -d --name nginx -p 8080:80 --network my-net  --mount type=bind,source=E:/work/workspace/docker-xiang/docker-xiang/nginx/site,target=/etc/nginx/conf.d/site --mount type=bind,source=E:/work/workspace/project/php,target=/var/www/test nginx:v1 


docker run -it  --network my-net alipeng/php7-fpm-alpine  sh


docker run -it --mount type=bind,source=/data/project/hexo,target=/data/project/hexo node

docker run  --name nginx_go -p 8080:80   --add-host host.docker.internal:host-gateway   nginx_go:v1


docker run  --name nginx -p 80:80  --network my-net --add-host host.docker.internal:host-gateway --mount type=bind,source=/data/project/docker-xiang/docker-xiang/nginx/site,target=/etc/nginx/conf.d/site --mount type=bind,source=/data/project,target=/var/www  --mount type=bind,source=/usr/local/log,target=/var/log  nginx:v1 

docker run -d --name php-fpm --network my-net --mount type=bind,source=/data/project/docker-xiang/docker-xiang/php,target=/usr/local/etc/php-fpm.d --mount type=bind,source=/data/project,target=/var/www alipeng/php7-fpm-alpine 


docker run -d --name nginx -p 80:80 --network my-net  --mount type=bind,source=/data/project/docker-xiang/docker-xiang/nginx/site,target=/etc/nginx/conf.d/site --mount type=bind,source=/data/project,target=/var/www  --mount type=bind,source=/usr/local/log,target=/var/log nginx:v1 


docker build -t tally-portal-qa:latest .

docker network create -d bridge my-net


docker run -d  --name tally-portal-qa  --network my-net  --mount type=bind,source=/data/project/tally_portal_qa/nohup.log,target=/app/nohup.log  --mount type=bind,source=/data/project/tally_portal_qa/resource/,target=/app/resource/ tally-portal-qa
docker run -d  --name tally-redis  --network my-net   redis
