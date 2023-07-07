In this stage the application is ready for development using `docker-compose`. A typical flow looks like:
- Run `docker-compose up` to start the application. 
- Make code changes and it will automatically pick them up because we added `volumes` to the `docker-compose.yml` file.

Tricky part was that the application wasn't starting after adding just:
```
volumes:
    - ./server:/app
```
We needed to add an additional volume mapping: `- /app/node_modules` which ensures that the node_modules folder inside the container is replaced with an empty volume. This allows the dependencies to be installed and managed within the container without interference from the host's node_modules folder.