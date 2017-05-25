- https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac
- https://onbing.com/first-blog/

docker logs -f baomi_web_site_1
docker run --name baomi_web_site_1 -d -p 80:8000 baomi_web_site
docker build -t baomi_web_site .
docker rm -f baomi_web_site_1
docker rmi baomi_web_site
docker restart baomi_web_site_1
docker images
docker exec -it baomi_web_site_1 bash
docker ps
