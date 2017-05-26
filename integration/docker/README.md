- https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac
- https://onbing.com/first-blog/

docker logs -f web_site_1
docker run --name web_site_1 -d -p 80:8000 web_site
docker build -t web_site .
docker rm -f web_site_1
docker rmi web_site
docker restart web_site_1
docker images
docker exec -it web_site_1 bash
docker ps
