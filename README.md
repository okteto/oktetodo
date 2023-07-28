Now I want to migrate this app to running it on K8s. The first thing I do is delete the `docker-compose.yaml` even though I could still keep it there. 

Build images for the right platform: `docker build -t rinkiyakedad/oktetodo-client --platform=linux/amd64 .`